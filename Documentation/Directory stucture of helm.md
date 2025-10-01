<img width="626" height="207" alt="image" src="https://github.com/user-attachments/assets/4089888e-059b-49e3-ab60-3a7761c035e9" /><img width="626" height="207" alt="image" src="https://github.com/user-attachments/assets/b1a55171-e7fd-4468-852f-acaff25be62a" />

#### You can see that there is Chart#Z folder where we can Add dependent subchart in it. eg. for application mysql is pre-requisit then you can add tar file or another helm directory stucture in it
---
## See the dependancies of charts
```
helm dependancy list <chart name>
```
## If missing 
```
helm dependacy update <name of chart>
```
## See the default values associated with helm
```
helm show values <chart name> 

**save the values file for adding custom values**

helm show values <chart name>  > custom-values.yaml

```
