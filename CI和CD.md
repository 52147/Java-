# CI/CD
CI代表contious integration 持續集成，CD 代表continus delivery持續交付、contius deployment持續部署。    

1. CI 持續集成:自動 build, test, merge。 當應用程序合併更改後，系統會自動構建應用程序並運行自動化測試(包含單元測試和集成測試)來測試這些更改。   
2. CD 持續交付: 自動提交到repo。完成CI中的構建和單元與集成測試後，CD持續交付可以自動將代碼發佈到repositary，repositary為可以隨時部署到生產環境的代碼庫。    
3. CD 持續部署: 自動將應用程序發布到生產環境。   


常見的CI/CD工具：GitLab, Jenkins, Circle。     
https://www.redhat.com/zh/topics/devops/what-is-ci-cd
