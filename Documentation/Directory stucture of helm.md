<img width="626" height="207" alt="image" src="https://github.com/user-attachments/assets/b1a55171-e7fd-4468-852f-acaff25be62a" />

You can see that there is Charts folder where we can Add dependent subchart in it. eg. for application mysql is pre-requisit then you can add tar file or another helm directory stucture in it
---
## See the dependancies of charts
```
helm dependancy list <chart name>
```
## If missing 
```
helm dependacy update <name of chart>
```
