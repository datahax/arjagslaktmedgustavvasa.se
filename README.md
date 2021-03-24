# Är jag släkt med Gustav Vasa?

Har du någonsin undrad om du är släkt med någon cool kändis? Kanske en artist?
Eller, en **kung**?! Well, fundera inte längre. Här har du källkoden till
[ärjagsläktmedgustavvasa.se](https://ärjagsläktmedgustavvasa.se) där du enkelt
kan se om just *du* är släkt med Gustav Vasa.

[Original README.md](README_REACT.md)

## Deployment

GCP + managed Cloud Run, something like this:

```sh
# Verify the domain
$ gcloud domains verify xn--rjagslktmedgustavvasa-41bg.se

# Map the domain to the service
$ gcloud beta run domain-mappings create \
  --service arjagslaktmedgustavvasase \
  --domain xn--rjagslktmedgustavvasa-41bg.se \
  --platform managed

# Build and push Docker image
$ gcloud builds submit \
  --tag gcr.io/zippy-cab-252712/arjagslaktmedgustavvasa.se

# Deploy
$ gcloud beta run deploy \
  --image gcr.io/zippy-cab-252712/arjagslaktmedgustavvasa.se \
  --platform managed

# Useless use of cat, this line does nothing except being stupid
$ cat README.md | head -1 | grep '[[:alpha:]]' | tail -1 | awk '{print $6 " " $7}' | sed 's,?,,'

# Open the site
$ xdg-open https://ärjagsläktmedgustavvasa.se
```
