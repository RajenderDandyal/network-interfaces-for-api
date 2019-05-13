# network-interfaces-for-api
explanation for network interfaces and how we work with them while deploying app

# Network Interface/host
* Every machine have access to multiple interfaces
* Public-interface: by default available to us as ipv4 address when we create new instance. All other computers on public network(web) can access this host.
* Private-itnerface: Only computers on this private network can access to our host(for private). Not available for general web(public).
* 0.0.0.0: If we run our application on this host, then its available to every network interface available to our machine.
* localhost/127.0.0.1/loopback: available with every machine. to work with local apps.

## network-interface and our app
* When we run our app ex app.listen(8081,()=>{}), this means by default our app is available on every network mentioned above on port 8081.
* To run app on public/private/0.0.0.0 or localhost only(any one). Use process.args[2], while starting app with command like, node app.js 135.25.6.356, the third argument can be accessed via process.args[2],
ex:
let hostname = process.args[2];

app.listen(8081, hostname, ()=>{})

Now our app will be available on the host that we pass as 3rd argument, on start script, but not available to other network/host

say our instance ipv4/public ip is 135.2.6.123, and we want to run our app only on public interface, then run 

node app.js 135.2.6.123

if we run node app.js 0.0.0.0, or node app.js null,... then our app will be available on every interfaces available to machine--public,private,local --- thats the default behaviour that we get.
