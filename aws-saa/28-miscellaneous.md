## amazon pinpoint
1. enables you to engage with customers through messaging channels.
2. Create **journeys** to customize engagements.
3. intended for
   1. marketing teams
   2. business users
4. **exam indicators:** marketing campaigns, user engagements, sending emails to targeted audiences.
5. sample archi - ![pinpoint-sample](./images/27/pintpoint-sample.png)

## aws amplify
1. offers tools and libraries for frontend web and mobile devsto build full stack apps.
2. offers
   1. frontend libs
   2. ui comps
   3. backend building
   4. easy authn and authz
3. like firebase
4. offers simplified development for less experienced teams.
5. supports ssr frameworks: next, nuxt, astro, etc
6. supports spa frameworks: vue, react, angular etc
7. supports ssg: gatsby, hugo, eleventsy, jekyll, vuepress, etc
8. **consider for anything managed SSR, easy mobile dev, running full stack app.**

## aws device farm
1. app testing svc for testing ang interacting with android, ios and web apps.
2. usable on actual phones and tablets.
3. 2 primary testing methods
   1. automated - upload scripts or built in test
   2. remote access - swipe, gesture, interact with devices realtime in browser.
4. **exam indicators:** anything that requires app testing on mobile dvcs in aws. Especially needing mobile or tablet for automated testing.

## aws wavelength
1. build apps that require edge computing infra to deliver low latency to mobile dvcs and end users.
2. leverages 5g.
3. specific 5g networking reqs.
4. increase resiliency of edge apps.

## amazon appflow
1. fully managed integration svc for securely exchanging data between saas and aws.
2. like, salesforce to s3.
3. zendesk, servicenow
4. destinations
   1. s3
   2. redshift
   3. etc

## amazon simple email service (SES)
1. aws svc for email platform to send and receive email.
2. allow own email addr and domains.
3. large scale email soln
4. DKIM support
5. send email from anything that can amke API call to SES.
6. provide stats about bounces, complaints, successful deliveries.
7. hard to setup?