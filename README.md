# Fabric Medallion Architecture Demo

A demo showing simple [ETL](https://learn.microsoft.com/en-us/azure/architecture/data-guide/relational-data/etl) (extract, transform and load) process utilizing [Medallion architecture](https://learn.microsoft.com/en-us/azure/databricks/lakehouse/medallion) on Microsoft Fabric platform. The features include:

- Test-driven development (on silver and gold layers using Notebooks)
- Use [South Australia crime statistics](https://data.sa.gov.au/data/dataset/crime-statistics)
- Simple Power BI dashboard demo
- TODO: Analysis with SA economical statistics, etc

## Project details:

<details open>

<summary>`01_bronze` directory</summary>

- [`nb_01_ingest_bronze.ipynb`](./01_bronze/nb_01_ingest_bronze.ipynb): notebook pipeline to download SA crime records
- [`pl_01_ingest_bronze.json`](./01_bronze/pl_01_ingest_bronze.json): Pipeline `JSON` file to download raw data from [Data SA](https://data.sa.gov.au/data/dataset/crime-statistics), including `.csv` and `.xlsx` files.

</details>

<details>
<summary>`02_silver` directory</summary>

- [`nb_02_sa_crime_record_wrangler.ipynb`](./02_silver/nb_02_sa_crime_record_wrangler.ipynb): class to clease and ingest SA crime records data
- [`nb_02_sa_crime_record_wrangler_tests.ipynb`](./02_silver/nb_02_sa_crime_record_wrangler_tests.ipynb): test units to test the wranger class.

	Call `%run` to import another notebook file, i.e. `SACrimeRecordWrangler` class.

	```
	%run nb_02_sa_crime_record_wrangler
	```

- [`nb_02_cleanse_silver.ipynb`](./02_silver/nb_02_cleanse_silver.ipynb): notebook to execute the ingestion and cleansing codes (two `Lakehouse`s are created, one for testing and another for dev env)

</details>

<details>

<summary>`pl_00_medallion.json` file</summary>

<summary>Project structure</summary>

```
fabric_sa_crime_records
├── 01_bronze
│   ├── nb_01_ingest_bronze.ipynb
│   └── pl_01_ingest_bronze.json
├── 02_silver
│   ├── nb_02_cleanse_silver.ipynb
│   ├── nb_02_sa_crime_record_wrangler_tests.ipynb
│   ├── nb_02_sa_crime_record_wrangler.ipynb
│   └── pl_02_silver_tests.json
├── 03_gold
│   ├── nb_03_crime_record_gold.ipynb
│   ├── nb_03_dim_date_wrangler_tests.ipynb
│   ├── nb_03_dim_date_wrangler.ipynb
│   ├── nb_03_dim_desc_wrangler_tests.ipynb
│   ├── nb_03_dim_desc_wrangler.ipynb
│   ├── nb_03_fact_record_wrangler_tests.ipynb
│   ├── nb_03_fact_record_wrangler.ipynb
│   └── pl_03_gold_tests.json
├── data_source
│   └── sa_crime_data_urls.csv
└── pl_00_medallion.json
```

</details>



## Todos:

- [x] Medallion ✅ 2025-07-06
	- [x] Bronze ✅ 2025-07-05
	- [x] Silver ✅ 2025-07-05
	- [x] Gold ✅ 2025-07-06
	- [x] Unit tests ✅ 2025-07-06
- [x] Pipelines ✅ 2025-07-06
- [ ] Analytics
	- [ ] Analysis with SA economical statistics
	- [x] Simple Power BI ✅ 2025-07-06
- [ ] CI/CD
	- [ ] Azure DevOps
	- [ ] Fabric Deployment
	- [ ] Automation
- [ ] Logging
- [ ] Security


## Acknowledgements

- [Microsoft Fabric](https://www.microsoft.com/en-us/microsoft-fabric)
- [Fabric Unit Test](https://www.youtube.com/watch?v=Y5f8T_lf77o)
- [Data SA (South Australian Government Data Directory)](https://data.sa.gov.au/data/dataset/crime-statistics)