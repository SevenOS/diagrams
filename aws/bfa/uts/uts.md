# uts & uas timeline

This documentation was created so that we can demonstrate the flow of **uts** and **uas** jobs

## uts



![uts diagram](https://github.com/SevenOS/diagrams/blob/main/aws/bfa/uts/uts.drawio.jpg)

| Dag                           | Task                                     |    Source db         |    Sink Dag                           | Dag Update Hour (utc) | Sink Dag Update Hour (utc) |
| :----:                        |    :----:                                |     :----:           |     :----:                            | :----: | :----: |
| data.ocean.subscriptions      | subscriptions_lifecycle                  | subscriptions-pg12   | services.uts.lifecycle                | 10AM | 07AM |
| data.ocean.subscriptions      | subscriptions_cycle                      | subscriptions-pg12   | services.uts.lifecycle                | 10AM | 07AM |
| data.ocean.subscriptions      | subscriptions_subscription_item.         | subscriptions-pg12   | services.uts.membership               | 10AM | 06AM |
| data.ocean.subscriptions      | subscriptions_subscription               | subscriptions-pg12   | services.uts.membership               | 10AM | 06AM |
| data.ocean.subscriptions      | subscriptions_personalized_product_price | subscriptions-pg12   | services.uts.membership               | 10AM | 06AM |
| data.ocean.subscriptions      | subscriptions_personalized_product       | subscriptions-pg12   | services.uts.membership               | 10AM | 06AM |
| data.ocean.ipsy               | ipsy_physical_address                    | ipsy-db              | services.uts.membership               | 10AM | 06AM |
| data.ocean.subscriptions      | subscriptions_subscription               | subscriptions-pg12   | services.uts.physical_address         | 10AM | 07AM |
| data.ocean.ipsy               | ipsy_physical_address                    | ipsy-db              | services.uts.physical_address         | 10AM | 07AM |
| data.ocean.subscriptions      | subscriptions_subscription               | subscriptions-pg12   | services.uts.refreshment_membership   | 10AM | 06:30AM |
| data.ocean.ipsy               | ipsy_physical_address                    | ipsy-db              | services.uts.refreshment_membership   | 10AM | 06:30AM |



## uas


![uts diagram](https://github.com/SevenOS/diagrams/blob/main/aws/bfa/uts/uas.drawio.jpg)

Environments:
- [Staging](https://0e5dd8e5-ae22-4f7c-9edb-1a22f1ab84ee.c27.us-east-1.airflow.amazonaws.com/home)
- [Production](https://74b87fd5-075d-478a-9678-a5223fa7de70.c1.us-east-1.airflow.amazonaws.com/home)
