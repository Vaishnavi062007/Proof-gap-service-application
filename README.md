# ProofGap – Service Claim Verification System

##Problem Statement

When a customer gives an electronic device such as a laptop, mobile phone, AC, or other device to a service centre, the technician may claim that a repair or replacement has been completed.

However, customers often have no reliable way to verify whether the claimed service was actually performed.

For example, if a technician claims that a laptop battery was replaced, the customer may not be able to verify:

- Whether the battery was actually replaced
- Whether the correct battery was used
- Whether the battery is properly installed
- Whether the serial number matches
- Whether the submitted service evidence is genuine

This creates a **trust and verification gap between customers and service centres.**

---

##  Solution

**ProofGap** is an **AI-based Service Claim Verification System** that analyses service evidence and verifies whether a technician's service claim is supported by the available evidence.

### System Workflow

**Service Case → Device Detection → Claim Identification → Evidence Upload → AI Analysis → Evidence Verification → Final Report**

ProofGap uses multiple AI models to analyse different types of service evidence.

###  AI Components

| Component | Purpose | Model |
|---|---|---|
| DS1 – Electronics Detection | Identifies the electronic device | YOLOv8 |
| DS2 – Battery Detection | Detects battery type | YOLOv8 |
| DS3 – Battery Installation | Verifies battery installation | YOLOv8 |
| DS4 – Serial Number | Detects and reads serial numbers | YOLO + OCR |
| DS5 – Image Forgery | Detects possible image manipulation | ResNet50 / EfficientNet |

---

##  Datasets

### DS1 – Electronics Detection

The dataset contains electronic device classes such as:

- Controller
- Earbuds
- Headphones
- Keyboard
- Laptop
- Monitor
- Phones
- Smartwatch

**Dataset:** [Electronics Dataset](https://universe.roboflow.com/a-i-yo9e4/electronic-devices-57wxc)

**Model:** YOLOv8n  
**Training:** 30 Epochs  
**Status:**  Completed

---

### DS2 – Battery Detection

The dataset contains the following battery classes:

- 9V
- AA
- Button Cell
- Other

**Dataset:** [Battery Detection Dataset](https://universe.roboflow.com/search?q=battery+class%3Aaa+object+detection)

**Model:** YOLOv8n  
**Training:** 50 Epochs  
**Status:**  Completed

---

### DS3 – Battery Installation Detection

Used to determine whether the claimed battery replacement or installation is supported by visual evidence.

**Model:** YOLOv8  
**Status:**  In Progress

---

### DS4 – Serial Number Detection & OCR

Used to detect the serial-number region and extract the serial number from service evidence.

**Model:** YOLO + OCR  
**Status:**  In Progress

---

### DS5 – Image Forgery Detection

Used to analyse whether submitted service evidence images show possible signs of manipulation or forgery.

**Model:** ResNet50 / EfficientNet  
**Status:**  In Progress

---

## 📈 Current Progress

| AI Component | Status |
|---|---|
| DS1 – Electronics Detection |  Completed |
| DS2 – Battery Detection |  Completed |
| DS3 – Battery Installation |  In Progress |
| DS4 – Serial Number OCR |  In Progress |
| DS5 – Image Forgery Detection |  In Progress |

**Overall Progress: 2 / 5 AI components completed**

---

##  Verification Result

ProofGap produces an evidence-based verification result:

###  VERIFIED
The available evidence sufficiently supports the service claim.

###  PARTIALLY VERIFIED
Some evidence supports the claim, but complete verification is not possible.

###  COULD NOT VERIFY
The available evidence does not sufficiently support the service claim.

---

##  Example

### Service Claim

> "Laptop battery has been replaced."

### Evidence Analysed

1. Device image
2. Battery image
3. Battery installation image
4. Serial number
5. Before/after diagnostic evidence
6. Image authenticity

### Final Output

```text
Service Claim: Battery Replacement

Device: Laptop
Battery: Detected
Installation: Verified
Serial Number: Matched
Image Authenticity: Passed

Final Result: VERIFIED

##  Datasets

| Dataset | Purpose | Source |
|---|---|---|---|
| DS1 – Electronics Detection | Electronic device detection | [Roboflow](https://universe.roboflow.com/a-i-yo9e4/electronic-devices-57wxc?utm_source=chatgpt.com) | ✅ Completed |
| DS2 – Battery Detection | Battery type detection | [Roboflow](https://universe.roboflow.com/ki/battery-detection-ymjep) |
| DS3 – Battery Installation | Battery installation verification | Custom Dataset  |
| DS4 – Serial Number | Serial number detection and OCR | [Roboflow](https://universe.roboflow.com/serial-number-plate-ocr/new-alphanumeric) |
| DS5 – Image Forgery | Image tampering detection | [CASIA v2.0](https://github.com/namtpham/casia2groundtruth) |
