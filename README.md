# 🧠 Lost and Found AI

An intelligent web application designed to **bridge the gap** between people who have lost items and those who have found them.  
This platform leverages **Artificial Intelligence (AI)** to analyze item images, generate visual embeddings using **CLIP**, and automatically identify potential matches across reports.

This system eliminates the need for manual searching by introducing an automated and accurate matching process, significantly enhancing the likelihood of reuniting individuals with their lost belongings.

---

## ✨ Features

- **Report Items:** Users can seamlessly report lost or found items by uploading an image, specifying details, and providing contact information.  
- **AI-Powered Matching:** The backend uses the CLIP AI model to compare an item's image against other items in the opposite category (lost vs. found).  
- **Confidence-Based Results:** Potential matches are displayed with confidence levels — *High*, *Good*, or *Possible*.  
- **Automated Notifications:** Upon a confirmed match, the system automatically sends an email notification to both parties, providing contact details to facilitate retrieval.  
- **Item Management:** Users can retrieve a list of all items they have reported by entering their email address.

---

## 🛠️ Technology Stack

| Component | Technology Used |
|------------|-----------------|
| **Programming Language** | Python 3.10+ |
| **Backend Framework** | FastAPI |
| **Frontend** | HTML5, Tailwind CSS, JavaScript |
| **AI Model** | Sentence Transformer (`clip-ViT-B-32`) |
| **Database** | Qdrant Vector Database (Local Storage) |
| **Templating** | Jinja2 for dynamic HTML and email rendering |
| **Image Handling** | Pillow (PIL) |
| **Email System** | SMTP with Gmail App Password |
| **Web Server** | Uvicorn |

---

## 🏗️ System Architecture

The application follows a **client-server architecture** integrated with AI services:

- **Frontend:** Users interact via forms for reporting lost or found items, built using HTML and Tailwind CSS.  
- **Backend (FastAPI):** Processes reports, generates embeddings, performs similarity searches, and handles notifications.  
- **AI Model (CLIP):** Converts uploaded images into 512-dimensional feature vectors (embeddings).  
- **Database (Qdrant):** Stores these embeddings and performs vector similarity searches using cosine distance.  
- **Email Service (SMTP):** Automates communication between users when items are claimed.

### 🔹 Text-Based Architecture Diagram

```

User
↓
Web Form
↓
FastAPI Server
↓
CLIP Model
↓
Qdrant Vector DB
↓
Match Found

````

---

## 🚀 Setup and Configuration

Follow these steps to set up and run the project locally.

### 1. Clone the Project Folder

```bash
git clone https://github.com/<your-username>/lost-and-found-ai.git
cd lost-and-found-ai
````

### 2. Install Dependencies

```bash
pip install fastapi uvicorn pillow qdrant-client sentence-transformers jinja2
```

### 3. Configure Email

Inside `main.py`, configure your **Gmail App Password** to enable the email notification system.

```python
EMAIL_ADDRESS = "your_email@gmail.com"
EMAIL_PASSWORD = "your_app_password"
```

### 4. Run the Application

```bash
uvicorn main:app --reload
```

### 5. Access the Application

Open your browser and navigate to:
👉 [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

---

## ⚙️ API Endpoints

| Endpoint                              | Method | Description                                                              |
| ------------------------------------- | ------ | ------------------------------------------------------------------------ |
| `/api/report-found`                   | `POST` | Report a found item. Generates embeddings and searches for lost matches. |
| `/api/report-lost`                    | `POST` | Report a lost item. Generates embeddings and searches for found matches. |
| `/api/claim-item`                     | `POST` | Mark items as claimed and send email notifications.                      |
| `/api/item-details/{collection}/{id}` | `GET`  | Retrieve detailed item data by ID.                                       |
| `/api/my-items`                       | `POST` | Retrieve all reported items associated with a user's email.              |

---

## 🔮 Future Enhancements

* Implement user authentication with JWT tokens
* Add map-based visualization of lost/found items
* Enable cloud storage for images (e.g., AWS S3 or Firebase)
* Develop mobile app integration
* Support multi-language localization

---

## 👥 Credits

This project was developed by the **Lost and Found AI Development Team (2025).**



