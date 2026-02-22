Link For The Project: https://production.d1kjayvs6x5ovj.amplifyapp.com



☁️ Cloud Fun Facts Generator

A serverless web application designed to deliver dynamic cloud computing facts. This project demonstrates the integration of core AWS services to build a scalable, cost-effective, and fully decoupled cloud architecture.

🏗️ Architecture

The application follows a Serverless-First approach, ensuring zero server management and pay-as-you-go pricing.

The Flow:

Frontend: Hosted on AWS Amplify, providing a responsive UI for users.

API Layer: Amazon API Gateway acts as the entry point, handling HTTP requests and routing.

Compute: AWS Lambda (Python) processes logic, fetching data from the database.

Database: Amazon DynamoDB stores cloud facts in a NoSQL format for high-speed retrieval.

Security: AWS IAM roles and policies strictly manage permissions between services.

graph LR
    %% Node Tanımları
    Browser[🖥️ Kullanıcı Tarayıcısı]
    Amplify[🚀 AWS Amplify\n(Frontend Hosting)]
    APIGW[🚪 Amazon API Gateway\n(REST Endpoint)]
    Lambda[🧠 AWS Lambda\n(Backend Mantığı)]
    DDB[(🗄️ Amazon DynamoDB\nVeri Depolama)]

    %% Akış Tanımları
    Browser -- 1. Siteyi Yükle --> Amplify
    Browser -- 2. Butona Tıkla\n(HTTP GET İsteği) --> APIGW
    APIGW -- 3. Fonksiyonu Tetikle --> Lambda
    Lambda -- 4. Veri Oku\n(IAM Yetkisi ile) --> DDB
    DDB -.->|5. Veriyi Dön| Lambda
    Lambda -.->|6. JSON Yanıtı| APIGW
    APIGW -.->|7. Sonucu Göster| Browser

    %% Stil Tanımları (Opsiyonel)
    classDef aws fill:#FF9900,stroke:#232F3E,stroke-width:2px,color:white;
    classDef client fill:#f9f,stroke:#333,stroke-width:2px;
    class APIGW,Lambda,DDB,Amplify aws;
    class Browser client;



























🚀 Key Features & Engineering Challenges

1. Cross-Origin Resource Sharing (CORS)
One of the primary challenges was enabling secure communication between the Amplify domain and the API Gateway endpoint. I resolved this by configuring CORS headers both in the API Gateway settings and within the Lambda function's response object.

2. Least Privilege Principle (IAM)
Security was a priority. I configured custom IAM Roles to ensure the Lambda function had the "Least Privilege" necessary—only allowing GetItem and Scan operations on the specific DynamoDB table, minimizing the attack surface.

3. Scalability & Cost Optimization
By choosing a serverless architecture, the application scales automatically with traffic. Since AWS Lambda and DynamoDB offer a generous "Always Free" tier, the operational cost remains near $0.00 for standard portfolio traffic.
