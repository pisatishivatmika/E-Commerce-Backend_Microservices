# E-Commerce Backend Microservices

A robust, scalable e-commerce backend solution built using a microservices architecture.

## Overview

This project implements a complete e-commerce backend using a microservices approach. Each core business domain is encapsulated in its own service, allowing for independent development, deployment, and scaling. The system is designed to handle high traffic loads while maintaining reliability and data consistency.

## Architecture

The application is divided into the following microservices:

- **Product Service**: Manages product catalog, categories, and inventory
- **Order Service**: Handles order processing, status management, and history
- **User Service**: Manages user accounts, authentication, and profiles
- **Payment Service**: Processes payments and handles financial transactions
- **Notification Service**: Sends notifications via email, SMS, and push notifications
- **API Gateway**: Single entry point for all client requests, handling routing and load balancing

## Tech Stack

- **Java/Spring Boot**: Core framework for all microservices
- **Spring Cloud**: For service discovery, configuration management, and circuit breaking
- **MongoDB**: Document database for products catalog
- **PostgreSQL**: Relational database for user and order information
- **RabbitMQ**: Message broker for asynchronous communication between services
- **Docker**: Containerization for easy deployment
- **Kubernetes**: Container orchestration for scaling and management
- **JWT**: Authentication and authorization

## Getting Started

### Prerequisites

- JDK 17 or higher
- Docker and Docker Compose
- Maven
- Kubernetes cluster (for production deployment)

### Local Development Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/pisatishivatmika/E-Commerce-Backend_Microservices.git
   cd E-Commerce-Backend_Microservices
   ```

2. Build all services:
   ```bash
   mvn clean package -DskipTests
   ```

3. Start infrastructure services with Docker Compose:
   ```bash
   docker-compose -f docker-compose-infra.yml up -d
   ```

4. Start all microservices:
   ```bash
   docker-compose up -d
   ```

5. The API Gateway will be accessible at http://localhost:8080

### Configuration

Each microservice has its own configuration in the `config` directory. Configuration properties include:

- Database connection settings
- Service discovery information
- Message broker configuration
- Security settings

## API Documentation

API documentation is available via Swagger UI once the services are running:

- Product Service: http://localhost:8081/swagger-ui.html
- Order Service: http://localhost:8082/swagger-ui.html
- User Service: http://localhost:8083/swagger-ui.html
- Payment Service: http://localhost:8084/swagger-ui.html

## Testing

The project includes comprehensive unit and integration tests. To run tests:

```bash
mvn test
```

For integration tests that require infrastructure components:

```bash
mvn verify -P integration-tests
```

## Deployment

### Docker Deployment

1. Build Docker images for all services:
   ```bash
   docker-compose build
   ```

2. Push images to your container registry:
   ```bash
   docker-compose push
   ```

### Kubernetes Deployment

Kubernetes deployment manifests are located in the `k8s` directory:

1. Apply infrastructure configurations:
   ```bash
   kubectl apply -f k8s/infra/
   ```

2. Deploy services:
   ```bash
   kubectl apply -f k8s/services/
   ```

## Monitoring and Observability

- **Prometheus**: Metrics collection
- **Grafana**: Visualization dashboards
- **ELK Stack**: Log aggregation and analysis
- **Jaeger**: Distributed tracing

## Performance

The system is designed to handle high throughput:

- Horizontal scaling capabilities
- Caching strategies
- Database optimization
- Message queue for asynchronous processing

## Security

- JWT-based authentication
- HTTPS/TLS encryption
- Input validation
- Role-based access control
- Rate limiting

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

