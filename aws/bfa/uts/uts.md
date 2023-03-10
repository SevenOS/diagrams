# uts timeline

This documentation was created so that we can demonstrate the flow of **uts** jobs

## uts

Uts stands for User Trait Service and is used for UP program

![uts diagram](https://github.com/SevenOS/diagrams/blob/main/aws/bfa/uts/uts.jpg)

### Production

| Dag                           | Task                                     |    Source db         |    Sink Dag                           | Dag Update Hour (utc) | Sink Dag Update Hour (utc) |
| :----:                        |    :----:                                |     :----:           |     :----:                            | :----: | :----: |
| data.ocean.subscriptions      | subscriptions_lifecycle                  | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.lifecycle                | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_cycle                      | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.lifecycle                | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription_item.         | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription               | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_personalized_product_price | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_personalized_product       | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.ipsy               | ipsy_physical_address                    | db-ro.prod.ipsy.com.ipsy                                                                                         | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription               | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.physical_address         | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.ipsy               | ipsy_physical_address                    | db-ro.prod.ipsy.com.ipsy                                                                                         | services.uts.physical_address         | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription               | subscriptions-prod-pg12.cluster-c6xs3p3jkysv.us-east-1.rds.amazonaws.com.subscriptions   | services.uts.refreshment_membership   | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.ipsy               | ipsy_physical_address                    | db-ro.prod.ipsy.com.ipsy                                                                                         | services.uts.refreshment_membership   | 00:00,10:00AM | 02:00,12:00AM |

### Staging

| Dag                           | Task                                     |    Source db         |    Sink Dag                           | Dag Update Hour (utc) | Sink Dag Update Hour (utc) |
| :----:                        |    :----:                                |     :----:           |     :----:                            | :----: | :----: |
| data.ocean.subscriptions      | subscriptions_lifecycle                  |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.lifecycle                | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_cycle                      |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.lifecycle                | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription_item.         |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription               |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_personalized_product_price |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_personalized_product       |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.ipsy               | ipsy_physical_address                    |  db-ro.staging.ipsy.com.ipsy                           | services.uts.membership               | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription               |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.physical_address         | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.ipsy               | ipsy_physical_address                    |  db-ro.staging.ipsy.com.ipsy                           | services.uts.physical_address         | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.subscriptions      | subscriptions_subscription               |  db-subscriptions-pg12.staging.ipsy.com.subscriptions  | services.uts.refreshment_membership   | 00:00,10:00AM | 02:00,12:00AM |
| data.ocean.ipsy               | ipsy_physical_address                    |  db-ro.staging.ipsy.com.ipsy                           | services.uts.refreshment_membership   | 00:00,10:00AM | 02:00,12:00AM |

Environments:
- [Staging](https://0e5dd8e5-ae22-4f7c-9edb-1a22f1ab84ee.c27.us-east-1.airflow.amazonaws.com/home)
- [Production](https://74b87fd5-075d-478a-9678-a5223fa7de70.c1.us-east-1.airflow.amazonaws.com/home)
