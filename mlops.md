---
marp: true
paginate: true
headingDivider: 2
---

<!--
To convert this markdown to slides, Install "Marp for VS Code" in VS Code.
https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode

To enable HTML for the Mermaid diagram, add the following line in VS Code's settings.json
    "markdown.marp.enableHtml" : true
Reference:
 https://laravel-school.com/snippet/how-to-enable-mermaid-or-html-directive-with-marp-in-vs-code-62 
-->

# Summary of ["Machine Learning Operations (MLOps): Overview, Definition, and Architecture"](https://arxiv.org/abs/2205.02302)

<p style="text-align:center;">Yusuke Minami</p>


## [1. Introduction]

What is MLOps?
To answer this question, researched:

(a) principles
(b) components
(c) roles
(d) architecture

## [2. Foundations of DevOps]

- emerged in the years 2008/2009 and aims to reduce issues in software development 
- the goal of eliminating the gap between development and operations 
- ensures automation with continuous integration, continuous delivery, and continuous deployment (CI/CD), thus allowing for fast, frequent, and reliable releases.
- designed to ensure continuous testing, quality assurance, continuous monitoring, logging, and feedback loops. 

## [2. Foundations of DevOps] 6 groups of DevOps tools

- collaboration and knowledge sharing (e.g., Slack, Trello, GitLab wiki)
- source code management (e.g., GitHub, GitLab)
- build process (e.g., Maven)
- continuous integration (e.g., Jenkins, GitLab CI), 
- deployment automation (e.g., Kubernetes, Docker),
- monitoring and logging (e.g., Prometheus, Logstash)

## [3. Methodology]

1. Literature review
2. Tools
3. Interviews

## [3. Methodology] 1. Literature review

27 peer-reviewed articles found by search query:
- "Machine Learning" AND either of:
  - "DevOps"
  - "CICD"
  - "Continuous Integration"
  - "Continuous Delivery"
  - "Continuous Deployment"
- "MLOps"
- "CD4ML"

## [3. Methodology] 2. Tools

![h:600](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200036.png)

## [3. Methodology] 2. Tools (cont'd)

![h:200](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200331.png)

## [3. Methodology] 3. Interviews

8 professionals found in Linkedin

![h:550](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200231.png)

## [4. Results] 1. Principles

P1. CI/CD automation: continuous integration/delivery/deployment

P2. Workflow orchestration

P3. Reproducibility: obtain the exact same results 

P4. Versioning of data, model, and code

P5. Collaboration: work collaboratively on data, model, and code

P6. Continuous ML training & evaluation: retraining of the ML model based on new data

P7. ML metadata tracking/logging: used parameters, the resulting performance metrics, data and code used

P8. Continuous monitoring: infrastructure resources and model serving performance 

P9 Feedback loops

## [4. Results] 2. Components

C1. CI/CD Component (P1, P6, P9) e.g. Jenkins, GitHub actions
C2. Source Code Repository (P4, P5) e.g. Bitbucket, GitLab, GitHub, Gitea
C3. Workflow Orchestration Component (P2, P3, P6) e.g. Apache Airflow, Kubeflow Pipelines, Luigi, AWS SageMaker Pipelines, Azure Pipelines
C4. Feature Store System (P3, P4) e.g. Google Feast, Amazon AWS Feature Store, Tecton.ai, Hopswork.ai
C5. Model Training Infrastructure (P6) e.g. Kubernetes, Red Hat OpenShift
C6. Model Registry (P3, P4) e.g. MLflow, AWS SageMaker Model Registry, Microsoft Azure ML Model Registry, Nepture.ai
C7. ML Metadata Stores (P4, P7) e.g. Kubeflow Pipelines, AWS SageMaker Pipelines, Azure ML, IBM Watson Studio, MLflow
C8. Model Serving Component (P1) e.g. KServing, TensorFlow Serving, Seldion.io
C9. Monitoring Component (P8, P9) e.g. Prometheus with Grafana, ELK stack, TensorBoard, Kubeflow, MLflow, AWS SageMaker model monitor, cloud watch

## [4. Results] 3. Roles

R1. Business Stakeholder (similar roles: Product Owner, Project Manager)
R2. Solution Architect (similar role: IT Architect)
R3. Data Scientist (similar roles: ML Specialist, ML Developer)
R4. Data Engineer (similar role: DataOps Engineer)
R5. Software Engineer
R6. DevOps Engineer
R7. ML Engineer/MLOps Engineer

## [4. Results] 3. Roles around ML Engineer/MLOps Engineer

![h:600](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200808.png)

## [5. Architecture and Workflow]

![h:600](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122202233.png)

## [5. Architecture and Workflow] MLOps workflow (core part extracted and restructured)

<div class="mermaid">
flowchart LR
    subgraph Serving
        repo --> CI[continous\nintegration\n/ continuous\ndelivery\n\n] --> CD[continuous\ndeployment\n\n] --> serving[model\nserving\n\n] --> monitoring
        CI --> artifact_store[artifact\nstore\n e.g. \nImage \n Registry\n\n] -.-> CD
        serving_code[model\nserving\ncode\n\n] --> repo
        Model_Registry --> CD
    end
    subgraph Experimentation
        export -.-> Model_Registry
        training_code -.-> training
        sources[Data\nSources\n\n] --> analysis[data\nanalysis\n\n] --> prep[data\npreparation\n& validation\n \n] --> training[model\ntraining\n\n] --> validation[model\nvalidation\n\n] --> export[export\nmodel\n\n] --> repo[(Git\nrepo\n\n)]
        training_code[training\ncode\n\n] --> repo
        training --> metadata[ML\nmetadata\nstore\n\n]
    end
</div>

## [6. Conceptualization] Define MLOps 

- MLOps (Machine Learning Operations) is a paradigm including:
  - best practices
  - concepts
  - development culture 

- engineering practice that leverages:
  - machine learning
  - software engineering (especially DevOps)
  - data engineering. 

- bridge the gap between development (Dev) and operations (Ops). 

## [7. Open Challenges] 

- Organizational challenges
  - need culture shift away from model-driven toward product-oriented
  - teams work in silos rather than in cooperative setups
  - decision-makers need to be convinced that an increased MLOps maturity and a product-focused mindset will yield clear business improvements
- ML system challenges
  - difficult to precisely estimate the necessary infrastructure resources
  - require a high level of flexibility in terms of scalability of the infrastructure
- Operational challenges
  - require governance, versioning of data, model, and code to ensure robustness and reproducibility
  - failures can be a combination of ML infrastructure and software

## [8. Conclusion]

- the academic space has focused intensively on machine learning model building and benchmarking, but too little on operating complex machine learning systems in real-world scenarios
- MLOps and its associated concepts were defined
- common understanding will hopefully  assist successful ML projects in the future

## References for this summary

- Original paper: https://arxiv.org/abs/2205.02302
- Summary blog: https://nsakki55.hatenablog.com/entry/2023/01/23/102630

## Appendix

MLOps Maturity Levels

- 2 levels by Google: https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning

- 4 levels by Microsoft: https://learn.microsoft.com/en-us/azure/architecture/example-scenario/mlops/mlops-maturity-model

- 7 levels by MLOps Community: https://mlops.community/mlops-maturity-assessment/
