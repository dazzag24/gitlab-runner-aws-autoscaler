## gitlab runner aws autoscaler with ec2 spot instance

![alt text](https://i.imgur.com/1byPnQS.jpg)

#### EC2 Spot Instance Price as a runner/agent
![alt text](https://i.imgur.com/o6OVzk9.png)


#### iam-policy
ec2 gitlat runner manager only can delete EC2 with ec2 profile `gitlab-runner-agent`
 ```
 {
            "Action": [
                "ec2:TerminateInstances"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:ec2::<AWS_ACCOUNT_ID>:instance/*",
            "Condition": {
                "StringEquals": {
                    "ec2:InstanceProfile": "arn:aws:iam::<AWS_ACCOUNT_ID>:instance-profile/gitlab-runner-agent"
                }
            }
        },
```        

#### One Gitlab runner use by multiple project
##### Disable lock runner in primary project
![alt text](https://i.imgur.com/uSfcfKk.png)
##### in other project enable runner in aws
![alt text](https://i.imgur.com/PO17CTY.png)



#### MachineOptions for AWS
https://docs.docker.com/machine/drivers/aws/

#### MachineOption for GCE
https://docs.docker.com/machine/drivers/gce/
##### example for gce with preemptible
https://verkoyen.eu/blog/2018/08/scaling-gitlab-runner-on-google-cloud-platform


        
