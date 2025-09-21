flowchart TD
    A([START]) --> B[Developer pushes code to GitHub (master branch)]
    B --> C[Git tracks changes]
    C --> D[Jenkins triggers CI/CD pipeline]
    D --> E[Maven builds microservice application]
    E --> F[Run JUnit & TestNG tests]
    F -->|Fail| G[STOP & send feedback to developer]
    F -->|Pass| H[Package code into Docker container]

    H --> I[Terraform provisions Test Server (AWS)]
    I --> J[Ansible configures Test Server]
    J --> K[Deploy Docker containerized app to Test Server]
    K --> L[Selenium runs automated tests]

    L -->|Fail| M[STOP & send feedback]
    L -->|Pass| N[Terraform provisions Prod Server (AWS)]
    N --> O[Ansible configures Prod Server]
    O --> P[Deploy Docker containerized app to Prod Server]

    P --> Q[Continuous Monitoring (Prometheus)]
    Q --> R[Visualization Dashboard (Grafana: CPU, Disk, Memory)]
    R --> S([END])
