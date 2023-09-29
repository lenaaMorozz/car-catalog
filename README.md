# Car Catalog REST API

This REST API provides a car catalog service where you can manage and retrieve information about cars.

<img src="https://github.com/lenaaMorozz/car-catalog/blob/master/src/main/resources/image/car-catalog.png" width="600">


## Endpoints

### Get All Cars

- HTTP Method: `GET`
- URL: `/cars`
- Description: Retrieves a list of all cars in the directory
- Response: Displays a list of cars with their details

### Add a Car

- HTTP Method: `POST`
- URL: `/add-car`
- Description: Add a new car to the directory
- Parameters:
    - `licensePlate` (String)
    - `color` (String)
    - `brand` (String)
    - `manufacturingYear` (Integer)
- Response: Redirects to the car list page after adding the car.
- Note: If a car already exists in the directory, it will not be added, and an error message will be displayed


### Delete a Car

- HTTP Method: `DELETE`
- URL: `/delete-car/{id}`
- Description: Deletes a car from the directory based on its ID.
- Parameters:
    - `id` (Long): The ID of the car to delete
- Response: Redirects to the car list page after deleting the car

### Get Database Statistics

Retrieves statistics about the database, including the total number of records and the first and last record timestamps.

- HTTP Method: `GET`
- URL: `/cars/statistics`
- Description: Retrieves statistics about the database, including the total number of records and the first and last record timestamps.
- Response: Displays statistics such as the total number of cars in the database, the timestamp of the first car record's creation, and the timestamp of the last car record's creation.

## Technologies Used

- Spring Boot
- ThymeLeaf

## Running the Application with Docker

To run this application using Docker, follow these steps:

### 1. Download Docker Images

Execute the following commands in your console to download the Docker images for the database and the application:

#### For Linux:

```bash
docker pull lenaamorozz/mysql_for_car_catalog:linux
```
```bash
docker pull lenaamorozz/car_catalog:linux
```

#### For MacOS:

```bash
docker pull lenaamorozz/mysql_for_car_catalog:macos
```
```bash
docker pull lenaamorozz/car_catalog:macos
```
### 2.To run Docker containers, you need to create a custom Docker network.

To create a custom Docker network, execute the following command in your console:

```bash
docker network create <network_name>
```
### 3. Start the Database Container
First, start the database container using the following command:
```bash
docker run --net=<network_name> --name db -e MYSQL_ROOT_PASSWORD=pass -d lenaamorozz/mysql_for_car_catalog:<tag>
```
### 4. Start the Application Container
After successfully starting the database container, you can start the application container using the following command:
```bash
docker run --net=<network_name> --name app -d -p 8080:8080 lenaamorozz/car_catalog:<tag>
```
The API will start running at `localhost:8080/cars`.

## Accessing the Application

You can access the application from the following link:

[Link to the Application](http://45.15.159.198:666/cars).









