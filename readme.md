<div align="center">

  <p align="center">
    <a href="https://t.me/cry_batya">
      <img src="https://img.shields.io/badge/Telegram-Channel-blue?style=for-the-badge&logo=telegram" alt="Telegram Channel">
    </a>
    <a href="https://t.me/+b0BPbs7V1aE2NDFi">
      <img src="https://img.shields.io/badge/Telegram-Chat-blue?style=for-the-badge&logo=telegram" alt="Telegram Chat">
    </a>
  </p>
</div>

# hCaptcha API Server

## ⚙️ Installation

1. **Make sure Python 3.8+ is installed** on your system.

2. **Clone the repository**:
   ```bash
   git clone https://github.com/TellBip/hcaptcha_api_for_solver.git
   cd hcaptcha_api_for_solver
   ```

3. **Create a Python virtual environment**:
   ```bash
   python3 -m venv venv
   ```

4. **Activate the virtual environment**:
   - **Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - **macOS/Linux**:
     ```bash
     source venv/bin/activate
     ```

5. **Install required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

6. **Install Chromium browser**:
   ```bash
   python3 playwright install chromium
   ```
   
7. **Get GEMINI API KEY**: 
   Create and set up your GEMINI_API_KEY at: https://aistudio.google.com/apikey

8. **Start the server**:
   ```bash
   python3 hcaptcha_api_server.py --api_key=YOUR_GEMINI_API_KEY
   ```

## 🔧 Command Line Arguments

| Parameter     | Default   | Type      | Description                                                           |
|---------------|-----------|-----------|-----------------------------------------------------------------------|
| `--headless`  | `False`   | `boolean` | Run the browser in headless mode                                      |
| `--useragent` | `None`    | `string`  | Specify a custom User-Agent string for the browser                    |
| `--debug`     | `False`   | `boolean` | Enable debug mode for additional logging                              |
| `--thread`    | `1`       | `integer` | Set the number of browser threads                                     |
| `--proxy`     | `False`   | `boolean` | Enable proxy support                                                  |
| `--host`      | `0.0.0.0` | `string`  | IP address for the API                                                |
| `--port`      | `5050`    | `integer` | Port for the API                                                      |
| `--api_key`   | -         | `string`  | Gemini API key for hCaptcha solving (required)                        |

## 📡 API Documentation

### Solve hCaptcha
```http
GET /hcaptcha?sitekey=914e63b4-ac20-4c24-bc92-cdb6950ccfde
```

#### Request Parameters:
| Parameter  | Type     | Description                                                 | Required |
|------------|----------|-------------------------------------------------------------|----------|
| `sitekey`  | string   | The site key for hCaptcha                                   | Yes      |
| `proxy`    | string   | Proxy in format ip:port or scheme://ip:port:user:pass       | No       |

#### Response:

```json
{
  "task_id": "d2cbb257-9c37-4f9c-9bc7-1eaee72d96a8"
}
```

### Get Result
```http
GET /result?id=d2cbb257-9c37-4f9c-9bc7-1eaee72d96a8
```

#### Request Parameters:
| Parameter | Type     | Description          | Required |
|-----------|----------|----------------------|----------|
| `id`      | string   | Task identifier      | Yes      |

#### Successful Response:
```json
{
  "token": "P0_eyJ0eXAiOiJKV1...",
  "elapsed_time": 5.321
}
```

#### Processing Response:
```json
{
  "status": "processing"
}
```

#### Error Response:
```json
{
  "token": "CAPTCHA_FAIL",
  "elapsed_time": 8.452,
  "error": "Error message"
}
```

## Telegram
http://t.me/+b0BPbs7V1aE2NDFi

Thank you for visiting this repository. Don't forget to support the project by starring and following for updates.

If you have questions, find an issue, or have suggestions for improvement, feel free to contact me or open an *issue* in this GitHub repository.