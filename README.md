# cloud-resume-challenge
Lukes Cloud Resume Challenge

URL to the challenge. https://forrestbrazeal.com/2020/04/23/the-cloud-resume-challenge/

The cloud resume challenge
Updated June 2020: Visit the official Cloud Resume Challenge homepage or join the Discord for rules, FAQ, and further updates.

We’re now at that point in quarantine where even the jobs people thought were safe are starting to dry up. Friends and family are telling me: “I’ve been thinking about changing careers and going into IT. Maybe doing something in the cloud, like you. Where should I start?”

So I’m making an offer right now, before God and the internet and everybody: send me your resume, and I will do my best to help you get a job in the cloud.

Yes, there are some conditions. The first two are easy.

The first condition is that I am not personally hiring anybody at the moment, and cannot force anyone else to hire you. But I have a relatively large network of connections, at least forty percent of whom seem to be tech recruiters, and I will make as much noise as possible to get their attention on you and your resume.

Second condition: the less prior experience you have, the bigger deal I will make out of you. For example, somebody who completes the Cloud Resume Challenge with no prior IT experience or related degree is going to get personal shoutouts on my Twitter and LinkedIn, personalized code reviews, direct intros to hiring managers, etc.

If you are fortunate enough to have a job in the cloud already, please share this post with #CloudResumeChallenge – let’s get it in the hands of the people who need it.

OK, now the important conditions.

Your resume needs to have the AWS Cloud Practitioner certification on it. This is an introductory certification that orients you on the industry-leading AWS cloud – if you have a more advanced AWS cert, that’s fine but not expected. No cheating: include the validation code on the resume. You can sit this exam online for $100 USD. If that cost is a dealbreaker for you, let me know and I’ll see if I can help. Here are some exam prep resources.
Your resume needs to be written in HTML. Not a Word doc, not a PDF. Here is an example of what I mean.
Your resume needs to be styled with CSS. No worries if you’re not a designer – neither am I. It doesn’t have to be fancy. But we need to see something other than raw HTML when we open the webpage.
Your HTML resume should be deployed online as an Amazon S3 static website. Services like Netlify and GitHub Pages are great and I would normally recommend them for personal static site deployments, but they make things a little too abstract for our purposes here. Use S3.
The S3 website URL should use HTTPS for security. You will need to use Amazon CloudFront to help with this.
Point a custom DNS domain name to the CloudFront distribution, so your resume can be accessed at something like my-c00l-resume-website.com. You can use Amazon Route 53 or any other DNS provider for this. A domain name usually costs about ten bucks to register.
Your resume webpage should include a visitor counter that displays how many people have accessed the site. You will need to write a bit of Javascript to make this happen. Here is a helpful tutorial to get you started in the right direction.
The visitor counter will need to retrieve and update its count in a database somewhere. I suggest you use Amazon’s DynamoDB for this. (Use on-demand pricing for the database and you’ll pay essentially nothing, unless you store or retrieve much more data than this project requires.) Here is a great free course on DynamoDB.
Do not communicate directly with DynamoDB from your Javascript code. Instead, you will need to create an API that accepts requests from your web app and communicates with the database. I suggest using AWS’s API Gateway and Lambda services for this. They will be free or close to free for what we are doing. You will need to write a bit of code in the Lambda function; you could use more Javascript, but it would be better for our purposes to explore Python – a common language used in back-end programs and scripts – and its boto3 library for AWS. Here is a good, free Python tutorial.
You should also include some tests for your Python code. Here are some resources on writing good Python tests.
You should not be configuring your API resources – the DynamoDB table, the API Gateway, the Lambda function – manually, by clicking around in the AWS console. Instead, define them in an AWS Serverless Application Model (SAM) template and deploy them using the AWS SAM CLI. This is called “infrastructure as code” or IaC. It saves you time in the long run.
You do not want to be updating either your back-end API or your front-end website by making calls from your laptop, though. You want them to update automatically whenever you make a change to the code. (This is called continuous integration and deployment, or CI/CD.) Create a private GitHub repository for your backend code. Set up GitHub Actions such that when you push an update to your Serverless Application Model template or Python code, your Python tests get run. If the tests pass, the SAM application should get packaged and deployed to AWS.
Create a second private GitHub repository for your website code. Create GitHub Actions such that when you push new website code, the S3 bucket automatically gets updated. (You may need to invalidate your CloudFront cache in the code as well.) Important note: DO NOT commit AWS credentials to source control! Bad hats will find them and use them against you!
Finally, in the text of your resume, you should link a short blog post describing some things you learned while working on this project. Dev.to is a great place to publish if you don’t have your own blog.
And that’s it. When you have done all this, add my GitHub username (@forrestbrazeal) as a collaborator on your repositories. If you have indeed met the conditions listed above, I will give you a personalized code review, then make as much noise about you as I can to anybody who will listen (including sharing your awesome blog post!).

Now, before you say it … obviously, I have no right to tell you to do any of this stuff. You will have to open a large number of browser tabs to figure out the steps. It will take you quite a few long evenings at the kitchen table. You might reasonably conclude that none of what I just suggested is worth the dubious reward of having a random industry professional share your resume with a few thousand people.

But if you give this project a try and realize that you hate it, or you’re just not interested, you’ll have learned a valuable lesson about whether or not you really want a career in the cloud – because these are the types of problems that real cloud engineers and developers really work on.

And I believe that if you can, in good faith, complete the Cloud Resume Challenge, you will already have more useful skills than a lot of people who graduate from university computer science programs. Specifically: you will understand something about full-stack software development, version control, infrastructure as code, automation, continuous integration and delivery, cloud services and “serverless”, application security, and networking. And you’ll have learned by doing, because I didn’t give you enough instructions to figure any of this out without going down some late-night rabbit holes. Most importantly, you will have demonstrated the number-one skill in a cloud engineer’s toolbox: the ability to learn fast and google well.

Those are skills you can take to a job interview. And I’ll do my best to help you get one.

Good luck!
