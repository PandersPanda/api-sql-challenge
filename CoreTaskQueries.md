## Create tables Line, Station, Services

CREATE TABLE Lines (
	line_id SERIAL PRIMARY KEY,
	line_name VARCHAR(255)
)

CREATE TABLE Stations (
	station_id SERIAL PRIMARY KEY,
	station_name VARCHAR(255),
	isOpen BOOLEAN,
	line_id INT,
	FOREIGN KEY (line_id) REFERENCES Lines(line_id)
);

CREATE TABLE Services(
	service_id SERIAL PRIMARY KEY,
	service_name VARCHAR(255)
);

Since stations can have multible services and services can be on multible stations we need a table inbetween

CREATE TABLE station_has_service(
	shs_id SERIAL PRIMARY KEY,
	station_id INT,
	service_id INT,
	FOREIGN KEY (station_id) REFERENCES stations(station_id),
	FOREIGN KEY (service_id) REFERENCES services(service_id)
);

## Insert into tables Line, Station, Services

INSERT INTO stations (station_name, isopen, line_id)
VALUES
('Harrow and Wealdstone', true, 1),
('Kenton', true, 1),
('South Kenton', true, 1),
('North Wembley', true, 1),
('Wembley Central', true, 1),
('Stonebridge Park', true, 1),
('Harlesden', true, 1),
('Willedsen Junction', true, 1),
('Kensel Green', true, 1),
('Queens Park', true, 1),
('Kilburn Park', true, 1),
('Maida Vale', true, 1),
('Warwick Avenue', true, 1),
('Paddington', true, 1),
('Edgeware Road', true, 1),
('Marylebone', true, 1),
('Baker Street', true, 1),
('Regents Park', true, 1),
('Oxford Circus', true, 1),
('Piccadilly Circus', true, 1),
('Charing Cross', true, 1),
('Embankment', true, 1),
('Waterloo', true, 1),
('Lambeth North', true, 1),
('Elephant and Castle', true, 1);

## Set Maida Vale Station as closed

UPDATE stations
SET isopen = false
WHERE station_id = 12;

## Select all open stations

SELECT stations.station_name
FROM stations
WHERE stations.isopen = true;

