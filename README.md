# Deploy React App to Amazon S3 using Github Actions by ikeri ebenezer.

*Tools*:
1. version control: github
2. CI: github actions 
3. s3 bucket
4. Auto-Testing tools: SonarQube

pipeline flow:

1. when code is pushed to main branch, sonarqube is triggered to scan code for vulnerabilitues, code smell, duplicated codes and outdated packages.
if the code doesnt meet the standard, then its been sent back as a FAILED push with reason or reasons the code was flagged and that can be seen in the github actions page.

SUGGESTION:  in a live scenario, i normally add slack pipeline incase there is a failed push so developers can get notified easily using slack notification.

2. if code passes all checks after sonar test, npm is installed and the build process begins.
3. code is then pushed to s3 bucket.

*Networking*
 1. the logic is to spin up a cloudfront (CDN) in which we use the s3 bucket we created for our app as the endpoint.
 2. then create a record in aws route53 using the cloudfront (CDN) we created as alias.

 this should work if all credentials are correct and bucket is created with the necessary policies.

