## **Automated OCR-Based Label Data Extraction for Voltas Appliances**

### **Overview**  
This industrial project focuses on automated text extraction from appliance labels for **Voltas Ltd, Ahmedabad**. 
The system uses **PaddleOCR** to extract key details such as **Appliance Type, Brand, Model/Year, and Total Volume** from refrigerator and air conditioner labels.  

---

### **🔧 Technologies Used**

- **FastAPI** – For API-based text extraction  
- **PaddleOCR** – For Optical Character Recognition  
- **OpenCV** – For image preprocessing  
- **Uvicorn** – For running the FastAPI server  
- **Base64 Encoding** – For image processing over API  

---

### **🚀 Project Workflow**

#### **Step 1: Image Acquisition**
- The system receives **Appliance label images** from BASLER industrial machine vision camera .
- **Sample Image**

  ![frame_from_api](https://github.com/user-attachments/assets/c9b54c23-6407-4676-a025-359ccab9db84)


#### **Step 2: OCR Processing**

https://private-user-images.githubusercontent.com/77053184/363696932-97cca04f-e1ed-4257-9fa2-f81c986a5ee4.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mzk5NTczNDcsIm5iZiI6MTczOTk1NzA0NywicGF0aCI6Ii83NzA1MzE4NC8zNjM2OTY5MzItOTdjY2EwNGYtZTFlZC00MjU3LTlmYTItZjgxYzk4NmE1ZWU0LmpwZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTAyMTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwMjE5VDA5MjQwN1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWRkYzIzODRmNThlMzU4NDk4OWViMzU2YTMxMDQ1MzllY2Y4ZDY1YzdiNjJkMWM4MGMxOTA0YTU0YjJmN2U2MTkmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.xatJkUjgEOCWq3GdCl6o1-8PTGAeCrOIzG9OERd2fpg

- The image is **processed using PaddleOCR** to extract text.  
- Unnecessary elements (such as other texts) are filtered out.  

#### **Step 3: Data Extraction & Formatting**
- Extracted text is **mapped** to relevant fields:
  - `Appliance`  
  - `Brand`  
  - `Model/Year`  
  - `Total Volume`  

#### **Step 4: API Response in JSON Format**
- The final extracted text is **formatted as a structured JSON output**.  

---

### **📌 API Endpoints**
| Method | Endpoint | Description |
|--------|---------|------------|
| **GET** | `/ServerCheck` | Checks if the server is running |
| **POST** | `/predict` | Accepts an image and returns extracted text in JSON |

---
**extracted text in JSON**


![image](https://github.com/user-attachments/assets/926d4427-d691-4add-a435-82b9cb4647a6)



---

### **📝 Usage**
#### **1️⃣ conda environment setup**
conda create n voltasbeko python==3.9.18


#### **2️⃣ Install Dependencies**
```bash
pip install fastapi uvicorn paddleocr opencv-python numpy
```

#### **3️⃣ Run the FastAPI Server**
```bash
uvicorn main:app --host 127.0.0.1 --port 5000
```

#### **4️⃣ Test API**
Use **Postman** or **cURL** to send a **POST request** with an image (base64 format).  

** Result from Fast API**
### **📜 Sample JSON Output**
```json
{
    "Appliance": "Refrigerator",
    "Brand": ":VOLTAS.beko",
    "Model/Year": "RFF270D/2024",
    "Total Volume": "230 liters"
}
```

### **🔗 About Voltas Ltd (Industry Context)**
- **Company:** Voltas Ltd, Ahmedabad  
- **Industry:** Home Appliances & HVAC Solutions  
- **Location:** Ahmedabad, Gujarat, India  
- **Use Case:** Automating the extraction of key label data from **refrigerators & AC units** for record-keeping, inventory tracking, and compliance.  

---
