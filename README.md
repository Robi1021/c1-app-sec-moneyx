# c1-app-sec-moneyx
Sample Java Spring application running in a container, for Cloud One Application Security demos
  
Download with
```
git clone https://github.com/Robi1021/c1-app-sec-moneyx.git
```

## Detailed Description
This is a sample, vulnerable-on-purpose, Java Spring application that can be used to demo Cloud One Application Security.

MoneyX was created by the fine folks over at nVisium.
See:  https://github.com/nVisium/MoneyX

 ## Pre-Requisites for Usage

* Docker
* A Cloud One Application Security account
* MOADSD-NG, Jenkins and Kubernetes


### Start the container locally 

1. Download and run the container:
```
docker run --rm -d -p 8080:8080 --name moneyx-app-protect -e TREND_AP_KEY=<KEY> -e TREND_AP_SECRET=<SECRET> howiehowerton/moneyx-app-protect
```

2. Access the app on port 8080

### Deploy the container in your Cluster 

1. Download the git repo using "git clone ..."
2. Edit the k8.app.yml to set your Trend Micro App Sec key & Secret:
```
env:
        - name: TREND_AP_KEY
          value: <YOUR_APP_SEC_KEY_HERE>
        - name: TREND_AP_SECRET
          value: <YOUR_APP_SEC_SECRET_HERE>
```
3. Run
```
kubectl apply -f k8-app.yml
```

2. Access the app on port 8080

### Exploit
  
1. Follow the instructions in [exploits.md](exploits.md) to exploit the application.  Demonstrate that the exploits work against the vulnerable app.

2. Switch Cloud One Application Security rules from "Report" to "Mitigate".

3. Follow the instructions in [exploits.md](exploits.md) again. Demonstrate that the exploits **no longer** work.

## Updates (20211012)
The C1AS agent in this container (image) now uses the new, emailbased, authentication mechanism in CloudOne.    
This allows to use regional CloudOne instances e.g in Europe 

 
 
