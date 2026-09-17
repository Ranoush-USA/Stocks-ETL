Stocks ETL Pipeline\
A production-ready ETL pipeline for processing stock market data using Databricks Lakehouse architecture.\
This project implements a medallion architecture (Bronze → Silver → Gold) with automated data quality checks and orchestrated execution.\

Architecture
This project uses a three-layer medallion architecture:\

Bronze Layer (bronze schema): Raw, unprocessed stock data ingestion with full historical refresh capability\
Silver Layer (silver schema): Cleaned and validated data with quality checks applied\
Gold Layer (gold schema): Business-ready aggregations and analytics-optimized datasets\
Quarantine Layer (quarantine schema): Records that fail data quality validations\

Project Structure\
Pipeline Flow\
The Stocks_Job orchestrates three sequential Spark Declarative Pipelines:\

Stocks_bronze → Ingests raw stock data with full refresh\
Stocks_Silver → Cleanses and validates bronze data (depends on bronze completion)\
Stocks_Gold → Creates business aggregations (depends on silver completion)\

Configuration\
Schemas\
Catalog: workspace (Unity Catalog)\
Bronze Schema: Raw ingested data\
Silver Schema: Cleaned validated data\
Gold Schema: Business-ready aggregations\
Quarantine Schema: Failed quality check records\

Deployment Targets\
dev (default): Development environment with full debugging capabilities\
prod: Production environment with controlled access (rana@ghazzi.com)\

Technology Stack\
Platform: Databricks on AWS\
Compute: Serverless (Photon-accelerated)\
Pipeline Type: Spark Declarative Pipelines (Lakeflow)\
Orchestration: Databricks Jobs with task dependencie\
Performance: Queue-enabled with performance optimization\
Getting Started\

1. Deployment\
Click the deployment rocket 🚀 in the left sidebar to open the Deployments panel, then click Deploy.\

Alternatively, use the Databricks CLI:\

2. Running the Pipeline\
UI: Hover over the resource in the Deployments panel and click Run\
CLI:\
databricks bundle run Stocks_Job --target dev\
3. Managing Resources\
Use the Add dropdown to add resources to the bundle\
Click Schedule on a notebook within the bundle to create a job definition\
Features\
✅ Automated data quality validation with quarantine handling\
✅ Full refresh capability for historical reprocessing\
✅ Performance-optimized serverless execution\
✅ Dependency-aware orchestration\
✅ Unity Catalog integration for governance\
✅ Multi-environment deployment (dev/prod)\
Documentation
Declarative Automation Bundles in the workspace
Declarative Automation Bundles Configuration reference
Spark Declarative Pipelines
