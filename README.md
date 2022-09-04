### Dependencies

```
- Node v14.15.1 (LTS)

- npm 6.14.8 (LTS)

- AWS CLI

- AWS EB CLI

- AWS RDS database running Postgres.

- AWS S3 bucket for Frontend.

- AWS Elastic Beanstalk for Backend.

```

### AWS Cloud Setup

- RDS - Database Host: postgres.c5tr5ffa6tbo.us-east-1.rds.amazonaws.com
- RDS - Database Port: 5432
- RDS - Database Name: postgres

- S3 Endpoint - Frontend: http://udagram-fwd-web-app-hosting.s3-website-us-east-1.amazonaws.com/

- Elastic Beanstalk URL - Backend: http://udagram-api-dev.eba-rqgi5yn5.us-east-1.elasticbeanstalk.com/

### Pipeline

From the root of the project:

- To install frontend dependencies run. - `npm run frontend:install`
- To build the Angular/Frontend run. - `npm run frontend:build`
- To deploy the project to S3 using `./udagram-frontend/bin/deploy.sh` deploy script run. - `npm run frontend:deploy`
- To install api dependencies run. - `npm run api:install`
- To build the api run. - `npm run api:build`
- To deploy the project to EB using run - `npm run api:deploy`

### CircleCi

The order of the CirleCi jobs:

- Setting Env Variables.
- Install NodeJS.
- Checkout Code & Cloning the Repo.
- Install AWS CLI v2.
- Configure AWS AccessKeyID.
- Configure AWS Region.
- Backend:
  - Install dependencies.
  - Change The main entry point in package.json.
  - Build the app.
  - Install AWS Elastic Beanstalk CLI.
  - Deploy the app to AWS Elastic Beanstalk.
- Frontend:
  - Install dependencies.
  - Build the angular.
  - Deploy the site to AWS S3.

### Documentation

- Screenshots of the AWS configurations and the CircleCI are in `./docs/screenshots/`
- Diagrams of the AWS and the Pipeline are in `./docs/diagrams/`
- Setup steps are in `./docs/setup/md/`
