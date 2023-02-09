# uas timeline

This documentation was created so that we can demonstrate the flow of **uas** jobs

## uas

Uas stands for user attributes service, and is used to profile the user through the Iterable

![uts diagram](https://github.com/SevenOS/diagrams/blob/main/aws/bfa/uas/uas.jpg)

### Production

| Dag                           | Task                                     |    Source db         |    Sink Dag                           | Dag Update Hour (utc) | Sink Dag Update Hour (utc) |
| :----:                        |    :----:                                |     :----:           |     :----:                            | :----: | :----: |
|data.ocean.subscriptions|subscriptions_cycle|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription_item|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_personalized_product_price|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_personalized_product|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription_audit|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.quiz|quiz_main_quiz_metadata|quiz-db.prod.ipsy.com.quiz|services.uas.new_quiz|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_payment_method|db-ro.prod.ipsy.com.ipsy|services.uas.payment_data|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_physical_address|db-ro.prod.ipsy.com.ipsy|services.uas.payment_data|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.payments|payments_payment_method_additional_info|db-payments.prod.ipsy.com.payments|services.uas.payment_data_international|00:00AM,10:00AM|02:00AM,12:00AM|
|dynamo_db|addresses_db_bfa_main|dynamo_db|services.uas.payment_data_international|-|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.physical_address|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_physical_address|db-ro.prod.ipsy.com.ipsy|services.uas.physical_address|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.physical_address_international|00:00AM,10:00AM|02:00AM,12:00AM|
|dynamo_db|addresses_db_bfa_main|dynamo_db|services.uas.physical_address_international|-|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription_item|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_physical_address|db-ro.prod.ipsy.com.ipsy|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_cycle|db-subscriptions-pg12.prod.ipsy.com.subscriptions|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.catalog1p|catalog1p_items|catalog-1p-db-main-writer.prod.bfa.bfainfra.com.catalog1p|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.catalog1p|catalog1p_products|catalog-1p-db-main-writer.prod.bfa.bfainfra.com.catalog1p|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.catalog1p|catalog1p_brands|catalog-1p-db-main-writer.prod.bfa.bfainfra.com.catalog1p|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|scores||S3|services.uas.propensity_annual_upgrade_scores|-|10:50AM|
|scores||S3|services.uas. propensity_gbp_upgrade_scores|-|10:40AM|
|crm_analytics||S3|services.uas.iterable_cluster|-|8:00AM|

### Staging

| Dag                           | Task                                     |    Source db         |    Sink Dag                           | Dag Update Hour (utc) | Sink Dag Update Hour (utc) |
| :----:                        |    :----:                                |     :----:           |     :----:                            | :----: | :----: |
|data.ocean.subscriptions|subscriptions_cycle|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription_item|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_personalized_product_price|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_personalized_product|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription_audit|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.quiz|quiz_main_quiz_metadata|quiz-db.staging.ipsy.com.quiz|services.uas.new_quiz|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_payment_method|db-ro.staging.ipsy.com.ipsy|services.uas.payment_data|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_physical_address|db-ro.staging.ipsy.com.ipsy|services.uas.payment_data|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.payments|payments_payment_method_additional_info|db-payments.staging.ipsy.com.payments|services.uas.payment_data_international|00:00AM,10:00AM|02:00AM,12:00AM|
|dynamo_db|addresses_db_bfa_main|dynamo_db|services.uas.payment_data_international|-|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.physical_address|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_physical_address|db-ro.staging.ipsy.com.ipsy|services.uas.physical_address|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.physical_address_international|00:00AM,10:00AM|02:00AM,12:00AM|
|dynamo_db|addresses_db_bfa_main|dynamo_db|services.uas.physical_address_international|-|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_subscription_item|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.ipsy|ipsy_physical_address|db-ro.staging.ipsy.com.ipsy|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.subscriptions|subscriptions_cycle|db-subscriptions-pg12.staging.ipsy.com.subscriptions|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.catalog1p|catalog1p_items|catalog-1p-db-main-writer.staging.bfa.bfainfra.com.catalog1p|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.catalog1p|catalog1p_products|catalog-1p-db-main-writer.staging.bfa.bfainfra.com.catalog1p|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|data.ocean.catalog1p|catalog1p_brands|catalog-1p-db-main-writer.staging.bfa.bfainfra.com.catalog1p|services.uas.refreshment_membership|00:00AM,10:00AM|02:00AM,12:00AM|
|scores||S3|services.uas.propensity_annual_upgrade_scores|-|10:50AM|
|scores||S3|services.uas. propensity_gbp_upgrade_scores|-|10:40AM|
|crm_analytics||S3|services.uas.iterable_cluster|-|8:00AM|


Environments:
- [Staging](https://0e5dd8e5-ae22-4f7c-9edb-1a22f1ab84ee.c27.us-east-1.airflow.amazonaws.com/home)
- [Production](https://74b87fd5-075d-478a-9678-a5223fa7de70.c1.us-east-1.airflow.amazonaws.com/home)
