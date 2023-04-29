---
marp: true
paginate: true
headingDivider: 2
---

<!--
To enable HTML, add the following in settings.json
    "markdown.marp.enableHtml" : true
Reference:
 https://laravel-school.com/snippet/how-to-enable-mermaid-or-html-directive-with-marp-in-vs-code-62 
-->

# Summary of ["Machine Learning Operations (MLOps): Overview, Definition, and Architecture"](https://arxiv.org/abs/2205.02302)

<p style="text-align:center;">Yusuke Minami</p>


## What is MLOps?

- ML engineering practice
- designing and maintaining productive ML
- ML automated and operationalized with DevOps

## What is DevOps?

- emerged in the years 2008/2009 and aims to reduce issues in software development 
- the goal of eliminating the gap between development and operations 
- ensures automation with continuous integration, continuous delivery, and continuous deployment (CI/CD), thus allowing for fast, frequent, and reliable releases.
- designed to ensure continuous testing, quality assurance, continuous monitoring, logging, and feedback loops. 

## 6 groups of DevOps tools

- collaboration and knowledge sharing (e.g., Slack, Trello, GitLab wiki)
- source code management (e.g., GitHub, GitLab)
- build process (e.g., Maven)
- continuous integration (e.g., Jenkins, GitLab CI), 
- deployment automation (e.g., Kubernetes, Docker),
- monitoring and logging (e.g., Prometheus, Logstash)

## Methodology 1: Literature review

27 peer-reviewed articles found by search query:
- "Machine Learning" AND either of:
  - "DevOps"
  - "CICD"
  - "Continuous Integration"
  - "Continuous Delivery"
  - "Continuous Deployment"
- "MLOps"
- "CD4ML"

## Methodology 2: Tools

![h:600](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200036.png)

## Methodology 2: Tools (cont'd)

![h:200](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200331.png)

## Methodology 3: Interviews

8 professionals found in Linkedin

![h:550](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200231.png)

## 9 Principles

P1. CI/CD automation: continuous integration/delivery/deployment

P2. Workflow orchestration

P3. Reproducibility: an ML experiment and obtain the exact same results 

P4. Versioning: Versioning ensures the versioning of data, model, and code to enable not only reproducibility, but also traceability (for compliance and auditing reasons) 

P5. Collaboration: work collaboratively on data, model, and code

P6. Continuous ML training & evaluation: retraining of the ML model based on new data

P7. ML metadata tracking/logging: used parameters, the resulting performance metrics, data and code used

P8. Continuous monitoring: infrastructure resources and model serving performance 

P9 Feedback loops

## 9 Components

C1. CI/CD Component (P1, P6, P9)
C2. Source Code Repository (P4, P5)
C3. Workflow Orchestration Component (P2, P3, P6)
C4. Feature Store System (P3, P4)
C5. Model Training Infrastructure (P6)
C6. Model Registry (P3, P4)
C7. ML Metadata Stores (P4, P7)
C8. Model Serving Component (P1)
C9. Monitoring Component (P8, P9)

## 7 Roles

R1. Business Stakeholder (similar roles: Product Owner, Project Manager)
R2. Solution Architect (similar role: IT Architect)
R3. Data Scientist (similar roles: ML Specialist, ML Developer)
R4. Data Engineer (similar role: DataOps Engineer)
R5. Software Engineer
R6. DevOps Engineer
R7. ML Engineer/MLOps Engineer

## Roles around ML Engineer/MLOps Engineer

![h:600](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122200808.png)

## MLOps workflow 

![h:600](https://cdn-ak.f.st-hatena.com/images/fotolife/n/nsakki55/20230122/20230122202233.png)

## MLOps workflow (core part extracted and restructured)

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

## Conceptualization: Define MLOps 

- MLOps (Machine Learning Operations) is a paradigm, including aspects like best practices, sets of concepts, as well as a development culture when it comes to the end-to-end conceptualization, implementation, monitoring, deployment, and scalability of machine learning products. 

- Most of all, it is an engineering practice that leverages three contributing disciplines: machine learning, software engineering (especially DevOps), and data engineering. 

- MLOps is aimed at productionizing machine learning systems by bridging the gap between development (Dev) and operations (Ops). 

## Open Challenges

- Organizational challenges
- ML system challenges
- Operational challenges

## Conclusion

- The academic space has focused intensively on machine learning model building and benchmarking, but too little on operating complex machine learning systems in real-world scenarios
- Defined MLOps and its associated concepts
- Hopefully assist successful ML projects in the future

## References

- https://arxiv.org/abs/2205.02302
- https://nsakki55.hatenablog.com/entry/2023/01/23/102630
