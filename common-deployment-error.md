If you are using gcloud shell to test this tutorial and if you run into the below error : <br>

unregistered redirect_uri ("https://8080-[redacted].cloudshell.dev/sky/callback"), here the link will be custom to the region to where your gcloud shell is hosted. <br>

Now, as per https://concoursetutorial.com/index.html, You need to set the external url env variable inside the docker-compose.yml as below :

+ CONCOURSE_EXTERNAL_URL=http://{{my-server}}:8080 <br>
Here, your modification should be as follows : <br>
+ CONCOURSE_EXTERNAL_URL=https://8080-[redacted].cloudshell.dev/

Once this is done, you will no longer receive the unregistered redirect_uri error as the web ui will now be accurately redirected by google cloud shell to the redirect_uri instead of locally.

PS: [redacted] - indicates some sensitive values, which shall be unique to you. <br>
This was just a learning that I wanted to share so that you might not end up in similar situation.
