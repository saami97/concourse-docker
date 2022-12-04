<h3> If you are using gcloud shell to deploy docker and test this tutorial and if you run into the below error : <h1>

<h4> Error 1: unregistered redirect_uri ("https://8080-[redacted].cloudshell.dev/sky/callback"), here the link will be custom to the region to where your gcloud shell is hosted. </h4> 
  
<h4> Solution : </h4>

Now, as per https://concoursetutorial.com/index.html, You need to set the external url env variable inside the docker-compose.yml as below :

+ CONCOURSE_EXTERNAL_URL=http://{{my-server}}:8080 <br>
Here, your modification should be as follows : <br>
+ CONCOURSE_EXTERNAL_URL=https://8080-[redacted].cloudshell.dev/

Once this is done, you will no longer receive the unregistered redirect_uri error as the web ui will now be accurately redirected by google cloud shell to the redirect_uri instead of locally.

PS: [redacted] - indicates some sensitive values, which shall be unique to you. <br>


<h4> Error 2: image fetching failed </h4> 

Pulling busybox@sha256:f75f3d1a317fc82c793d567de94fc8df2bece37acd5f2bd364a0d91a0d1f3dab (attempt 3 of 3)...
Error response from daemon: error parsing  HTTP 408 response body : invalid character '<' looking for beginning of value: "<html><body>408 Request Time-out \nYour browser didn't send a complete request in time.\n</body></html>\n"

Failed to pull image busybox@sha256
image fetching failed****

<h4> Solution : </h4>
  
 Just run this command and then try setting and launching your pipeline again, it should work :
  
 <code> sudo ip link set dev eth0 mtu 1400 </code>
  
  <b> PS : This was just a learning that I wanted to share so that you might not end up in similar situation. </b> <br>
  


