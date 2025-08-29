# Client Data Extractor 📄➡️📊

A Python tool for **automated client data extraction from PDF documents** using **GPT-4 Vision**.
It converts PDFs to images, analyzes them with GPT-4o, and extracts structured client/business information into a clean **CSV** file.

---

## 🚀 Features

* Convert PDFs into images with multiple fallback methods (`pdf2image`, `pdftocairo`, `PyMuPDF`)
* Encode PDF pages as base64 images for GPT-4 Vision
* Extract structured client and business details:

  * Page number, date, timestamp
  * Client ID, company name, address
  * Contact/attorneys, phone, fax, email
  * Status, manager, billing type
  * Accounts receivable balance and more
* Process multiple PDFs at once
* Save results into **CSV** with detailed logs and extraction statistics
* Handles failures gracefully with empty responses

---

## 📦 Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/client-data-extractor.git
   cd client-data-extractor
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

   ### Core Dependencies:

   * `openai`

   * `pdf2image`

   * `pillow`

   * `pandas`

   * `PyMuPDF` (optional fallback)

   > ⚠️ You may need to install [Poppler](https://github.com/oschwartz10612/poppler-windows/releases/) for `pdf2image` on Windows.

---

## 🔑 Setup

1. Get an [OpenAI API key](https://platform.openai.com/).
2. Save your API key as an environment variable (or use `google.colab.userdata` if running in Colab):

   ```bash
   export OPENAI_API_KEY="your_api_key_here"
   ```

---

## 🛠 Usage

### Run locally:

```bash
python main.py
```

### Workflow:

1. Place your client PDF files inside:

   ```
   /content/drive/MyDrive/Client_Documents
   ```
2. Run the script.
3. Extracted client data will be saved as:

   ```
   extracted_client_data_update.csv
   ```

---

## 📊 Output Example

Each extracted entry will include fields like:

| Document Name | Entry ID | Page Number | Client\_Id | Company\_Name | Address     | Phone          | Email                                       | Status | A/R\_Balance |
| ------------- | -------- | ----------- | ---------- | ------------- | ----------- | -------------- | ------------------------------------------- | ------ | ------------ |
| client1.pdf   | entry\_1 | 2           | 12345      | ABC Corp      | 123 Main St | (555) 123-4567 | [client@email.com](mailto:client@email.com) | Active | \$2,500      |

---

## ⚡ Notes

* **Default limit**: 20 pages per PDF (to control GPT-4 Vision costs).
* Each entry missing a field is labeled `"Not Found"`.
* Logs and statistics are shown after each run, including success rate and entry distribution.

---

## 📈 Roadmap

* [ ] Add support for exporting to **Excel** and **JSON**
* [ ] Build a **Streamlit dashboard** for previewing extracted data
* [ ] Optimize batch processing with async calls to reduce runtime

---

## 📝 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.




