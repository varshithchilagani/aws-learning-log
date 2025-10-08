# AWS Lambda – Deploying Python Code  
📅 **Date:** October 8, 2025  

---

## 🧠 Overview  

In this learning, I explored how to deploy **Python code** to AWS Lambda, manage dependencies, create reusable components using **Lambda Layers**, and monitor execution logs through **Amazon CloudWatch**.

---

## ⚙️ Uploading Local Code to Lambda  

To bring local Python code into AWS Lambda, there are two main approaches:

1. **Direct Upload:**  
   - Create a `.zip` file containing your `.py` files.  
   - Upload it directly to the **Lambda code editor** from your local system.

2. **Upload via S3:**  
   - Create a ZIP package of your Python files.  
   - Upload the ZIP file to **Amazon S3**.  
   - While creating or updating your Lambda function, select the ZIP from S3.

Both methods allow Lambda to run your custom Python code easily.

---

## 📦 Handling Dependencies  

For dependencies such as external **Python libraries** (like pandas, requests, etc.), we need to package them manually before uploading to Lambda.  
You can install them locally into a folder using the following command:

```bash
pip install --target ./package pandas

```

---
# 📦 Handling Dependencies

After installation:

1. Place your main `.py` file inside the same `package` folder.  
2. Compress the folder into a single `.zip` file.  
3. Upload this ZIP file directly to **Lambda’s code editor**.  

This ensures all required dependencies are available for Lambda execution.

---

## 🧩 Using Lambda Layers

For **reusable code** or **custom libraries**, AWS Lambda provides a feature called **Layers**.  
Layers are ideal when multiple Lambda functions need to share the same code or dependencies.

### Steps to use a layer:
1. Create and upload a layer containing your shared library code or dependencies.  
2. Attach the layer to your Lambda function.  
3. Import the module inside your function code as shown below:

```python
from myModule import *
```

![Screenshot 1](./docs/screenshot1.png)
![Screenshot 2](./docs/screenshot2.png)
![Screenshot 3](./docs/screenshot3.png)


