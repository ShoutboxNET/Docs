# Introduction 

Shoutbox is a simple to use API for developers. Using any language that allows call out to the Shoutbox API, a large volume of emails can be sent. 

Pick your environment below to start setting up and sending email: 

[CURL](./b3K6TMSsuooLnSQYOGVsRd)

[NodeJS](./BRcuD5CFnJ922YOKIATLHS)


# Prerequisites

- A [Cloudflare](https://cloudflare.com) account 
- One or more domains connected to that Cloudflare account

# New User: Set up domain 

- Go to: https://shoutbox.net
- Click on https://shoutbox.net/auth/sign-up

![Screenshot 2024-05-08 at 14.41.56.png](./assets/f32f30d08e194e05a9b7533b4bfe6f0e.png)

and Sign up with your information. 

- Create a team to work with

![Screenshot 2024-05-08 at 14.42.32.png](./assets/2d44fc000b5d4769836f19f56d579b44.png)

![Screenshot 2024-05-08 at 14.43.40.png](./assets/3fbc28eadc034f029fa9c3d5451184e9.png)

- Now gather the Cloudflare information for your account; 

![Screenshot 2024-05-08 at 14.44.25.png](./assets/b3a701e95abc4201961e74ef9e6608aa.png)

Please see the guide here how to complete this step: [Cloudflare retrieve your Account ID & Secret Token](./cloudflare-retrieve-account-id-and-secret.md)

- Click to add a Cloudflare Worker automatically

![Screenshot 2024-05-08 at 15.15.05.png](./assets/634dd826ca1e480fb300c27c669cb083.png)

- Now it is time to add the first Domain

*Note*: this domain must be in your Cloudlfare account, in the account you picked when setting up the account Id and secret; this cannot work if this was not set up properly. 

![Screenshot 2024-05-08 at 15.16.45.png](./assets/2e0cee6a192444c996c74b47996e9be8.png)

- Now you can automatically or manually set up your domain for use with Shoutbox

![Screenshot 2024-05-08 at 15.18.11.png](./assets/f60e0b0da37d46a3815a35b72f7027a1.png)

- To make sure everything goes more smoothly, it is recommend to clean up the Cloudflare DNS first, click here to see how; [Cleanup Cloudflare DNS](./cleanup-cloudflare-dns.md)

- Click to automatically add the information in Cloudflare

![Screenshot 2024-05-08 at 15.25.40.png](./assets/3077121bc7e044aab2887d0541aef835.png)

- Enter the domain, without www. in the box below to continue

![Screenshot 2024-05-08 at 15.26.08.png](./assets/259ee7288ec846ff8aff53da86a3ef0e.png)

- Continue to add the records 

![Screenshot 2024-05-08 at 15.27.32.png](./assets/ad163ba6491c4ce1a2ff64453d359f83.png)

- On the keys screen, add a key for your account to send email with

![Screenshot 2024-05-08 at 15.28.23.png](./assets/f5c6bce97fb642e4a7b5c3cc8420e0d6.png)

- Pick a name and a domain, or All domains

![Screenshot 2024-05-08 at 15.30.05.png](./assets/4ccf6d7ca35b4f03b4b8a17cdd4387a2.png)

- Click Create

![Screenshot 2024-05-08 at 15.30.45.png](./assets/9db3ce3817a348e487e3fbc9963b9da5.png)

- Copy the Key starting with key_ somewhere safe! 

This key cannot be copied again after this step but is required to send emails. You can always go back to API Keys and then Create another key. 

- Verify the domain by clicking Domains in the left menu

![Screenshot 2024-05-08 at 15.33.06.png](./assets/d0ec3eaf9e464a249444fce441c846e7.png)

- Check for the domain that was Not Started yet and click on it

![Screenshot 2024-05-08 at 15.33.33.png](./assets/6e140921555c4ca4985ceedb94b6d760.png)


![Screenshot 2024-05-08 at 15.34.46.png](./assets/a9659fe5539843c8942dc7ceea98163f.png)


- Click on the Verify DNS Records button


![Screenshot 2024-05-08 at 15.35.42.png](./assets/3e2e9dae4a6844a08dfc468dd8bee1ca.png)


![Screenshot 2024-05-08 at 15.35.55.png](./assets/50a4411e8cde4240b61ca28cf98f9673.png)


- This step can take 24 hours at max; when it has been completed, it shows active or an error

![Screenshot 2024-05-08 at 15.36.42.png](./assets/3d250f0b1f3e4447aff0ff7247f8387e.png)

## Congratulations! 

You are ready to send your first email. Return to the settings for your preferred development language / environment or try to send a test email: 


```
curl -X POST 'https://api.shoutbox.net/send' \
  -H 'Authorization: Bearer key_XXXXXXXXXXXX' \
  -H 'Content-Type: application/json' \
  -d $'{
    "from": "no-reply@YOURDOMAIN.com",
	  "name": "Tycho", 
    "to": "someone@somewhere.com",
    "subject": "Hello World",
    "html": "<strong>it works!</strong>"
  }'

```

Replace key_XXXXXXXXXXXX with the key you saved from the Shoutbox API keys and change the From Address with your own email/domain and the To address with some address you want to try to send to. *Make sure to use the domain you used and activated above*. 

