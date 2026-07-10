---
title: "Blog 3"
date: 2026-07-10
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# A Very Cool Feature of AWS Lake Formation

Recently while researching Data Lakes on AWS, I came across a very interesting article from AWS about Lake Formation that I wanted to share with everyone.

Looking at the diagram, we can see:

* **EMR Spark** reads/writes data directly from/to S3 via IAM Permissions.
* **Lake Formation** manages permissions on database tables in the Glue Catalog.
* **Athena** queries data based on Lake Formation permissions.

This leads to a very common scenario:
You can query data using Athena normally, but when using Spark to read files directly in S3, you get an Access Denied error.

This happens because Athena and Spark use two different authorization mechanisms:
* Athena → Lake Formation
* Spark reading S3 files → IAM / S3 Policy

### The New AWS Solution

AWS recently introduced a new feature to solve this issue. Lake Formation can now grant temporary credentials to Spark for direct S3 access based on permissions configured in Lake Formation, via the API:
`GetTemporaryDataLocationCredentials()`

### Data Access Flow Diagram

![AWS Lake Formation S3 Access Architecture](/images/3-BlogsPosted/blog3-lakeformation-s3.png)

### Key Benefits of This Feature:

* **Reduced overhead of managing permissions in multiple places:** Unifies the authorization mechanism under a single management plane.
* **Fewer Access Denied errors due to misconfiguration:** Syncs access permissions between direct S3 file accesses and queries.
* **More convenient for Spark, ETL, and Machine Learning workloads:** Integrates big data pipeline engines more seamlessly.
* **Easier monitoring of data access via CloudTrail:** Audits access logs centrally for audit compliance.

### Some Considerations:

* The S3 Location must be registered with Lake Formation.
* Requires Amazon EMR 6.15.0+ or 7.1.0+.
* Apache Iceberg is not yet supported.
* Cross-Region access is not yet supported.

I find this a very useful improvement for Data Lake architectures on AWS, especially in environments utilizing both Athena and EMR Spark.

---

**Article Link:** <https://www.facebook.com/groups/awsstudygroupfcj/posts/2191055074992786/?notif_id=1782041739635661&notif_t=group_post_approved&ref=notif>

**Reference Guide:** <https://aws.amazon.com/vi/blogs/big-data/access-amazon-s3-data-files-directly-using-aws-lake-formation-permissions/?fbclid=IwY2xjawSu8LtleHRuA2FlbQIxMABicmlkETFDd1poRWJtcTNFMEw4bmJKc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHlfRqurG5Rir4FRt1bIoRDfriCsPR9wuIOYoTnZdypKxZVcIBVgtWsk4A8C9_aem_pW5Px8mN6tGNyQOA7DJaXA>