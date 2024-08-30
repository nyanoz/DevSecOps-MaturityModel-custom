# Customization
This repo is there to customize the original OWASP DevSecOps Maturity Model.

## Generation of yaml and usage of it
```bash
cd DevSecOps-MaturityModel-custom
mkdir /tmp/generated
docker run  -e "IS_IMPLEMENTED_WHEN_EVIDENCE=true" -v $(pwd)/data/custom:/var/www/html/src/assets/YAML/custom -v /tmp/generated:/var/www/html/src/assets/YAML/generated wurstbrot/dsomm-yaml-generation
docker run  -p 8080:8080 -v /tmp/generated:/srv/assets/YAML/generated -v $(pwd)/evidence-images:/srv/assets/evidence-images wurstbrot/dsomm:latest
```
You can set the environment variable `IS_IMPLEMENTED_WHEN_EVIDENCE=true` to enable an activity if evidence is set.
 # Development
docker run -ti -v $(pwd)/../DevSecOps-MaturityModel-data/yaml-generation/generateDimensions.php:/var/www/html/yaml-generation/generateDimensions.php  -v $(pwd)/../DevSecOps-MaturityModel-data/yaml-generation/:/var/www/html/yaml-generation/  -e "IS_IMPLEMENTED_WHEN_EVIDENCE=true" -v $(pwd)/data/custom:/var/www/html/src/assets/YAML/custom -v $(pwd)/generated:/var/www/html/src/assets/YAML/generated  wurstbrot/dsomm-yaml-generation bash
