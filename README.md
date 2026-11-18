# RetailPulse

A retail intelligence dashboard built during an AWS Cloud Workshop. It brings product trends, customer-review sentiment, and alert rules into one interface for small store owners. RetailPulse was a top finalist at the AWS Cloud Hackathon in March 2026.

![RetailPulse dashboard screenshot](<Screenshot 2026-03-22 161611.png>)

## What the dashboard shows

- Product and regional trends
- Customer-review sentiment from Amazon Comprehend
- Alerts generated from rules and trend signals

## Workshop architecture

| Stage | AWS services |
| --- | --- |
| Input and data storage | Amazon S3 for source data and DynamoDB for application records |
| Processing | AWS Lambda for ingestion and trend processing, with Amazon Comprehend for sentiment |
| Delivery | API Gateway for REST endpoints and CloudFront with S3 for the dashboard |

## Explore the demo

Open [index.html](index.html) in a browser. The dashboard can display bundled sample data if the workshop API is unavailable. The repository contains the frontend, sample inputs, and screenshots.

- [Sample reviews](reviews.json), [market trends](market_trends.json), and [alert rules](alert_rules.json)
- [Additional dashboard screenshot](<Screenshot 2026-03-22 164943.png>)

## Contributors

- **Vivek Chaudhary** — Led the project and architecture, and implemented core backend services and AWS integrations.
- **Manav Chaudhari** — Co-developed the application and contributed to serverless design, integration, testing, and documentation.
