# DevOps Pipeline Dashboard

## Overview

A real-time CI/CD monitoring platform that aggregates data from multiple sources (GitHub, AWS CloudWatch) and provides customizable tile-based visualizations with automated health roll-up for engineering teams.

## Features

- **Multi-Source Data Connectors**: Integrate with GitHub API, AWS CloudWatch, and extensible plugin architecture for additional data sources
- **Real-Time Dashboards**: Drag-and-drop tile customization with WebSocket-based live updates
- **Health Roll-Up System**: Hierarchical status aggregation from individual pipelines to system-level summaries
- **Configurable Alerts**: Threshold-based monitoring with webhook notifications (Slack, Teams)
- **Serverless Architecture**: Built on AWS Lambda for scalability and cost efficiency

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| Frontend | React 18, TypeScript, Tailwind CSS, Recharts |
| Backend | Node.js, Express, AWS Lambda, API Gateway |
| Database | DynamoDB |
| Integrations | GitHub API, AWS CloudWatch |
| DevOps | Docker, GitHub Actions, AWS CDK |

## Project Structure

```
devops-pipeline-dashboard/
├── frontend/
│   ├── src/
│   │   ├── components/       # React components
│   │   │   ├── Dashboard/    # Dashboard grid & tiles
│   │   │   ├── Charts/       # Visualization components
│   │   │   └── Alerts/       # Alert management UI
│   │   ├── hooks/            # Custom React hooks
│   │   ├── services/         # API client services
│   │   └── types/            # TypeScript definitions
│   └── package.json
├── backend/
│   ├── src/
│   │   ├── handlers/         # Lambda function handlers
│   │   ├── connectors/       # Data source plugins
│   │   │   ├── github/       # GitHub API integration
│   │   │   └── cloudwatch/   # AWS CloudWatch integration
│   │   ├── services/         # Business logic
│   │   └── utils/            # Helper utilities
│   └── serverless.yml
├── infrastructure/           # AWS CDK / CloudFormation
└── README.md
```

## Getting Started

### Prerequisites
- Node.js 18+
- AWS CLI configured
- GitHub Personal Access Token

### Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

### Backend Setup
```bash
cd backend
npm install
serverless deploy
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/pipelines | List all monitored pipelines |
| GET | /api/pipelines/{id}/runs | Get recent pipeline runs |
| GET | /api/metrics | Get aggregated metrics |
| GET | /api/health | Get system health roll-up |
| POST | /api/alerts | Create alert rule |
| WS | /ws/updates | Real-time data stream |

## Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   GitHub    │     │ CloudWatch  │     │  (Future)   │
│    API      │     │    API      │     │  Plugins    │
└──────┬──────┘     └──────┬──────┘     └──────┬──────┘
       │                   │                   │
       └───────────────────┼───────────────────┘
                           │
                    ┌──────▼──────┐
                    │   AWS API   │
                    │   Gateway   │
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │   Lambda    │
                    │  Functions  │
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │  DynamoDB   │
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │   React     │
                    │  Frontend   │
                    └─────────────┘
```

## Status

🚧 **In Development** - Core features being implemented

## Roadmap

- [x] Project setup & architecture design
- [ ] GitHub API connector
- [ ] CloudWatch metrics integration
- [ ] Dashboard tile components
- [ ] Health roll-up logic
- [ ] WebSocket real-time updates
- [ ] Alert configuration UI

## License

MIT License

## Contact

Rui Chen - [GitHub](https://github.com/2304685665-sketch)
