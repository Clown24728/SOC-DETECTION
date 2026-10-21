# Splunk Universal Forwarder Installation & Configuration
← [Back to project overview](README.md)    
# installing the forwarder   
For Splunk Enterprise to receive anything from the Windows VM, an agent needed to be running on that VM whose job is to read local log data and ship it off to the indexer. That agent is the Splunk Universal Forwarder. It was downloaded and installed inside the Windows 11 VM, and during setup, On-Premises Splunk Enterprise Instance was selected as the deployment type, since this lab does not use Splunk Cloud.     


<div align="Center">
<img width="4032" height="3024" alt="IMG_5793" src="https://github.com/user-attachments/assets/aa9313a9-3940-4b07-bf81-fe28afc39bf8" />
<p><em>Figure 7.downloading the Splunk Universal Forwarder</em></p>
</div>  


<div align="Center">  
<img width="800" height="600" alt="Screenshot 2026-10-13 190440" src="https://github.com/user-attachments/assets/77657fd5-1286-43a1-bebd-b3c3c1903a6b" />  
<p><em>Figure 8. Splunk Universal Forwarder Installation in progress</em></p>  
</div>  

# Configuring Splunk Forwarding   
Installing the Forwarder alone does not create a working pipeline, both ends need to agree on where data is going and where it is expected to arrive. On the Windows VM side, the Universal Forwarder was configured with the host machine's IP address (192.168.18.3) and port 9997 as its receiving destination. On the Splunk Enterprise side, the platform was configured under Forwarding and Receiving to listen for incoming forwarder connections on that same port. Both sides of this configuration have to match for data to flow, which is why they are documented together here.    


<div align="Center">
<img width="4032" height="3024" alt="IMG_5794" src="https://github.com/user-attachments/assets/7cd94867-0721-4102-b600-502caedd189f" />  
<p><em>Figure 9. Universal Forwarder Configuration with the receiving server address and port</em></p>  
</div>    


<div align="Center">
<img width="1440" height="900" alt="Screenshot 2026-10-13 at 7 37 56 pm" src="https://github.com/user-attachments/assets/f1cfa97c-0af7-4a6d-9f03-6a07abb7b00f" />    
<p><em>Figure 10. Splunk Enterprise configured to receive data on port 9997.</em></p>    
</div>    


<div align="Center">  
<img width="1440" height="900" alt="Screenshot 2026-10-13 at 7 39 20 pm" src="https://github.com/user-attachments/assets/5ab12655-f4dc-49fe-884c-e428f54fee3a" />  
<p><em>Figure 11 Receiving data from the endpoint telemetry </em></p>    
</div>     


# Confirming the Splunk Forwarder Connection  
Configuration alone does not guarantee a working connection, so this was verified directly rather than assumed. From the Windows VM command line, the forward server status was checked, which confirmed an active forward to 192.168.18.3:9997. This was then crosschecked from the Splunk Enterprise side by searching Splunk's internal logs (index=_internal sourcetype=splunkd), which returned thousands of events, this proof that the Forwarder was not only configured correctly, but actively exchanging data with Splunk Enterprise in real time.    


<div align="Center">
<img width="800" height="600" alt="Screenshot 2026-10-13 202616" src="https://github.com/user-attachments/assets/05d5ba1f-b63a-45f0-8919-804a9376b097" />  
<p><em>Figure 12  Command-line confirmation of an active forward from the Windows VM.</em></p>  
</div>    


<div align="Center">
<img width="1440" height="900" alt="Screenshot 2026-10-13 at 10 58 21 pm" src="https://github.com/user-attachments/assets/ee9c864e-2ad7-4c51-aa87-b85d23a6c796" />   
<p><em>Figure13 Splunk Enterprise search confirming forwarder activity (`index=_internal sourcetype=splunkd`).</em></p>   
</div>    


