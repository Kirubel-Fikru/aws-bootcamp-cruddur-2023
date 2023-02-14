# Week 0 — Billing and Architecture

## Business Scenario

- Your company has asked to put together a technical presentation on the proposed architecture that will be implemented so it can be reviewed by the fractional CTO.
- Your presentation must include a technical architectural diagram and breakdown of possible services used along with their justification.
- The company also wants to generally know what spend we expect to encounter and how we will ensure we keep our spending low.

### CRUDER ?
Blogging app, Ephemeral, cloud native, Targeted to busy professional, no permanent presence online, Time limited
## AWS Billing and Free Tier
### Walkthrough
* Billing Dashboard
* Pricing differs with region
* **Creating Billing alarm** :There are two ways of creating a billing alarm
	*  Old  Method :  Billing Preference => Email/Free tier Usage alerts/Recieve Alert
	*  New Method: Cloud watch (Only in northern virginia) =>  Alarms => in alarm => Create alarm => Select metrics => Billing => Total estimated charges => Select metrics=> Metric name/currency/statstics/period/Conditions(Threshold value) => Next => Notification (Email end point) =>Create alarm
*  **Creating budget**:  To create a Budget
	*  Budgets => Create budget => Budget setup /Templates(Monthly)/Name/Budget amount(10$)/Email/
*  **Cost allocation Tags** (Key value pairs)  :A tag is a label that you or AWS assigns to an AWS resource. Each tag consists of a key and a value. For each resource, each tag key must be unique, and each tag key can have only one value. You can use tags to organize your resources, and cost allocation tags to track your AWS costs on a detailed level. After you activate cost allocation tags, AWS uses the cost allocation tags to organize your resource costs on your cost allocation report, to make it easier for you to categorize and track your AWS costs.  To create CaT:  
	*  Go to a Service (EC2) => Tags => Manage tags (Key/Value) => Save => Go to Billing Service => Cost allocation tag => Activate
* 	**Cost Explorer** : AWS Cost Explorer has an easy-to-use interface that lets you visualize, understand, and manage your AWS costs and usage over time. We can use report parameters to  filter our search.
* 	**Report**: The Reports page provides default reports. You can also create new reports with existing templates. The reports include Cost and usage report, Savings Plans utilization report, Savings Plans coverage report, reservation utilization report, and reservation coverage report.
* 	**Credits** AWS credits are applied to bills to help cover costs that are associated with eligible services. Credits are applied until they are exhausted or they expire.
* 	**Aws Pricing Calculator**: Configure a cost estimate that fits your unique business or personal needs with AWS products and services.
* 	**Aws Free Tier**: 
	* 	*Free trials*
	* 	*12 month free*
	* 	*Alway free for all*
	*   Compute = 750 hr per month EC2 (windows and linux t2.micro and t3.micro instances)
	*   Storage = 5Gb of standard storage(20000 GET requests and 2000 Put Request)
	*   Database = 750 hr per month RDS(single_AZ db.t2/t3/t4g.micro instances running MySQL,MariaDB,PostgreSQL. 20 gb general purpose SSD and for backups/snapshots each )
	* 	Database = 25 gb 0f Dynamo db storage (25 WCU and RCU each(Enough to handle 200 requests per month))
	* 	Machine Learning = Amazon SageMaker 2 month free trial
	* 	Compute = 1 million Lambda requests per month (Upto 3.2 million seconds of compute time per month)
	* 	2 Month amazon Redshift Free trial
	* 	750 hours per month of amazon open search service
	* 	[Further services included in Free Tier](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all&awsm.page-all-free-tier=2)



## Architecture
**TOGAF?**
Togaf is an architecture framework that provides the methods and tools for assisting in the acceptance, production, use, and maintenance of an enterprise architecture. It is based on an iterative process model supported by best practices and a re-usable set of existing architecture assets"
* The most popular framework for Enterprose architecture
* Common dictionary of words to convey desired outcomes 
* Meta-model for the creation of the underlying projects 
* Maps closelt to the well architectured tool
### Well Architectured Frameowrk: **6 Pillars?**
1. Operational Exellence
2. Security
3. Reliabilty
4. Performance Efficiency
5. Cost Optimization
6. Sustainability
