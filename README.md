# 步驟
1. **在 Azure 上建立資源群組**

    在 Azure 上建立一個資源群組--名稱自訂

2. **建立儲存體帳戶、翻譯工具和語言分析工具**

    建立Azure Containor Registry

3. **管理使用者要開啟，並存取金要**

   建立一個 Docker 映像檔並標記它，以便推送到 Azure Container Registry。

4. **到DockerFile終端機執行**
   
   1.登入docker
   ```bash
    docker login <登入伺服器>
    ```
   2.建立映像檔
   ```bash
    docker image build -t <該映像檔名稱> .
    ```
   3.確認映像檔是否建立成功
      ```bash
    docker image ls
    ```

5. **登入到 Azure**
   
   1.登入azure
   ```bash
    az login
    ```

6. **建立 Azure Container Registry 容器登錄**
   
    1.建立Azure Container Registry
     ```bash
    az acr create --resource-group <資源群組名稱> --name <容器登錄名稱> --sku Basic
    ```
     2.登入
    ```bash
    az acr login --name <容器登錄名稱>
    ```

7. **推送 Docker 映像檔到 Azure Container Registry**

    1.標記該印像檔
    ```bash
    docker tag <該映像檔名稱> <容器登錄名稱>.azurecr.io/<該映像檔名稱>:v1
    ```
    2.推送映像檔到 Azure Container Registry
    ```bash
    docker push <容器登錄名稱>.azurecr.io/<該映像檔名稱>:v1
    ```
    3.確認映像檔是否成功推送到Azure Container Registry中的存放庫
   
8. **建立容器執行個體**

    在Azure建立一個容器執行個體並設定--名稱自訂

9. **執行**
    
    ```bash
    docker run -p 8080:8080 <該映像檔名稱>
    ```
    瀏覽器開啟URL，並開始使用

