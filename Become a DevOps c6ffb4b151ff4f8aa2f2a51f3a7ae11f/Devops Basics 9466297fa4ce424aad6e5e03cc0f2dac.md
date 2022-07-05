# Devops Basics

- What is DevOps?
    - 
- DevOps Lifecycle
    
    ![Untitled](Devops%20Basics%209466297fa4ce424aad6e5e03cc0f2dac/Untitled.png)
    
- What is Continous Integration?
    - Là một phần mềm phát triển DevOps. Dev thường xuyên commit, merge code trên SCM. Code sẽ được tự động build, test, run,…
    - Là một quá trình tự động trong DevOps
    - Tích hợp các phần mềm, tính năng của nó nhanh hơn, hiệu quả hơn.
    - Bao gồm các giai đoạn: Code, Build, Test, Analyst, Upload to Registry,…
    - Quy trình
        - Code được commit lên SCM
        - Code sẽ được build, test, evaluate ở Build Server. trong giai đoạn này, code sẽ được build thành artifact. Nếu test xảy ra lỗi, thông báo lỗi cho dev để fix.
        - Artifact được upload lên registry
            
            ![Untitled](Devops%20Basics%209466297fa4ce424aad6e5e03cc0f2dac/Untitled%201.png)
            
        - Mục đích của CI là phát hiện các lỗi trong các giai đoạn đầu.
- What is Continous Delivery
    - Là một phần mềm phát triển, code khi thay đổi sẽ được tự động chuẩn bị để release tới production.
    - Là giai đoạn tự động đưa artifact lên server
    - Quy trình
        - Lấy các artifact từ repository/registry về
        - Deploy artifact lên server: cài các dependency, thay đổi cấu hình, network,…
        - Software testing
        - Chuyển artifact đến server production