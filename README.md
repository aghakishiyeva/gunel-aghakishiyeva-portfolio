# Building and Hosting Personal Portfolio using Zola and Amazon S3

This portfolio website is built using <b>Zola</b> and hosted on <b>Amazon S3</b>.

![image](https://github.com/aghakishiyeva/gunel-aghakishiyeva-portfolio/assets/78721466/8a75c96c-110e-4b48-b778-0464fbd2b168)

[Zola](https://www.getzola.org/) is a static site generator written in Rust programming language, providing fast rendering times and flexibility for website development.

## Installation and Setup
As a first step, you need to do installation and setup locally. For this purpose, please refer to the [Resume Theme on Zola Website](https://www.getzola.org/themes/resume/).

## Deployment Steps

1. After building and hosting your website locally using `zola serve`, run the following command to generate the production files:

    ```bash
    zola build
    ```

2. This will create a `public` directory containing your website files.

3. Create an S3 bucket using one of the following methods:
    - AWS Management Console
    - AWS CLI
    - AWS SDK

4. Upload the files from the `public` directory to your Amazon S3 bucket.

5. Add the following bucket policy (replace `gunelsportfolio` with your bucket name):

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "AddPerm",
                "Effect": "Allow",
                "Principal": "*",
                "Action": "s3:GetObject",
                "Resource": "arn:aws:s3:::gunelsportfolio/*"
            }
        ]
    }
    ```

6. Enable Static website hosting for your bucket (via <b>Properties</b> tab).
   
7. Uncheck everything under "Block public access" in bucket settings (via <b>Permissions</b> tab).

8. Go to bucket <b>Properties</b> again and scroll down to "Static website hosting". You'll find a link similar to `http://gunelsportfolio.s3-website-us-east-1.amazonaws.com`.

9. Your website is now hosted and accessible via the provided link.

