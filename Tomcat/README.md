The Dockerfile helps you to configure your own Tomcat server from scratch. 
Couple of Pointers,
1. You need to update the user and password and give the required permissions in tomcat-users.xml file.
eg,
<user username="xyz", password="something" roles="built in role">

2. Tomcat doesn't allow access to it's servers from any other machine. We need to comment out the configuration
file in webapps/manager/META-INF/context.xml
<!--
<CookieProcessor className="org.apache.tomcat.util.http.Rfc6265CookieProcessor"
                   sameSiteCookies="strict" />
  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->

3. You can add the mount and add your own configuration files which can take care of above 2 scenarios.
