# User-Authentication-Subscription

## Getting Started

### Prerequisites

Install the latest version of npm
  ```sh
  npm install npm@latest -g
  ```
Create a MongoDB Database 
* Link - https://www.mongodb.com/

Create a SendGrid API Key
* Link - https://sendgrid.com/

### Installation

1. Clone the repo
   ```sh
   git clone 
   ```
2. Install NPM packages
   ```sh
   npm install
   ```
3. Update your Databse url in `.env`

   ```JS
   DATABASE='ENTER YOUR DB URL'
   ```
3. Update your SendGrid API key in `.env`

   ```JS
   SENDGRID_API_KEY='ENTER YOUR SENDGRID API KEY'
   ```
4. Add your SendGrid email in `emailsubscriber.js`

    ```JS
      exports.sendGridEmailResetPassword = (email, subject, message, code) => {
        sgMail.setApiKey(process.env.SENDGRID_API_KEY);
        const msg = {
          to: email,
          from: "example@example.com", // Please use your Sendgrid email
          subject: subject,
          text: `${message}\n\n This is your verification code: ${code}`,
        };
        sgMail
          .send(msg)
          .then(() => {
            console.log("Email sent");
          })
          .catch((error) => {
            console.error(error);
          });
    };
       ```
3. Start the server
   ```sh
   npm start
   ```

