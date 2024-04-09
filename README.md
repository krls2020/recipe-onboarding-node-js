# Zerops Hello Worlds Node.js

```yaml
project:
  name: zerops-hello-world-node-js
  tags:
    - zerops
    - hello-worlds

services:
  - hostname: nodejs20
    type: nodejs@20
    envSecrets:
      DB_HOST: db
      DB_NAME: db
      DB_PASS: ${db_password}
      DB_PORT: "5432"
      DB_USER: ${db_user}
      NODE_ENV: production
    ports:
      - port: 3000
        httpSupport: true
    enableSubdomainAccess: true
    buildFromGit: https://github.com/krls2020/recipe-onboarding-node-js
    minContainers: 1

  - hostname: adminer
    type: php-apache@8.0+2.4
    buildFromGit: https://github.com/zeropsio/recipe-adminer@main
    enableSubdomainAccess: true
    minContainers: 1
    maxContainers: 1

  - hostname: db
    type: postgresql@14
    mode: NON_HA
    priority: 1
```

