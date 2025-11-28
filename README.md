command to run --- uvicorn main:app --reload

# ⭐ **Problem Statement**

Creating advertising creatives for retail platforms (like Facebook, Instagram, Amazon, Tesco, Walmart) is difficult for many businesses, especially small brands. Each retailer has strict rules about what creatives should look like — where the product should be placed, how big the logo must be, what text is allowed, what colors can be used, and what cannot be shown.

Designers must create different versions of the same creative for multiple sizes (e.g., Story, Feed, Banner). This requires time, skill, design experience, and repeated manual editing. If any guideline is violated, retailers reject the ads, causing time loss and financial loss.

Most existing design tools require manual work and do not check whether the creative follows retailer rules. Smaller advertisers cannot afford professional design agencies, and non-designers struggle to make high-quality creatives that follow all rules.

### **In simple words:**

Companies struggle to make good-looking, correct-format, rule-compliant ads quickly and cheaply — and current tools don’t help enough.

---

# ⭐ **What Our Solution Does**

We are building a **Semantic AI-Driven Creative Builder**, a smart tool that automatically creates professional and retailer-approved creatives with minimal effort. It uses AI to **understand rules, design layouts, check compliance, and generate multiple sizes automatically.**

### **How Our Solution Works (Simple Explanation)**

| User Action                          | What Our AI Does                                     |
| ------------------------------------ | ---------------------------------------------------- |
| User uploads product image & logo    | AI removes background and prepares assets            |
| User uploads retailer guidelines PDF | AI reads and understands rules automatically         |
| User chooses mood/theme              | AI generates multiple creative design layouts        |
| User edits design if needed          | AI checks rules and warns about violations           |
| User clicks “Generate all sizes”     | AI automatically creates Story, Feed, Banner formats |
| User downloads final campaign pack   | Files are optimized and ready to publish             |

---

# ⭐ **How We Will Solve the Problem Using AI**

### ✔ AI that reads and understands retailer guideline documents

(not manually coded rules)

### ✔ AI that generates creative layouts automatically

(generative design, not manual drag-and-drop)

### ✔ AI that checks compliance visually and textually

(logo size, safe zones, banned words, readability, hierarchy)

### ✔ AI that resizes creatives automatically for all formats

(no manual resizing or cropping)

### ✔ A simple editor for users to tweak designs easily

(no design expertise needed)

### ✔ One-click export of all ad sizes under 500KB

---

# ⭐ **Benefits of Our Solution**

| For Small Businesses    | For Designers              | For Retailers          |
| ----------------------- | -------------------------- | ---------------------- |
| No design skills needed | Faster creative production | Fewer rejected ads     |
| Saves money             | Smart layout suggestions   | Brand consistency      |
| Saves time              | Reduces repetitive work    | Fewer rule violations  |
| High-quality designs    | AI compliance assistance   | Better user experience |

---

# ⭐ **One-Line Summary**

> We make creative production simple and intelligent by using AI that understands guidelines, generates beautiful layouts, ensures compliance, and automatically creates all ad formats — so anyone can design like a professional.

---

## 🏗 System Architecture

The system includes:
- A React-based Canvas Builder UI
- Backend AI engine for layout generation & compliance validation
- Semantic Guideline Interpreter using LLMs
- Vision-Language based Compliance Validator
- Multi-format Creative Generator
- Export Engine for optimized final images

### Architectural Flow
User Uploads Assets & Guidelines →
AI Guideline Interpreter extracts constraint rules →
Generative Layout Engine produces layout variations →
User edits in Visual Canvas →
Semantic Compliance Validator checks for violations →
Adaptive Multi-Format Engine produces variations for each dimension →
User downloads final asset pack.

## 🔄 System Workflow Steps

1. User uploads packshot, background, logo, and guideline PDF.
2. Guideline Interpreter extracts semantic rules.
3. AI generates multiple layouts & styles.
4. User selects layout and edits via canvas.
5. AI validates compliance using Vision + NLP.
6. System autogenerates multi-format assets.
7. User downloads final campaign creatives (<500KB).

## 📋 Requirements Summary

### Functional Requirements
- Upload product assets
- Remove background via MODNet
- Generate AI-based layout variations
- Interpret retailer guideline PDF
- Real-time compliance feedback
- Multi-format creative resizing
- Export optimized final creatives

### Non-Functional Requirements
- Fast inference
- Clean and intuitive UI
- Scalable for any retailer guidelines
- High visual quality output


🏗 System Architecture Overview

START
 ↓
Upload Product Image / Logo / Background / Guideline PDF
 ↓
Guideline Interpreter extracts constraint rules
 ↓
AI Generative Engine produces multiple layout options
 ↓
User selects design and edits in Canvas
 ↓
Semantic Compliance Validator checks rule violations
 ↓
AI suggests fixes / auto-corrects layout
 ↓
Adaptive Multi-Format Generator produces Story / Feed / Banner sizes
 ↓
Export final creative pack (JPG/PNG under 500KB)
 ↓
END
----

⭐ TASK 1 — UI Wireframes (Simple Text-Based Wireframe)

---
## Home Page UI Wireframe

---------------------------------------------------------
| Semantic AI Creative Builder                            |
---------------------------------------------------------
| Upload Assets:  [Upload Packshot] [Upload Logo]         |
| Upload Background:   [Select/Upload]                    |
---------------------------------------------------------
| Upload Retailer Guidelines PDF  [Upload]                |
---------------------------------------------------------
| Select Creative Style: [Minimal] [Bold] [Luxury] [Fun]  |
---------------------------------------------------------
|   [Generate AI Layouts]                                 |
---------------------------------------------------------

## Canvas Editor UI Wireframe

-------------------------------------------------------------
|  Canvas Workspace (Editable Creative Preview Area)        |
-------------------------------------------------------------
| Tools: Move | Resize | Rotate | Add Text | Add Shape      |
| Assets: Product | Logo | Background | Elements            |
| Safe Zones Overlay [Toggle]                               |
| Layout Suggestions  [Option 1] [Option 2] [Option 3]       |
-------------------------------------------------------------
| Compliance Alerts:   ✔ No Violations | ⚠ Fix Logo Size    |
-------------------------------------------------------------
| Buttons:  [Auto Fix] [Generate Multi-format] [Download]   |
-------------------------------------------------------------

## Multi-Format Preview UI Wireframe

-----------------------------------------
| Preview Formats:                      |
|  9:16 (Story)   |  1:1 (Feed)         |
|  1.91:1 Banner  |  Carousel           |
-----------------------------------------
|      [Download All Formats Pack]      |
-----------------------------------------

---

⭐ TASK 2 — API Endpoints Planning

---

## Backend API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| /upload/packshot | POST | Upload product image |
| /remove-bg | POST | Remove background using MODNet |
| /upload-guideline | POST | Upload guideline PDF/text |
| /parse-guideline | POST | Extract rules using LLM |
| /generate-layouts | POST | Generate creative layout options |
| /compliance-check | POST | Validate layout using Vision + NLP |
| /generate-formats | POST | Create multi-format creatives |
| /export | GET | Download final assets |

---
⭐ TASK 3 — Semantic AI Guideline Interpreter Prompt
---

## AI Design Components

### Guideline Interpreter Prompt
# TASK 4
You are a Retail Creative Compliance Expert. Your goal is to read and interpret retailer
guidelines and convert them into clear creative constraints.

Input: Retailer guideline document text.
Output: A structured JSON that contains:
- Placement rules (logo, product, CTA, text)
- Color and branding restrictions
- Safe zone requirements
- Copy restrictions (claims/pricing/sustainability/etc.)
- Tone of voice requirements
- File size & format requirements
- Text font/legibility guidelines

Do not summarize the document. Convert rules into actionable constraints
for validating ad creative layout and content.


### Compliance Engine Logic
- Visual model checks layout violations
- Language model checks text tone & banned phrases
- Suggests corrective actions automatically
