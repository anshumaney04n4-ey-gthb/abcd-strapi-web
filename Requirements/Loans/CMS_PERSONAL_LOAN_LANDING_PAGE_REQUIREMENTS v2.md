# Loans CMS Requirements v2 - Personal Loan Landing Page

**Date:** 2026-04-15  
**Status:** To be IMPLEMENTED  
**Collection Type:** `loans-landing-pages`

---

## 1. Components

### 1.1 Landing Page Sections
 
| Key | Component | Purpose |
|-----|-----------|---------|
| `header` | `landing-header` | Logo configuration |
| `hero` | `landing-hero` | Hero section with pricing, title, description, highlights |
| `widget` | `application-widget` | Mobile input widget for loan application |
| `smartFeatures` | `smart-features` | Feature highlights carousel section |
| `steps` | `loan-steps` | 3-step loan process section |
| `eligibility` | `eligibility-criteria` | Loan eligibility criteria section |
| `rates` | `rates-charges` | Rates and charges information |
| `simpleSection` | `simple-section` | Benefits highlight section |
| `partners` | `trusted-partners` | Trusted lenders showcase section |
| `faq` | `faq-section` | FAQ section with Q&A |
| `appPromo` | `app-promotion` | Mobile app promotion section |
| `footer` | `landing-footer` | Footer with reference details |
| `mobileNavigation` | `mobile-navigation` | Mobile-specific navigation |

### 1.2 Reusable Components

| Component | Used In |
|-----------|---------|
| `logo` | `header.logo` |
| `product-highlighter` | `hero.productHighlighters[]` |
| `partner-logo` | `hero.partnerLogos[]` |
| `consent-config` | `widget.consentConfig` |
| `cta-config` | `widget.ctaConfig` |
| `smart-feature-item` | `smartFeatures.items[]` |
| `notification-content` | `smartFeatureItem.notificationContent` |
| `step-item` | `steps.items[]` |
| `eligibility-item` | `eligibility.items[]` |
| `rate-item` | `rates.items[]` |
| `benefit-item` | `simpleSection.benefits[]` |
| `partner-item` | `partners.items[]` |
| `faq-item` | `faq.items[]` |
| `app-cta-button` | `appPromo.ctaButtons[]` |
| `reference-details` | `footer.referenceDetails` |
| `side-logo-details` | `footer.sideLogoDetails` |
| `footer-feature` | `footer.features[]` |
| `mobile-footer-banner` | `mobileNavigation.footerBanner` |
| `store-button` | `mobileNavigation.footerBanner.appStoreButton/playStoreButton` |

---

## 2. Schema

### 2.1 `header`

| Field | Type | Required |
|-------|------|:--------:|
| `logo` | logo | Yes |
| `mobileHeaderLogo` | string | Yes |

**logo:**
| Field | Type | Required |
|-------|------|:--------:|
| `src` | string | Yes |
| `alt` | string | Yes |
| `size` | integer | Yes |

### 2.2 `hero`

| Field | Type | Required |
|-------|------|:--------:|
| `slides` | hero-slide[] | Yes |
| `carouselConfig` | carousel-config | Yes |
| `backgroundVariant` | enum [default, light] | Yes |
| `productHighlighters` | product-highlighter[] | Yes |
| `showSeparator` | boolean | Yes (default: true) |

**hero-slide:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `title` | string (rich text) | Yes |
| `subtitle` | string (rich text) | Yes |
| `background` | string (asset URL) | Yes |
| `order` | integer | Yes |

**carousel-config:**
| Field | Type | Required |
|-------|------|:--------:|
| `autoPlay` | boolean | Yes |
| `autoPlayInterval` | integer | Yes |
| `showArrows` | boolean | Yes |
| `showIndicators` | boolean | Yes |
| `indicatorStyle` | enum [dots, bars] | Yes |

**product-highlighter:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `text` | string | Yes |
| `showIcon` | boolean | Yes (default: true) |
| `order` | integer | Yes |

### 2.3 `widget`

| Field | Type | Required |
|-------|------|:--------:|
| `headerTitle` | string (rich text) | Yes |
| `headerBackgroundColor` | string | Yes |
| `title` | string | Yes |
| `mobileInputPlaceholder` | string | Yes |
| `helperText` | string | Yes |
| `consentConfig` | consent-config | Yes |
| `ctaConfig` | cta-config | Yes |

**consent-config:**
| Field | Type | Required |
|-------|------|:--------:|
| `label` | string | Yes |
| `termsText` | string | Yes |
| `termsUrl` | string (URL) | Yes |
| `privacyText` | string | Yes |
| `privacyUrl` | string (URL) | Yes |

**cta-config:**
| Field | Type | Required |
|-------|------|:--------:|
| `buttonText` | string | Yes |
| `trustText` | string | Yes |
| `loadingText` | string | Yes |

### 2.4 `smartFeatures`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `autoScroll` | boolean | Yes (default: true) |
| `autoScrollInterval` | integer | Yes (default: 5000) |
| `items` | smart-feature-item[] | Yes |

**smart-feature-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `variant` | enum [gifting] | Yes |
| `number` | string | Yes |
| `title` | string | Yes |
| `subtitle` | string | No |
| `description` | string (rich text) | Yes |
| `ctaText` | string | Yes |
| `backgroundColor` | string | Yes |
| `backgroundImage` | string | No |
| `order` | integer | Yes |
| `notificationContent` | notification-content | No |

**notification-content:**
| Field | Type | Required |
|-------|------|:--------:|
| `icon` | string | No |
| `headerText` | string | No |
| `title` | string | No |
| `bodyLines` | string[] | No |

### 2.5 `steps`

| Field | Type | Required |
|-------|------|:--------:|
| `tagline` | string | No |
| `heading` | string | Yes |
| `items` | step-item[] | Yes |

**step-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `number` | string | Yes |
| `title` | string | Yes |
| `description` | string (rich text) | Yes |
| `icon` | string | Yes |
| `iconurl` | string | No |
| `iconAlt` | string | Yes |

### 2.6 `eligibility`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `items` | eligibility-item[] | Yes |

**eligibility-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `label` | string | Yes |
| `value` | string | Yes |
| `alternateValueBackground` | boolean | No |

### 2.7 `rates`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `items` | rate-item[] | Yes |

**rate-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `icon` | string | Yes |
| `title` | string | Yes |
| `value` | string | Yes |
| `description` | string (rich text) | Yes |
| `badge` | string | No |

### 2.8 `simpleSection`

| Field | Type | Required |
|-------|------|:--------:|
| `heading` | string | Yes |
| `highlightWord` | string | No |
| `centerImageUrl` | string | Yes |
| `centerImageAlt` | string | Yes |
| `circleBackgroundUrl` | string | No |
| `patternIconUrl` | string | Yes |
| `backgroundColor` | string | Yes |
| `benefits` | benefit-item[] | Yes |
 

**benefit-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `icon` | string | Yes |
| `title` | string | Yes |
| `description` | string (rich text) | Yes |

### 2.9 `partners`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `subtitle` | string | No |
| `items` | partner-item[] | Yes |
| `fallbackLogoSrc` | string | No |

**partner-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `src` | string | Yes |
| `alt` | string | Yes |

### 2.10 `faq`

| Field | Type | Required |
|-------|------|:--------:|
| `title` | string | Yes |
| `defaultOpenIds` | string[] | No |
| `items` | faq-item[] | Yes |

**faq-item:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `question` | string (rich text) | Yes |
| `answer` | string (rich text) | Yes |

### 2.11 `appPromo`

| Field | Type | Required |
|-------|------|:--------:|
| `appLabel` | string | Yes |
| `title` | string (rich text) | Yes |
| `mobileTitle` | string | Yes |
| `subtitle` | string (rich text) | Yes |
| `mobileSubtitle` | string | Yes |
| `fromLabel` | string | Yes |
| `houseLogoSrc` | string | Yes |
| `houseLogoAlt` | string | Yes |
| `qrSrc` | string | Yes |
| `qrAlt` | string | Yes |
| `phoneImageSrc` | string | Yes |
| `phoneImageAlt` | string | Yes |
| `ctaButtons` | app-cta-button[] | Yes |
| `ctaVisibility` | enum [all, ios, android] | Yes |
| `companyInfoLayout` | enum [row, column] | Yes |

**app-cta-button:**
| Field | Type | Required |
|-------|------|:--------:|
| `label` | string | Yes |
| `link` | string (URL) | Yes |
| `iconSrc` | string | Yes |
| `iconAlt` | string | Yes |

### 2.12 `footer`

| Field | Type | Required |
|-------|------|:--------:|
| `referenceDetails` | reference-details | Yes |
| `sideLogoDetails` | side-logo-details | Yes |
| `features` | footer-feature[] | Yes |

**reference-details:**
| Field | Type | Required |
|-------|------|:--------:|
| `heading` | string | Yes |
| `name` | string | Yes |
| `logo` | string | Yes |
| `certification` | string | Yes |

**side-logo-details:**
| Field | Type | Required |
|-------|------|:--------:|
| `image` | string | Yes |
| `alt` | string | Yes |

**footer-feature:**
| Field | Type | Required |
|-------|------|:--------:|
| `id` | string | Yes |
| `text` | string | Yes |

### 2.13 `mobileNavigation`

| Field | Type | Required |
|-------|------|:--------:|
| `tabs` | object[] | No |
| `footerBanner` | mobile-footer-banner | Yes |

**mobile-footer-banner:**
| Field | Type | Required |
|-------|------|:--------:|
| `text` | string | Yes |
| `appStoreButton` | store-button | Yes |
| `playStoreButton` | store-button | Yes |

**store-button:**
| Field | Type | Required |
|-------|------|:--------:|
| `icon` | string | Yes |
| `label` | string | Yes |
| `url` | string (URL) | Yes |

---

## 3. Expected API Response

**Endpoint:** `GET /api/loans-landing-pages?filters[subProduct][$eq]=personal&populate=*`

```json
{
  "data": {
      "header": {
        "logo": {
          "src": "/logos/lob/abcd.svg",
          "alt": "ABCD Logo",
          "size": 40
        },
        "mobileHeaderLogo": "/logos/lob/abcd.svg"
      },
      "hero": {
        "slides": [
          {
            "id": "slide-1",
            "title": "Apply for a Instant Personal Loan Up to ₹15 Lakh, in Minutes!",
            "subtitle": "Access a wide variety of loan offers across multiple lenders.",
            "background": "/assets/landing/pl-herosection-bag.webp",
            "order": 1
          },
          {
            "id": "slide-2",
            "title": "Apply for a Personal Loan with Flexible Terms",
            "subtitle": "Choose from a variety of loan options tailored to your needs.",
            "background": "/assets/landing/pl-herosection-bag.webp",
            "order": 2
          },
          {
            "id": "slide-3",
            "title": "Join 2.5 Lakh+ borrowers",
            "subtitle": "Trusted by thousands for personal loans",
            "background": "/assets/landing/pl-herosection-bag.webp",
            "order": 3
          }
        ],
        "carouselConfig": {
          "autoPlay": true,
          "autoPlayInterval": 5000,
          "showArrows": true,
          "showIndicators": true,
          "indicatorStyle": "bars"
        },
        "backgroundVariant": "default",
        "productHighlighters": [
          {
            "id": "highlighter-1",
            "text": "Get Instant Offer",
            "showIcon": true,
            "order": 1
          },
          {
            "id": "highlighter-2",
            "text": "No Paperwork",
            "showIcon": true,
            "order": 2
          },
          {
            "id": "highlighter-3",
            "text": "Low interest rates",
            "showIcon": true,
            "order": 3
          }
        ],
        "showSeparator": true
      },
      "widget": {
        "headerTitle": "Verified partners. <strong>100% transparent</strong>. Fully secure.",
        "headerBackgroundColor": "#7c2279",
        "title": "Enter your mobile number to get started",
        "mobileInputPlaceholder": "Enter 10-digit mobile number",
        "helperText": "OTP will be sent to your mobile number",
        "consentConfig": {
          "label": "I agree with",
          "termsText": "Terms & Conditions",
          "termsUrl": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
          "privacyText": "Privacy Policy",
          "privacyUrl": "https://www.adityabirlacapital.com/abcd/privacy-policy"
        },
        "ctaConfig": {
          "buttonText": "Apply now",
          "trustText": "Join 1L+ investors trusting ABCD for Personal Loans",
          "loadingText": "Processing..."
        }
      },
      "smartFeatures": {
        "title": "Smart Features. Real Impact.",
        "autoScroll": true,
        "autoScrollInterval": 5000,
        "items": [
          {
            "id": "pl-instant-offer",
            "variant": "gifting",
            "number": "01",
            "title": "Get Instant Offer",
            "subtitle": "Personalized loan assessment",
            "description": "Unlock your personalized loan offer in seconds with our smart AI assessment",
            "ctaText": "Apply Now",
            "backgroundColor": "#FFF8E7",
            "backgroundImage": "/assets/landing/pl-instant-offer-bg.png",
            "order": 1,
            "notificationContent": {
              "icon": "bell",
              "headerText": "Your A/C can be credited with ₹30,000/-",
              "title": "",
              "bodyLines": []
            }
          },
          {
            "id": "pl-no-paperwork",
            "variant": "gifting",
            "number": "02",
            "title": "100% Digital Process",
            "subtitle": "Completely paperless",
            "description": "Complete your loan application entirely online without any physical documentation",
            "ctaText": "Start Application",
            "backgroundColor": "#E8F5E9",
            "backgroundImage": "/assets/landing/pl-instant-offer-bg.png",
            "order": 2
          },
          {
            "id": "pl-quick-disbursal",
            "variant": "gifting",
            "number": "03",
            "title": "Quick Disbursal",
            "subtitle": "Fast fund transfer",
            "description": "Get funds credited directly to your account within 24 hours of approval",
            "ctaText": "Learn More",
            "backgroundColor": "#E3F2FD",
            "backgroundImage": "/assets/landing/pl-instant-offer-bg.png",
            "order": 3
          }
        ]
      },
      "steps": {
        "tagline": "Personal Loan",
        "heading": "Get Your Loan in 3 Easy Steps",
        "items": [
          {
            "id": "step-1",
            "number": "1",
            "title": "Provide Basic Details",
            "description": "Share a few quick details to help us personalise your loan offer",
            "icon": "/assets/landing/document-11.svg",
            "iconurl": "/assets/landing/document-11.svg",
            "iconAlt": "Document icon"
          },
          {
            "id": "step-2",
            "number": "2",
            "title": "Choose & Apply Loan Offers",
            "description": "Pick the offer that best fits your needs and repayment plan.",
            "icon": "/assets/landing/filter-1.svg",
            "iconurl": "/assets/landing/filter-1.svg",
            "iconAlt": "Filter icon"
          },
          {
            "id": "step-3",
            "number": "3",
            "title": "Get instant Cash in Bank",
            "description": "Once approved, your loan is transferred directly to your bank account in minutes.",
            "icon": "/assets/landing/money-4.svg",
            "iconurl": "/assets/landing/money-4.svg",
            "iconAlt": "Money icon"
          }
        ]
      },
      "eligibility": {
        "title": "Personal Loan Eligibility",
        "items": [
          {
            "id": "age-limit",
            "label": "Age Limit",
            "value": "19 to 60 years",
            "alternateValueBackground": true
          },
          {
            "id": "income",
            "label": "Income",
            "value": "Min. ₹10,000/m",
            "alternateValueBackground": false
          },
          {
            "id": "residency",
            "label": "Residency",
            "value": "Resident of India",
            "alternateValueBackground": true
          }
        ]
      },
      "rates": {
        "title": "Rates & Charges",
        "items": [
          {
            "id": "rate-1",
            "icon": "/assets/landing/rate-pl-loan.svg",
            "title": "Loan Amount",
            "value": "Min. ₹25,000 and Max. 5 Lakhs",
            "description": "Min. ₹25,000 and Max. 5 Lakhs",
            "badge": "Best Rate"
          },
          {
            "id": "rate-2",
            "icon": "/assets/landing/rate-pl-repayment.svg",
            "title": "Repayment Tenure",
            "value": "12 months to 36 months",
            "description": "12 months to 36 months"
          },
          {
            "id": "rate-3",
            "icon": "/assets/landing/rate-pl-interest.svg",
            "title": "Rate of Interest",
            "value": "10.99% to 30% per annum",
            "description": "10.99% to 30% per annum",
            "badge": "Zero Charges"
          },
          {
            "id": "rate-4",
            "icon": "/assets/landing/rate-pl-delivery.svg",
            "title": "Free Insurance on Delivery",
            "value": "1.18% - 4.13% of Loan amount incl. GST.",
            "description": "1.18% - 4.13% of Loan amount incl. GST."
          }
        ]
      },
      "simpleSection": {
        "heading": "Personal Loans Made Simple, Fast & Transparent",
        "highlightWord": "Simple",
        "centerImageUrl": "loans/assets/personal-loan/icons/money_simple_lending.svg",
        "centerImageAlt": "Hands holding money bag with rupee symbol",
        "circleBackgroundUrl": "",
        "patternIconUrl":  "loans/assets/personal-loan/icons/patternIconLending.svg",
        "backgroundColor": "#FFFFFF",
        "benefits": [
          {
            "id": "benefit-1",
            "icon": "speed",
            "title": "Instant Approval",
            "description": "Get loan approval in minutes with our AI-powered assessment engine"
          },
          {
            "id": "benefit-2",
            "icon": "security",
            "title": "Secure Process",
            "description": "Your data is encrypted and protected with bank-grade security"
          },
          {
            "id": "benefit-3",
            "icon": "compare",
            "title": "Compare Offers",
            "description": "Access multiple lender offers in one place and choose the best"
          },
          {
            "id": "benefit-4",
            "icon": "support",
            "title": "24/7 Support",
            "description": "Our customer support team is always available to help you"
          }
        ]
      },
      "partners": {
        "title": "Our Trusted Lending Partners",
        "subtitle": "We are associated with India's popular lenders",
        "items": [
          {
            "id": "partner-1",
            "src": "/assets/vehicle-insurance/dashboard/icic.svg",
            "alt": "ICICI Bank"
          },
          {
            "id": "partner-2",
            "src": "/assets/vehicle-insurance/dashboard/acko.svg",
            "alt": "ACKO"
          },
          {
            "id": "partner-3",
            "src": "/assets/vehicle-insurance/dashboard/digit.svg",
            "alt": "Digit"
          },
          {
            "id": "partner-4",
            "src": "/assets/vehicle-insurance/dashboard/tata.svg",
            "alt": "Tata AIG"
          },
          {
            "id": "partner-5",
            "src": "/assets/vehicle-insurance/dashboard/general.svg",
            "alt": "Bajaj Allianz"
          }
        ],
        "fallbackLogoSrc": ""
      },
      "faq": {
        "title": "Frequently Asked Questions",
        "defaultOpenIds": ["pl-faq-1"],
        "items": [
          {
            "id": "pl-faq-1",
            "question": "What is the maximum loan amount I can get?",
            "answer": "You can get a personal loan up to ₹15 Lakh, depending on your eligibility, income, and credit profile. The final amount will be determined by the lender based on their assessment."
          },
          {
            "id": "pl-faq-2",
            "question": "How quickly can I get the loan disbursed?",
            "answer": "Once your application is approved and all documents are verified, the loan amount is typically disbursed within 24 hours directly to your bank account."
          },
          {
            "id": "pl-faq-3",
            "question": "What documents are required for a personal loan?",
            "answer": "You need basic KYC documents: Aadhaar card, PAN card, bank statements for the last 3-6 months, and income proof (salary slips or ITR). Additional documents may be required based on the lender's policy."
          },
          {
            "id": "pl-faq-4",
            "question": "Can I prepay my personal loan without penalty?",
            "answer": "Yes, most lenders allow prepayment without any penalty charges. However, it's recommended to check the specific terms with your chosen lender before proceeding."
          },
          {
            "id": "pl-faq-5",
            "question": "What is the minimum credit score required?",
            "answer": "While requirements vary by lender, a credit score of 650 or above generally improves your chances of approval with better interest rates. Some lenders may approve loans with lower scores based on other factors."
          },
          {
            "id": "pl-faq-6",
            "question": "How is my loan eligibility calculated?",
            "answer": "Loan eligibility is calculated based on multiple factors including your monthly income, existing obligations, credit score, employment stability, and repayment capacity. Our AI-powered engine instantly assesses these factors to determine your eligibility."
          },
          {
            "id": "pl-faq-7",
            "question": "Can self-employed individuals apply for a personal loan?",
            "answer": "Yes, both salaried and self-employed individuals can apply. Self-employed applicants need to provide business proof, ITR for the last 2-3 years, and bank statements showing regular income."
          },
          {
            "id": "pl-faq-8",
            "question": "What happens if I miss an EMI payment?",
            "answer": "Missing an EMI can result in late payment charges and may negatively impact your credit score. It's important to contact your lender immediately if you're facing difficulty in making payments to discuss possible solutions."
          }
        ]
      },
      "appPromo": {
        "appLabel": "The ABCD app",
        "title": "Everything Finance\nas simple as\nABCD",
        "mobileTitle": "Everything Finance as simple as ABCD",
        "subtitle": "Download the ABCD app and start doing more with your money everyday",
        "mobileSubtitle": "Download the ABCD app today",
        "fromLabel": "From the house of",
        "houseLogoSrc": "/assets/vehicle-insurance/abcd-logo.png",
        "houseLogoAlt": "ABCD Logo",
        "qrSrc": "/assets/vehicle-insurance/qr-code.png",
        "qrAlt": "QR Code to download ABCD app",
        "phoneImageSrc": "/assets/gold-loan/gl-finanace.png",
        "phoneImageAlt": "ABCD app showing personal loans",
        "ctaButtons": [
          {
            "label": "App Store",
            "link": "https://apps.apple.com/",
            "iconSrc": "/assets/mobile-nav/apple.svg",
            "iconAlt": "Apple App Store"
          },
          {
            "label": "Google Play",
            "link": "https://play.google.com/store",
            "iconSrc": "/assets/mobile-nav/google.svg",
            "iconAlt": "Google Play Store"
          }
        ],
        "ctaVisibility": "all",
        "companyInfoLayout": "column"
      },
      "footer": {
        "referenceDetails": {
          "heading": "Powered by",
          "name": "ABCD",
          "logo": "/assets/landing/Grouping.svg",
          "certification": "A Aditya Birla Capital Company - ISO 27001:2013 certified."
        },
        "sideLogoDetails": {
          "image": "/assets/landing/pl-footer-money.png",
          "alt": "Money bag with coins"
        },
        "features": [
          {
            "id": "footer-feature-1",
            "text": "Get Instant Offer"
          },
          {
            "id": "footer-feature-2",
            "text": "No Paperwork"
          },
          {
            "id": "footer-feature-3",
            "text": "Lowest interest rate"
          }
        ]
      },
      "mobileNavigation": {
        "tabs": [],
        "footerBanner": {
          "text": "Download the app",
          "appStoreButton": {
            "icon": "apple",
            "label": "App Store",
            "url": "https://apps.apple.com"
          },
          "playStoreButton": {
            "icon": "google",
            "label": "Play Store",
            "url": "https://play.google.com"
          }
        }
      }
  }
}
```

---

## 4. Content Validation Rules

### Required Fields:
- All top-level section relations must be populated
- `slides` in hero: minimum 1 item, maximum 5 items recommended
- `carouselConfig`: autoPlayInterval should be between 3000-10000ms
- `indicatorStyle` enum: only accepts "dots" or "bars"
- `backgroundVariant`: only accepts "default" or "light"
- `productHighlighters` in hero: minimum 3 items with unique IDs
- `steps.items`: exactly 3 items required
- `faq.items`: minimum 5 items recommended
- `rate.items`: minimum 4 items recommended
- Color fields must contain valid hex color codes
- URLs must be HTTPS and publicly accessible

### Hero Carousel:
- Slides must have sequential ordering (1, 2, 3, ...)
- Each slide requires unique `id`, `title`, `subtitle`, and `background`
- `autoPlayInterval` in milliseconds (e.g., 5000 = 5 seconds)
- `showArrows` and `showIndicators` control carousel UI elements
- Items must have sequential ordering (1, 2, 3, ...)
- `number` field format: "01", "02", "03"
- `variant` only accepts: "gifting"

### Media Requirements:
- All image URLs must return 200 status and valid image formats
- SVG preferred for icons and logos
- WebP format recommended for background images (including hero carousel backgrounds)
- PNG as fallback if WebP is not supported
- Minimum resolution: 300x300px for logos, 600x400px for backgrounds
- Hero carousel backgrounds: 1920x600px minimum for desktop, 1080x720px for mobile

### Text Fields:
- Rich text fields support HTML: `<strong>`, `<em>`, `<a>`, `<br>`
- Title fields: max 120 characters
- Description fields: max 500 characters
- URL fields: must start with https://

---

## 5. Localization & Internationalization

### Default Language: English (en-US)

### Content by Language:
- All text fields should be translatable
- Rich text fields support multi-language content
- URL fields may vary by region (app store links)

### Supported Languages:
- English (en-US) - Default
- Hindi (hi-IN) - Optional
- Other regional languages (to be configured)

---

## 6. Integration Guide

### Frontend Integration Path:
`src/app/personal/landing/page.tsx`

### Data Flow:
1. Fetch from Strapi: `GET /api/personal-loan-landings?populate=*`
2. Cache response with TTL: 5 minutes
3. Fallback to hardcoded `FALLBACK_LANDING_CONTENT` on error
4. Display notification if fallback is used

### Error Handling:
| Scenario | Action |
|----------|--------|
| Network timeout | Use fallback content |
| Invalid JSON | Log error, use fallback |
| Partial data missing | Merge with fallback |
| CMS unavailable (500) | Use fallback, retry after 5 min |

---

## 7. Notes

| Item | Detail |
|------|--------|
| Fallback source | `src/app/personal/landing/content/fallback.ts` |
| CMS transformer | `src/app/personal/landing/content/index.ts` |
| Fallback behavior | If CMS is unavailable or content is empty, `FALLBACK_LANDING_CONTENT` is returned |
| Supported response shape | Transformer supports both Strapi `data: []` and `data: {}` styles |

---

## 8. Change History

| Version | Date | Status | Changes |
|---------|------|--------|---------|
| v2 | 2026-04-23 | Updated | Hero section changed from static image to carousel/slideshow with multiple slides, added carouselConfig, backgroundVariant, and hero-slide schema |
| v1 | 2026-04-15 | Implemented | Initial CMS structure from fallback.ts |

---

## 9. Deployment Checklist

- [ ] All collections created in Strapi
- [ ] Permissions configured for roles (Admin, Editor, Marketing Manager)
- [ ] API documentation generated
- [ ] Content migration from fallback completed
- [ ] Frontend integration tested
- [ ] Fallback error handling verified
- [ ] Cache strategy implemented (5-minute TTL)
- [ ] Performance monitoring enabled
- [ ] Content editor training completed