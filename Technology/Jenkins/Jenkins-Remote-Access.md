# Jenkins Remote Access

## Request and Response

### Crumb Request

```bash
# cURL Crumb Request
curl -v -X GET http://jenkins-url:8080/crumbIssuer/api/json --user <username>:<password>
```

### Crumb Response

```json
# JSON Crumb Response
{
    "_class": "hudson.security.csrf.DefaultCrumbIssuer",
    "crumb": "0db38413bd7ec9e98974f5213f7ead8b",
    "crumbRequestField": "Jenkins-Crumb"
}
```

### Jenkins Request

```bash
# cURL Jenkins Request
curl -X POST http://jenkins-url:8080/job/<job-name>/build --user <username>:<password> -H 'Jenkins-Crumb: 0db38413bd7ec9e98974f5213f7ead8b'
```

## Reference
* [Remote Access API](https://www.jenkins.io/doc/book/using/remote-access-api/)
* [Jenkins: 403 No valid crumb was included in the request](https://stackoverflow.com/questions/44711696/jenkins-403-no-valid-crumb-was-included-in-the-request)