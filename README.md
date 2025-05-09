# AWS Serverless CRUD REST API

This project is a fully serverless REST API built using the **Serverless Framework**, **AWS API Gateway**, **AWS Lambda**, and **Amazon DynamoDB**. It supports full CRUD (Create, Read, Update, Delete) operations via HTTP methods. All integration with DynamoDB is done through Lambda functions — **no direct service proxy integration** is used.

## 🚀 Features

- Serverless architecture using AWS Lambda
- RESTful endpoints with API Gateway
- CRUD operations: Create, Read (single and all), Update, Delete
- DynamoDB for storage (accessed via Lambda)
- Written in **Rust**
- Easily deployable via the Serverless Framework

## 🛠️ Tech Stack

- **AWS Lambda**
- **API Gateway**
- **DynamoDB**
- **Serverless Framework**
- **Node.js**

## 📁 Project Structure

```
.
├── handler.js              # Main Lambda handlers for CRUD
├── serverless.yml          # Serverless Framework config
├── utils/                  # Utility functions (e.g., DynamoDB client)
├── package.json
└── README.md
```

## 📦 Installation

1. **Install Serverless Framework:**

```bash
npm install -g serverless
```

2. **Clone the repository:**

```bash
git clone https://github.com/yourusername/aws-serverless-crud-api.git
cd aws-serverless-crud-api
```

3. **Install dependencies:**

```bash
npm install
```

4. **Configure AWS credentials:**

```bash
aws configure
```

## 🚀 Deployment

Deploy the entire stack to AWS:

```bash
serverless deploy
```

This will output the REST API endpoints.

## 🧪 Usage

Once deployed, you’ll get a base URL like:

```
https://your-api-id.execute-api.region.amazonaws.com/dev
```

### Endpoints

| Method | Path              | Description        |
|--------|-------------------|--------------------|
| POST   | /items            | Create an item     |
| GET    | /items            | Get all items      |
| GET    | /items/{id}       | Get a single item  |
| PUT    | /items/{id}       | Update an item     |
| DELETE | /items/{id}       | Delete an item     |

### Example Request (Create)

```bash
curl -X POST https://your-api-id.execute-api.region.amazonaws.com/dev/items \
  -H "Content-Type: application/json" \
  -d '{"id": "1", "name": "Item 1", "description": "A sample item"}'
```

## 🔐 IAM & Permissions

Lambda functions are granted fine-grained permissions to access the specific DynamoDB table defined in `serverless.yml`.

## 🧹 Teardown

To remove all AWS resources:

```bash
serverless remove
```

## 📌 Notes

- This project **does not use service proxy integration** (i.e., API Gateway to DynamoDB directly). All data access is via Lambda handlers.
- Suitable for learning and small-to-medium scale production apps.

## 📄 License

MIT © [Your Name]
