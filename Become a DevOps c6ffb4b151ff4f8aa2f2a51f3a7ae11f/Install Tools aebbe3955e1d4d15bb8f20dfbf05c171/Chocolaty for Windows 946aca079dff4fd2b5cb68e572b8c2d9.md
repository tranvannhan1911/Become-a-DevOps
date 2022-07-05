# Chocolaty for Windows

1. Install
    1. Run **`Get-ExecutionPolicy`**. If it returns **`Restricted`**, then run **`Set-ExecutionPolicy AllSigned`** or **`Set-ExecutionPolicy Bypass -Scope Process`**.
    2. install
        
        ```bash
        Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
        ```
        
2. Usage
    1. Tìm kiếm package trên trang [https://community.chocolatey.org/packages](https://community.chocolatey.org/packages)
    2. copy command và chạy
3. References
    1. [https://chocolatey.org/install](https://chocolatey.org/install)
    2. [https://community.chocolatey.org/packages](https://community.chocolatey.org/packages)