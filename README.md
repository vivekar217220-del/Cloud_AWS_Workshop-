# Cloud_AWS_Workshop-

🛒 RetailPulse — Retail & Market Intelligence Engine

Built during an AWS Cloud Workshop — Hackathon Project


🏆 About the Project
RetailPulse is a full-stack cloud-native web application built for small store owners to track their products, analyze customer sentiment, monitor regional sales trends, and receive real-time alerts — all from a single dashboard. This project was developed and presented as a Hackathon submission during an AWS Cloud Workshop.

☁️ What I Learned in the Workshop
During the workshop, I completed 4 hands-on mini projects before building the final hackathon project:

Project 1 — S3 Bucket : Uploading, managing, and hosting static files on Amazon S3
Project 2 — Cognito OTP : User authentication with OTP-based login using Amazon Cognito
Project 3 — DynamoDB + EC2 : Creating tables, inserting records, and running a simple EC2 instance
Project 4 — API Gateway : Building and connecting REST APIs to backend Lambda functions


🏗️ Architecture
The full system architecture follows a serverless AWS pipeline:
S3 Data Bucket (reviews.json · trends.json · alert_rules.json)
        ↓  trigger / read
AWS Lambda — 4 Functions (Python 3.9)
  ├── DataIngestion     → POST /ingest
  ├── SentimentAnalysis → POST /analyze
  ├── TrendDetection    → Scheduled
  └── APIHandler        → GET routes
        ↓  NLP call                    ↓  write
Amazon Comprehend              DynamoDB — 4 Tables
detect_sentiment()             Sentiments · Products
POS / NEG / NEUTRAL            Trends · Alerts
        ↓
API Gateway — REST, prod stage, CORS enabled
/dashboard · /products · /trends · /alerts · /sentiments
        ↓  HTTPS JSON
CloudFront + S3 Static Website
Hosts index.html · CDN delivery · HTTPS
        ↓
RetailPulse Dashboard (Browser)
9 products · 25 reviews · 13 alerts · regions map · rising trends

📊 Dashboard Features

9 Products Tracked across multiple regions
25 Reviews Analyzed using Amazon Comprehend NLP
4 Positive Products · 1 Needs Attention
13 Active Alerts · 4 Rising Trends
Regional Distribution — city-wise review breakdown across Goa, Mumbai, Delhi, Bangalore, Jaipur, Pune, Chennai, Hyderabad, Kolkata, and Rishikesh
Live Data — real-time ingestion and analysis pipeline


🗺️ Regional Intelligence
The dashboard shows area-wise trends for small store owners including thumbs up / thumbs down sentiment per city, helping local businesses understand which regions are responding positively to their products and which need attention.

🚀 How It Works

Store owner data (reviews, product info) is uploaded to S3
Lambda triggers ingestion and calls Amazon Comprehend for sentiment
Results are written to DynamoDB across 4 tables
API Gateway exposes REST endpoints to the frontend
CloudFront delivers the static dashboard over HTTPS
Dashboard displays live metrics, regional trends, and alerts


🎯 Key Takeaways

Hands-on experience with core AWS serverless architecture
Built a real-world use case for small and local business owners
Integrated NLP sentiment analysis using managed AWS AI services
Learned end-to-end cloud deployment from storage to CDN delivery
Participated and built this under hackathon conditions.

The project used a total of 8 AWS services. Amazon S3 was used for two purposes — storing raw data files like reviews.json and trends.json, and also hosting the static frontend website. AWS Lambda served as the entire serverless backend with 4 Python 3.9 functions handling data ingestion, sentiment analysis, trend detection, and API routing. Amazon Cognito was used for secure user authentication with OTP-based login. Amazon DynamoDB acted as the NoSQL database with 4 tables storing Sentiments, Products, Trends, and Alerts. Amazon Comprehend provided the AI-powered NLP sentiment analysis, classifying each customer review as Positive, Negative, or Neutral. API Gateway exposed all the REST endpoints to the frontend with CORS enabled on the production stage. Amazon CloudFront handled CDN delivery of the dashboard over HTTPS to the browser. Finally, Amazon EC2 was used as a hands-on virtual server instance during the workshop training mini projects.
