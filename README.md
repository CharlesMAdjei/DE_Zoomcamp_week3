# DE_Zoomcamp_week3


-- Create external table
CREATE OR REPLACE EXTERNAL TABLE `gtaxi.green_taxi_data`
OPTIONS (
  format = 'PARQUET',
  uris = ['gs://de_zoomcamp_cadjei/green_taxi/green_taxi_data.parquet']
);

-- Create table
CREATE EXTERNAL TABLE `gtaxi_trips.green_taxi_trips`
OPTIONS (
  format = 'PARQUET',
  uris = ['gs://de_zoomcamp_cadjei/green_taxi/green_taxi_data.parquet']
);


SELECT * FROM `gtaxi.green_taxi_data`;

--Question 1: What is count of records for the 2022 Green Taxi Data??
SELECT COUNT(*) FROM `gtaxi.green_taxi_data`;



--Write a query to count the distinct number of PULocationIDs for the entire dataset on both the tables.
--What is the estimated amount of data that will be read when this query is executed on the External Table and the Table?
SELECT COUNT(DISTINCT p_ulocationid) FROM `gtaxi.green_taxi_data`;
SELECT COUNT(DISTINCT p_ulocationid) FROM `gtaxi_trips.green_taxi_trips`;

--How many records have a fare_amount of 0?
SELECT COUNT(*) FROM `gtaxi.green_taxi_data` WHERE fare_amount = 0;


SELECT DISTINCT p_ulocationid
FROM `gtaxi_trips.green_taxi_trips`
WHERE DATE(lpep_pickup_datetime) BETWEEN '2022-06-01' AND '2022-06-30';


SELECT DISTINCT p_ulocationid
FROM `gtaxi_trips.green_taxi_trips`
WHERE DATE(lpep_pickup_datetime) BETWEEN '2022-06-01' AND '2022-06-30';
