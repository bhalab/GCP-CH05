# GCP-CH05


Hello every one.
The Challenge (#GoogleClout Set 5(4/10))
https://www.cloudskillsboost.google/quests/218

---
I solve this challenge after I reviewed this links from <a href='https://www.googlecloudcommunity.com/gc/Learning-Forums/New-Challenge-Show-off-your-cloud-skills-by-completing-the/m-p/448619#M10339'> @You-Jun </a> 
[1] https://cloud.google.com/blog/products/spanner/change-streams-for-cloud-spanner-now-generally-availa...
[2] https://www.youtube.com/watch?v=fwyLNP3RtCs&t=318s&ab_channel=GoogleCloudTech
, also I followed the steps from <a href='https://www.googlecloudcommunity.com/gc/Learning-Forums/New-Challenge-Show-off-your-cloud-skills-by-completing-the/m-p/448619#M10339'> @fuchengyen </a>  that helps me shrink more time

First step3:
// I run this line in Cloud Shell Editor
gcloud config set compute/region [dynamically selected lab startup]
Then I opened Jobs dataflow and create the job streamjob . [1]
[1] https://cloud.google.com/blog/products/spanner/change-streams-for-cloud-spanner-now-generally-availa...

Second step 1:
//run the following in Compute Shell

//creating the spanner instance

gcloud spanner instances create [Cloud Spanner Meta Instance] \
--config=regional-[dynamically selected lab startup] \
--description="Spanner Meta" \
--nodes=1
//create the spanner databases

gcloud spanner databases create [Cloud Spanner Meta Database] --instance=[Cloud Spanner Meta Instance]

//creating the dataset in BQ

bq --location=[dynamically selected lab startup] mk [BigQuery Dataset]

Third step 2:
Create the Cloud Spanner change stream named ordersstream on the orders table.

CREATE CHANGE STREAM ordersstream FOR orders;

return to the jobs and see if the dataflow start running .
Forth step 4:
if dataflow start running then I open Cloud Spanner Query console and insert data into orders table.


INSERT INTO orders(
OrderID,
CustomerID,
OrderDate,
Price,
ProductID)
VALUES(123, -- type: INT64
456, -- type: INT64
'2022-04-26', -- type: DATE
99, -- type: INT64
789 -- type: INT64
);

when you open BQ you will find the rows in the table.

Good luck.
=========
