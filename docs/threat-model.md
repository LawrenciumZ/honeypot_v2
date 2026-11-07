# Threat Model — Cowrie Honeypot v2

## 1. System Overview
I am deploying a decoy system where it will live on the cloud where it will have a public ip address, where it can be interacted with by online threat actors. This system logs all the cyber attacks done to it and ship it to a storage for manual review of attack patterns.

## 2. Assets
What I am protecting is my AWS account, billing, the EC2 instance, and the S3 logs. If Attackers escape the honeypot, then my AWS will be vulnerable, resulting in the shut down of the project. I do not expect this to happen but if it does then I will have to shut down the honeypot, reconfigure security and have my AWS account monitored for suspicious activities.


## 3. Threat Actors
The threat actors would primarily be bots automated, and maybe the occasional opportunist. Additionally, personal errors of the project where it results in the attackers escaping the honeypot, leaked AWS keys when committing to GitHub, public s3 buckets by mistake and forget to limit the instance running resulting in my billing increase.

## 4. Attacker Goals
What are these actors trying to achieve by attacking this specific type of target? The attacker would probably want to break into the machine to either find valuable data, such as email, usernames, other accounts, or to use the resources of the machine to do crypto mining or to commit crimes.

## 5. Out of Scope
I would not be defending against zero-day exploits, not doing real-time incident response or prevention, not guarantee to protect against more experienced threat actor, and not protecting real systems(This is an isolated decoy).

## 6. Success Criteria
The decision of whether this project worked or not is determined by achieving 200+ unique source ip addresses within 2Weeks of deploying, ensure that the amount of data shipped before numbers matches after numbers before processing and no compromise of the AWS account by keeping the AWS budget under the free tier.

## 7. Assumptions
The free tier AWS, no dedicated home network control, a single instance deployment, the project is not going to continue running after a specific time period.