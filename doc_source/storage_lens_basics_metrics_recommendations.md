# Understanding Amazon S3 Storage Lens<a name="storage_lens_basics_metrics_recommendations"></a>

Amazon S3 Storage Lens provides a single view of object storage usage and activity across your entire Amazon S3 storage\. It includes drilldown options to generate insights at the organization, account, Region, bucket, or even prefix level\. 

Amazon S3 Storage Lens aggregates your usage and activity metrics and displays the information in the account snapshot on the Amazon S3 console home \(**Buckets**\) page, interactive dashboards, or through a metrics export that you can download in CSV or Parquet format\. You can use the dashboard to visualize insights and trends, flag outliers, and receive recommendations for optimizing storage costs and applying data protection best practices\. You can use S3 Storage Lens through the AWS Management Console, AWS CLI, AWS SDKs, or REST API\.

## Amazon S3 Storage Lens concepts and terminology<a name="storage_lens_basics"></a>

This section contains the terminology and concepts that are essential for understanding and using Amazon S3 Storage Lens successfully\.

**Topics**
+ [Configuration](#storage_lens_basics_configuration)
+ [Default dashboard](#storage_lens_basics_default_dashboard)
+ [Dashboards](#storage_lens_basics_dashboards)
+ [Account snapshot](#storage_lens_basics_account_snapshot)
+ [Metrics export](#storage_lens_basics_metrics_export)
+ [Home Region](#storage_lens_basics_home_region)
+ [Data available for queries](#storage_lens_basics_data_queries)
+ [Metrics types](#storage_lens_basics_metrics_types)
+ [Recommendations](#storage_lens_basics_recommendations)
+ [Metrics selection](#storage_lens_basics_metrics_selection)
+ [S3 Storage Lens and AWS Organizations](#storage_lens_basics_organizations)

### Configuration<a name="storage_lens_basics_configuration"></a>

Amazon S3 Storage Lens requires a *configuration* that contains the properties that are used to aggregate metrics on your behalf for a single dashboard or export\. This includes all or partial sections of your organization account’s storage, including filtering by Region, bucket, and prefix\-level \(available only with advanced metrics\) scope\. It includes information about whether you chose *free metrics* or *advanced metrics and recommendations*\. It also includes whether a metrics export is required, and information about where to place the metrics export if applicable\.

### Default dashboard<a name="storage_lens_basics_default_dashboard"></a>

The S3 Storage Lens default dashboard on the console is named **default\-account\-dashboard**\. S3 preconfigures this dashboard to visualize the summarized insights and trends of your entire account’s aggregated storage usage and activity metrics, and updates them daily in the Amazon S3 console\. You can't modify the configuration scope of the default dashboard, but you can upgrade the metrics selection from **free metrics** to the paid **advanced metrics and recommendations**\. You can also configure the optional metrics export, or even disable the dashboard\. However, you can't delete the default dashboard\.

**Note**  
If you disable your default dashboard, it is no longer updated, and you will no longer receive any new daily metrics in S3 Storage Lens, or in the account snapshot on S3 home \(**Buckets**\) page\. You can still see historic data in the dashboard until the 14\-day period that data is available for queries expires, or 15 months if you are subscribed to *advanced metrics and recommendations* for that dashboard\. You can re\-enable the dashboard within the expiration period to access this data\.

### Dashboards<a name="storage_lens_basics_dashboards"></a>

You can also use Amazon S3 Storage Lens to configure dashboards that visualize summarized insights and trends of aggregated storage usage and activity metrics that you can configure, updated daily on the Amazon S3 console\. You can create and modify S3 Storage Lens dashboards to express all or partial sections of your organization or account’s storage\. You can filter by AWS Region, bucket, and prefix \(available only with advanced metrics and recommendations\)\. You can also disable or delete dashboards\.

**Note**  
You can use S3 Storage Lens to create up to 50 dashboards per home Region\.
If you disable a dashboard, it is no longer updated, and you will no longer receive any new daily metrics\. You can still see historic data until the 14\-day expiration period \(or 15 months, if you subscribed to advanced metrics and recommendations for that dashboard\)\. You can re\-enable the dashboard within the expiration period to access this data\.
If you delete your dashboard, you lose all your dashboard configuration settings\. You will no longer receive any new daily metrics, and you also lose access to the historical data associated with that dashboard\. If you want to access the historic data for a deleted dashboard, you must create another dashboard with the same name in the same home Region\.
Organization\-level dashboards can only be limited to a Regional scope\.

### Account snapshot<a name="storage_lens_basics_account_snapshot"></a>

The S3 Storage Lens *account snapshot* displays your total storage, object count, and average object size on the S3 console home \(**Buckets**\) page by summarizing metrics from your default dashboard\. This gives you quick access to insights about your storage without having to leave the **Buckets** page\. The account snapshot also provides one\-click access to your S3 Storage Lens page, where you can conduct a deeper analysis of your usage and activity trends by AWS Region, storage class, bucket, or prefix\.

 You can upgrade the metrics selection in your **default\-account\-dashboard** from **free metrics** to the paid **advanced metrics and recommendations**\. You can then display all requests, bytes uploaded, and bytes downloaded in the S3 Storage Lens account snapshot\.

**Note**  
 You can't modify the dashboard scope of the **default dashboard** because it's linked to the **account snapshot**\. However, you can upgrade the metrics selection from **free metrics** to the paid **advanced metrics and recommendations**\. 
If you disable your default dashboard, your account snapshot is no longer updated\. You can re\-enable the **default\-account\-dashboard** to resume displaying metrics in the account snapshot\.

### Metrics export<a name="storage_lens_basics_metrics_export"></a>

An S3 Storage Lens *metrics export* is a file that contains all the metrics identified in your S3 Storage Lens configuration\. This information is generated daily in CSV or Parquet format in an S3 bucket of your choice for further analysis\. The S3 bucket for your metrics export must be in the same Region as your S3 Storage Lens configuration\. You can generate an S3 Storage Lens metrics export from the S3 console by editing your dashboard configuration, or by using the AWS CLI and SDKs\.

### Home Region<a name="storage_lens_basics_home_region"></a>

The home Region is the AWS Region where all Amazon S3 Storage Lens metrics for a given dashboard or configuration's are stored\. You must choose a home Region when you create your S3 Storage Lens dashboard or configuration\. After a home Region is assigned, it can't be changed\.

**Note**  
Creating a home Region is supported the following Regions:  
US East \(N\. Virginia\) – us\-east\-1
US East \(Ohio\) – us\-east\-2
US West \(N\. California\) – us\-west\-1
US West \(Oregon\) – us\-west\-2
Asia Pacific \(Mumbai\) – ap\-south\-1
Asia Pacific \(Osaka\) – ap\-northeast\-3
Asia Pacific \(Seoul\) – ap\-northeast\-2
Asia Pacific \(Singapore\) – ap\-southeast\-1
Asia Pacific \(Sydney\) – ap\-southeast\-2
Asia Pacific \(Tokyo\) – ap\-northeast\-1
Canada \(Central\) – ca\-central\-1
China \(Beijing\) – cn\-north\-1
China \(Ningxia\) – cn\-northwest\-1
Europe \(Frankfurt\) – eu\-central\-1
Europe \(Ireland\) – eu\-west\-1
Europe \(London\) – eu\-west\-2
Europe \(Paris\) – eu\-west\-3
Europe \(Stockholm\) – eu\-north\-1
South America \(São Paulo\) – sa\-east\-1

### Data available for queries<a name="storage_lens_basics_data_queries"></a>

You can use Amazon S3 Storage Lens metrics for queries so that you can see historical trends and compare differences in your storage usage and activity over time\. Metrics are available for a specific duration\. The duration depends on your [metrics selection](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage_lens_basics_metrics_recommendations.html#storage_lens_basics_metrics_selection) and cannot be modified\. Free metrics are available for queries for a 14\-day period, and advanced metrics are available for queries for a 15\-month period\.

### Metrics types<a name="storage_lens_basics_metrics_types"></a>

S3 Storage Lens offers two types of storage metrics: *usage* and *activity*\.
+ **Usage metrics**

  S3 Storage Lens collects *usage metrics* for all dashboards and configurations\. Usage metrics describe the size, quantity, and characteristics of your storage\. This includes the total bytes stored, object count, and average object size\. It also includes metrics that describe feature utilization, such as encrypted bytes, or delete market object counts\. For more information about the usage metrics aggregated by S3 Storage Lens, see [Metrics glossary](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage_lens_metrics_glossary.html)\.
+ **Activity metrics**

  S3 Storage Lens aggregates *activity metrics* for all dashboards and configurations that have the *advanced metrics and recommendations metrics* type enabled\. Activity metrics describe the details of how often your storage is requested\. This includes the number of requests by type, upload and download bytes, and errors\. For more information about the activity metrics that are aggregated by S3 Storage Lens, see [Metrics glossary](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage_lens_metrics_glossary.html)\.

### Recommendations<a name="storage_lens_basics_recommendations"></a>

S3 Storage Lens provides automated *recommendations* to help you optimize your storage\. Recommendations are placed contextually alongside relevant metrics in the S3 Storage Lens dashboard\. Historical data is not eligible for recommendations because recommendations are relevant to what is happening in the most recent period\. Recommendations only appear when they are relevant\.

S3 Storage Lens recommendations come in the following forms:
+ **Suggestions**

  *Suggestions* alert you to trends within your storage usage and activity that might indicate a storage cost optimization opportunity or data protection best practice\. You can use the suggested topics in the *Amazon S3 User Guide* and the S3 Storage Lens dashboard to drill down for more details about the specific Regions, buckets, or prefixes to further assist you\.
+ **Call\-outs**

  Call\-outs are recommendations that alert you to interesting anomalies within your storage usage and activity over a period that might need further attention or monitoring\.
  + **Outlier call\-outs**

    S3 Storage Lens provides call\-outs for metrics that are *outliers*, based on your recent 30\-day trend\. The outlier is calculated using a standard score, also known as a *z\-score*\. In this score, the current day’s metric is subtracted from the average of the last 30 days for that metric, and then divided by the standard deviation for that metric over the last 30 days\. The resulting score is usually between \-3 and \+3\. This number represents the number of standard deviations that the current day’s metric is from the mean\. 

    S3 Storage Lens considers metrics with a score >2 or <\-2 to be outliers because they are higher or lower than 95 percent of normally distributed data\. 
  + **Significant change call\-outs**

    The *significant change call\-out* applies to metrics that are expected to change less frequently\. Therefore it is set to a higher sensitivity than the outlier calculation, which is typically in the range of \+/\- 20 percent versus the prior day, week, or month\.

    **Addressing call\-outs in your storage usage and activity** – If you receive a significant change call\-out, it’s not necessarily a problem, and could be the result of an anticipated change in your storage\. For example, you might have recently added a large number of new objects, deleted a large number of objects, or made similar planned changes\. 

    If you see a significant change call\-out on your dashboard, take note of it and determine whether it can be explained by recent circumstances\. If not, use the S3 Storage Lens dashboard to drill down for more details to understand the specific Regions, buckets, or prefixes that are driving the fluctuation\.
+ **Reminders**

  *Reminders* provide insights into how Amazon S3 works\. They can help you learn more about ways to use S3 features to reduce storage costs or apply data protection best practices\.

### Metrics selection<a name="storage_lens_basics_metrics_selection"></a>

S3 Storage Lens offers two metrics selections that you can choose for your dashboard and export: *free metrics* and *advanced metrics and recommendations*\.
+ **Free metrics**

  S3 Storage Lens offers free metrics for all dashboards and configurations\. Free metrics contain metrics that are relevant to your storage usage\. This includes the number of buckets, the objects in your account, and what state they are in\. All free metrics are collected daily\. Data is available for queries for 14\-days\. For more information about what usage metrics are aggregated by S3 Storage Lens, see the [Metrics glossary](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage_lens_metrics_glossary.html)\.
+ **Advanced metrics and recommendations**

  S3 Storage Lens offers free metrics for all dashboards and configurations with the option to upgrade to * advanced metrics and recommendations*\. Additional charges apply\. For more information, see [Amazon S3 pricing](http://aws.amazon.com/s3/pricing/)\. Advanced metrics contain all the usage metrics that are included in free metrics\. This includes the number of buckets, the objects in your account, and what state they are in\. 

  This metrics selection also provides recommendations to help you optimize your storage\. Recommendations are placed contextually alongside relevant metrics in the dashboard\. 

  Advanced metrics and recommendations also include the following features:
  + **Activity metrics** \- Generate additional metrics aggregated by bucket, such as requests, bytes uploaded/downloaded, and errors\. Activity metrics data is relevant to your storage activity\. This includes the number of requests, scans, and errors with respect to the configuration scope and what state they are in\.
  + **Amazon CloudWatch publishing ** \- Publish S3 Storage Lens usage and activity metrics to CloudWatch to create a unified view of your operational health in CloudWatch [dashboards](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html)\. You can also use CloudWatch APIs and features like alarms and triggered actions, metric math, and anomaly detection to monitor and take action on S3 Storage Lens metrics\. For more information, see [Monitor S3 Storage Lens metrics in CloudWatch](storage_lens_view_metrics_cloudwatch.md)\.
  + **Prefix aggregation** \- Collect usage metrics at the prefix level\. Prefix level metrics are not published to CloudWatch\.

  All advanced metrics are collected daily\. Data is available for queries for 15 months\. For more information about the storage metrics aggregated by S3 Storage Lens, see [Amazon S3 Storage Lens metrics glossary](storage_lens_metrics_glossary.md)\.
**Note**  
Recommendations are available only when you use the S3 Storage Lens dashboard on the Amazon S3 console, and not via the AWS CLI and SDKs\.

### S3 Storage Lens and AWS Organizations<a name="storage_lens_basics_organizations"></a>

AWS Organizations is an AWS service that helps you aggregate all your AWS accounts under one organization hierarchy\. Amazon S3 Storage Lens works with AWS Organizations to provide a single view of object storage usage and activity across your Amazon S3 storage\.

For more information, see [Using Amazon S3 Storage Lens with AWS OrganizationsEnabling trusted access for S3 Storage Lens](storage_lens_with_organizations.md)\.
+ **Trusted access**

  Using your organization’s management account, you must enable *trusted access* for S3 Storage Lens to aggregate storage metrics and usage data for all member accounts in your organization\. You can then create dashboards or exports for your organization using your management account or by giving delegated administrator access to other accounts in your organization\. 

  You can disable trusted access for S3 Storage Lens at any time, which stops S3 Storage Lens from aggregating metrics for your organization\.
+ **Delegated administrator**

  You can create dashboards and metrics for S3 Storage Lens for your organization using your AWS Organizations management account, or by giving *delegated administrator* access to other accounts in your organization\. You can deregister delegated administrators at any time, which prevents S3 Storage Lens from collecting data on an organization level\.

For more information, see [Amazon S3 Storage Lens and AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/services-that-can-integrate-s3lens.html) in the *AWS Organizations User Guide*\.

#### Amazon S3 Storage Lens service\-linked roles<a name="storage_lens_basics_service_linked_role"></a>

Along with AWS Organizations trusted access, Amazon S3 Storage Lens uses AWS Identity and Access Management \(IAM\) service\-linked roles\. A service\-linked role is a unique type of IAM role that is linked directly to S3 Storage Lens\. Service\-linked roles are predefined by S3 Storage Lens and include all the permissions that it requires to collect daily storage usage and activity metrics from member accounts in your organization\. 

For more information, see [Using service\-linked roles for Amazon S3 Storage Lens](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-service-linked-roles.html)\.