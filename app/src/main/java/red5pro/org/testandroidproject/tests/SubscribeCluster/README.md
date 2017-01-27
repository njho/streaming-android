#Subscribing To a Cluster Server

#Publishing and subscribing with Red5 Pro clusters

###Example Code

- ***[SubscribeCluster.java](SubscribeCluster.java)***

##Configuration of the server.


```Java
HttpClient httpClient = new DefaultHttpClient();
HttpResponse response = httpClient.execute(new HttpGet("http://" + TestContent.GetPropertyString("host") + ":5080/cluster"));
StatusLine statusLine = response.getStatusLine();
if (statusLine.getStatusCode() == HttpStatus.SC_OK) {
	ByteArrayOutputStream out = new ByteArrayOutputStream();
	response.getEntity().writeTo(out);
	String responseString = out.toString();
	out.close();
	//the return is the host ip and rtmp port. we are only interested in the host ip.
	String[] bits = responseString.split(":");
	edgeIP = bits[0];
	Log.i("cluster", "round robin ip: " + edgeIP);
```
<sup>
[SubscribeCluster.java #48](SubscribeCluster.java#L48)
</sup>