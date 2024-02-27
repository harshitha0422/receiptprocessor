# Receipt Processor

This repository contains the source code for the Receipt Processor project.

## Folder Structure

```plaintext
receiptprocessor/
│
├── backend/           # Backend source code files
│   ├── controllers/
│   │   └── test/      # Test files for controllers
│   ├── models/
│   ├── routes/
│   ├── utils/         # Utility files
│   │   └── test/      # Test files for utils
│   ├── Dockerfile     # Dockerfile for containerization
│   ├── main.go        # Main application logic
│   └── ...            # Other source files
│
├── docker-compose.yml # Docker Compose configuration
├── README.md          # Project documentation (you are here)
├── ...                # Other project files
```

## Getting Started
Follow the steps below to set up and run the Receipt Processor service.

### Prerequisites
Docker installed on your machine.

### Running the Service
#### 1. Clone the repository:
```plaintext
git clone https://github.com/harshitha0422/receiptprocessor.git
cd receiptprocessor
```

#### 2. Build and run the Docker containers using Docker Compose:
```plaintext
docker-compose up -d
```
This will start the service and expose it on port 9018.

#### 3. Check if the service is running by visiting http://localhost:9018 in your web browser or using a tool like curl or Postman.

Endpoint: Process Receipts

* Path: `/receipts/process`
* Method: `POST`
* Payload: Receipt JSON
* Response: JSON containing an id for the receipt.

**Request:** `http://localhost:9018/receipts/process`  
**Response:** `{ "id": "7fb1377b-b223-49d9-a31a-5a02701dd310" }`

Endpoint: Get Points

* Path: `/receipts/{id}/points`
* Method: `GET`
* Response: A JSON object containing the number of points awarded.
  
**Request:** `http://localhost:9018/receipts/7fb1377b-b223-49d9-a31a-5a02701dd310/points`  
**Response:** `{ "points": 32 }`

**Note:** After processing a receipt, subsequent GET requests to the same ID (`/receipts/{id}/points`) will return 0 points.


### Stopping the Service
To stop the service, run:
```plaintext
docker-compose down
```
