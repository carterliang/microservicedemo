Rabbit MQ sample and Demo
System Design Document
1. Introduction
1.1 Purpose
The purpose of this document is to provide a comprehensive system analysis of the stock trading simulation platform. This includes architecture, data flow, database schema, and code explanation.
1.2 Scope
This document covers the backend services built using Spring Boot, RabbitMQ, WebSocket, and the frontend components using HTML, CSS, and JavaScript.
2. System Architecture
The system consists of a Spring Boot application that integrates with RabbitMQ for message queuing and WebSocket for real-time communication. The architecture includes the following components:
2.1 Components
1. RabbitMQ: Used for message exchange between services.
2. WebSocket: Facilitates real-time data updates to the client.
3. REST API: Provides endpoints for client-server communication.
4. Frontend: Built with HTML, CSS, and JavaScript for user interaction.
3. Data Flow Diagram
The following diagram illustrates the data flow between different components of the system:
[Data Flow Diagram Image]
4. Database Schema
The database schema consists of the following tables with their respective relationships:
4.1 Tables
Field	Type	Description
id	int	Primary Key
order_no	varchar(50)	Order number
symbol	varchar(10)	Stock symbol
price	double	Order price
quantity	int	Order quantity
status	varchar(20)	Order status
The database stores information about orders, stocks, and transactions. Here are some example SQL queries used in the system:
4.2 Example SQL Queries
SELECT * FROM orders WHERE status = 'completed';
DELETE FROM orders WHERE symbol = 'AAPL';
INSERT INTO orders (order_no, symbol, price, quantity, status) VALUES ('O123', 'TSLA', 650.50, 10, 'pending');
5. Code Explanation
5.1 Key Components
1. RabbitmqStreamTwstockStarter9901Application: Main class for starting the Spring Boot application.
2. RabbitMQConfig: Configures RabbitMQ exchanges and queues.
3. WebSocketConfig: Sets up WebSocket endpoints and message broker.
4. OrderController: Handles REST API requests related to orders.
5.2 Integration
The application integrates RabbitMQ and WebSocket as follows:
- RabbitMQ is used for asynchronous communication between services such as order processing and stock updates.
- WebSocket provides real-time updates to clients, enabling live stock price tracking and order status updates.
5.3 REST API Endpoints
The following REST API endpoints are exposed by the application:
- GET /orders: Retrieve all orders.
- POST /order: Submit a new order.
- GET /price/{symbol}: Get the latest price for a given stock symbol.
6. Frontend Architecture
6.1 Overview
The frontend is built using HTML, CSS, and JavaScript, with a focus on real-time updates and user interaction.
6.2 JavaScript Components
1. app.js: Manages WebSocket connections and updates the UI based on incoming messages.
2. stock_chart.js: Utilizes Chart.js to render dynamic stock price charts.
3. index.html: Provides the main layout and elements for user interaction.
6.3 WebSocket Usage
WebSocket is used to receive real-time stock updates and order confirmations. The client subscribes to specific topics and updates the UI accordingly.
![Uploading image.png…]()
