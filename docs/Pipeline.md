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