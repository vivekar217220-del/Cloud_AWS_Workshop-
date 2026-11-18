# RetailPulse

RetailPulse is a retail intelligence dashboard built for an AWS Cloud Workshop hackathon. It brings product trends, customer-review sentiment, and rule-based alerts together so a small retailer can see which products and regions warrant attention. The project was a top finalist at the AWS Cloud Hackathon in March 2026.

![RetailPulse dashboard screenshot](<Screenshot 2026-03-22 161611.png>)

## Dashboard views

| View | What it shows |
| --- | --- |
| Overview | Product, review, trend, and alert counts at a glance |
| Products | Review counts, average ratings, and sentiment by product |
| Trends | Product momentum and regional signals |
| Alerts | Prioritized items generated from review or trend conditions |
| Regional view | City-level distributions to help compare customer response across locations |

## Workshop architecture

```text
Reviews, trend data, and alert rules -> Amazon S3
  -> AWS Lambda for ingestion, sentiment requests, and trend processing
     -> Amazon Comprehend for sentiment classification
     -> Amazon DynamoDB for processed records
  -> Amazon API Gateway -> Dashboard JSON

Amazon S3 and CloudFront -> Dashboard HTML -> Browser
```

S3 held the workshop inputs and also hosted the static website. Lambda handled ingestion, sentiment processing, trend detection, and API responses. Amazon Comprehend supplied sentiment scores for customer reviews. DynamoDB held the resulting product, sentiment, trend, and alert records. The dashboard used API Gateway for data access, and CloudFront served the frontend.

The browser implementation has controls to request ingestion and analysis, then refresh the dashboard. Those operations require a running workshop-compatible API. The checked-in frontend can also render its own embedded sample response.

## Explore the demo

1. Download or clone the repository and open [index.html](index.html) in a browser.
2. If the dashboard reports that it could not reach the API, select **Load Demo Data**.
3. Compare the overview counts with the product and alert views. Inspect the trends and regional views to see how the same records are summarized.
4. If charts appear blank, check that the browser can load the page's externally hosted chart library.

The demo data is a fixed browser-side snapshot. Use it to explore the interface and review the separate JSON fixtures for examples of the workshop inputs.

## Repository guide

| File | Purpose |
| --- | --- |
| [index.html](index.html) | Dashboard markup, styles, charts, API calls, and sample-data fallback |
| [reviews.json](reviews.json) | Sample product reviews |
| [market_trends.json](market_trends.json) | Sample product and regional trend records |
| [alert_rules.json](alert_rules.json) | Example conditions used to define alerts |
| [Dashboard screenshot](<Screenshot 2026-03-22 161611.png>) and [additional screenshot](<Screenshot 2026-03-22 164943.png>) | Views captured during the workshop |

This repository contains the dashboard, sample inputs, and screenshots. Recreating the live workflow requires provisioning the backend services and configuring the dashboard for your endpoint. The Lambda implementation and infrastructure configuration are outside this repository.

## Contributors

- **Vivek Chaudhary** led project development and architecture, including core backend services and AWS integrations.
- **Manav Chaudhari** co-developed the project and contributed to serverless design, frontend and backend integration, testing, and documentation.
