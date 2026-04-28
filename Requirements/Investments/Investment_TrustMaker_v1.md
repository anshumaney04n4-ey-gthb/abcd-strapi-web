# Investments Trust Makers - Complete Schema Documentation

## Parent Content-Type: Investments Dashboard Page

**CMS Key:** `trustMakers`  
**Stored Under:** `investments_dashboard_pages` entry (same Dashboard API payload)  
**Draft & Publish:** Inherited from `investments_dashboard_pages`

---

## All Content-Type Fields (Exact Strapi Field Names)

> TrustMakers is configured as a nested field within Investments Dashboard Page and should be fetched using the same dashboard API call.

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `[cardId]` | object key | Yes | - | Keyed by banner card ID (`card-1`, `card-2`, `card-3`) |
| `heading` | string | No | `"Build on trust. Backed by RBI-regulated banks"` | Sidebar heading text |
| `subheading` | string | No | `"Every bank deposit on ABCD is protected by the DICGC..."` | Sidebar subheading text |
| `headerIconPath` | media/string | No | `/icons/secure-shield.svg` | Header icon asset path |
| `items` | component[] | Yes | - | Trust maker item entries (max 4) |
| `items[].id` | string | Yes | - | Unique item identifier |
| `items[].title` | string | Yes | - | Item title text |
| `items[].description` | string | Yes | - | Item description text |
| `items[].iconPath` | media/string | No | - | Item icon asset path |

---

## Complete JSON Structure

> **Note:** `trustMakers` is a keyed object where each key corresponds to a banner card ID from `bannerFD.cards`.  
> **Note:** This object is expected inside the dashboard page payload (`attributes.trustMakers`) returned by `/api/investments-dashboard-pages`.


```json
{
  "data": {
    "trustMakers": {
      "card-1": {
        "heading": "Build on trust. Backed by RBI-regulated banks",
        "subheading": "Every bank deposit on ABCD is protected by the DICGC, which insures up to ₹5 lakh per depositor per bank",
        "headerIconPath": "media_or_url",
        "items": [
          {
            "id": "1",
            "title": "₹5 lakh deposit insurance",
            "description": "Every bank deposit on ABCD is protected by the DICGC, which insures up to ₹5 lakh pre depositor per bank",
            "iconPath": "media_or_url"
          },
          {
            "id": "2",
            "title": "RBI regulated institutions",
            "description": "We partner only with banks and small finance banks that follow RBI's guidelines for liquidity and governance. Small finance banks operate under the same regulatory framework as larger banks, ensuring trust and compliance.",
            "iconPath": "media_or_url"
          },
          {
            "id": "3",
            "title": "Money goes direct to bank",
            "description": "Your money flows directly from your bank account to the partner bank you choose. ABCD never touches or holds your funds the fixed deposit is opened in your name.",
            "iconPath": "media_or_url"
          },
          {
            "id": "4",
            "title": "No new account needed",
            "description": "Book and manage FDs without opening a new savings account. Keep using your current bank for transactions while enjoying higher returns elsewhere.",
            "iconPath": "media_or_url"
          }
        ]
      },
      "card-2": { "...same structure as card-1..." },
      "card-3": { "...same structure as card-1..." }
    }
  }
}
```

---

## API Endpoints

### Base URL
```
/api/investments-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/investments-dashboard-pages` | Fetch dashboard entries including `trustMakers` |
| GET | `/api/investments-dashboard-pages/:id` | Fetch one dashboard entry including `trustMakers` |
| POST | `/api/investments-dashboard-pages` | Create dashboard entry with `trustMakers` |
| PUT | `/api/investments-dashboard-pages/:id` | Update `trustMakers` in dashboard entry |
| DELETE | `/api/investments-dashboard-pages/:id` | Delete dashboard entry |

### Query Parameters
```
?filters[subProduct][$eq]=fixed-deposits&
filters[partner][$eq]=default&
populate=*
```

### API Response Example (Actual Runtime Shape Expected from Dashboard API)

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "trustMakers": {
          "card-1": {
            "heading": "Build on trust. Backed by RBI-regulated banks",
            "subheading": "Every bank deposit on ABCD is protected by the DICGC, which insures up to ₹5 lakh per depositor per bank",
            "headerIconPath": "/icons/secure-shield.svg",
            "items": [
              {
                "id": "1",
                "title": "₹5 lakh deposit insurance",
                "description": "Every bank deposit on ABCD is protected by the DICGC, which insures up to ₹5 lakh per depositor per bank",
                "iconPath": "/icons/insurance-coin.svg"
              },
              {
                "id": "2",
                "title": "RBI regulated institutions",
                "description": "We partner only with banks and small finance banks that follow RBI's guidelines for liquidity and governance.",
                "iconPath": "/icons/rbi-coin.svg"
              }
            ]
          }
        }
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 1,
      "total": 1
    }
  }
}
```

### Recommended Fetch (TrustMakers via Dashboard API)

```
/api/investments-dashboard-pages?
filters[subProduct][$eq]=fixed-deposits&
filters[partner][$eq]=default&
populate=*
```

---

## Field Resolution Logic (Used in Code)

1. Card lookup key: `selectedCardId` from `bannerFD.cards[].id` (e.g. `card-1`, `card-2`, `card-3`).
2. Config resolution: `cmsContent.trustMakers[selectedCardId]` — returns `null` if no matching key.
3. Icon resolution:
   1. `headerIconPath` → `<img>` ReactNode via `headerIcon` prop
   2. `items[].iconPath` → `<img>` ReactNode via `items[].icon` prop
4. CMS merge: `deepMergeWithFallback` against `TRUST_MAKERS_CONFIG` fallback — no dedicated normalizer.
5. Data source: `trustMakers` is read from dashboard CMS payload (`attributes.trustMakers`) after standard dashboard transform.
6. Sidebar renders only when `isCardSidebarOpen && selectedCardId && trustMakersConfig` are all truthy.

---

## Defaults Summary

| Field | Default Value |
|-------|---------------|
| `heading` | `"Build on trust. Backed by RBI-regulated banks"` |
| `subheading` | `"Every bank deposit on ABCD is protected by the DICGC, which insures up to ₹5 lakh per depositor per bank"` |
| `headerIconPath` | `/icons/secure-shield.svg` |
| `items[0].iconPath` | `/icons/insurance-coin.svg` |
| `items[1].iconPath` | `/icons/rbi-coin.svg` |
| `items[2].iconPath` | `/icons/bank-coin.svg` |
| `items[3].iconPath` | `/icons/wallet.svg` |

---

## CMS Configuration: Comparison with BankDetailsSidebar

| Aspect | BankDetailsSidebar | TrustMakers |
|--------|--------------------|-------------|
| **CMS key** | `bankDetailsSidebar` | `trustMakers` |
| **Structure** | Single base object (overridden per bank via `bankMapping`) | Keyed object `{ [cardId]: config }` |
| **Sidebar open state** | `isBankSidebarOpen` | `isCardSidebarOpen` |
| **Selected entity** | `selectedBankDetailsId` | `selectedCardId` |
| **Type guard** | `hasBankDetailsSidebarConfig()` — checks 7 required keys | Null-check on `trustMakersConfig` |
| **Icon handling** | `iconSrc` → `<img>` | `iconPath` → `<img>` |
| **Action handlers** | `onOpenFd`, `onOpenRd`, `onDiscoveryClick` | `onSidebarBackClick`, `onSidebarHelpClick` |
| **Loading/error** | `isLoading`, `hasError`, `onRetry` | Not applicable (static content) |
| **useMemo returns** | `BankDetailsSidebarConfig \| Record<string, never>` | Config object \| `null` |

---

## Restrictions Summary Table

| Section | Max Items |
|---------|-----------|
| Trust Makers Entries (`card-1`, `card-2`, `card-3`) | 3 |
| Trust Makers Items per card | 4 |

---