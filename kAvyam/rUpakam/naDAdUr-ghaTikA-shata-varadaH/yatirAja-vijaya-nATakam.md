+++
title = "यति-राज-विजय-नाटकम्"
+++
<details><summary>AI Prompt</summary>

PROMPT 0:  
You are an expert Sanskrit proofreader and formatter. Your task is to process raw Sanskrit text and convert it into perfectly formatted and linguistically correct Markdown.  

Where the text provided has blocks with summary starting with मूलम्, for example `<details><summary>मूलम्</summary> ...</details>`, you should not alter text within those; but process the rest. Otherwise, fix the entire text provided.


Your entire output must be a single Markdown code block.

---

### **Part 1: Definitions and Core Principles**

#### **1. Word or Stem Boundary**

A word or stem boundary is the point where two words or stems are joined (possibly but not always involving sandhi) without a space or hyphen. It is the character sequence spanning the end of the first word and the beginning of the second.

#### **2. The Separation Principle**

The core of your task is to identify "separable" boundaries and insert the correct separator (a space or a hyphen).

The **cardinal rule** is: **Do not revert the sandhi.** You are splitting the *result* of the sandhi, not undoing it.

#### **3. The Rule of Precedence: Non-Separability is Absolute**

This is the most critical section. The rules for non-separation **always take precedence** over rules for separation.

*   **If a boundary is identified as non-separable, you MUST NOT split it for any reason, even if the words form a compound (`samāsa`).** This is a veto rule.

#### **4. Boundary Types and Examples**

**A. Non-Separable Boundaries: These MUST NOT be split.**

*   **Vowel Lengthening (dīrgha sandhi):** When two vowels merge into a single long vowel (`आ`, `ई`, `ऊ`, `ॠ`).
    *   `दया + आर्द्र → दयार्द्र`. The boundary `या` is non-separable.
    *   `अपि + इच्छा → अपीच्छा`. The boundary `पी` is non-separable.
    *   **Crucial Compound Example:** `धर्म + अर्थ → धर्मार्थ`. This is a `dīrgha sandhi` within a compound. Because the non-separation rule is absolute, this **must remain `धर्मार्थ`**, not be split into `धर्म-अर्थ`.
    *   **Error Case Study:** The input `स्वप्रकाशाद्वितीय` (from `स्वप्रकाश + अद्वितीय`) must remain `स्वप्रकाशाद्वितीय` because it is a `dīrgha sandhi`. It is incorrect to split it as `स्वप्रकाश-अद्वितीय`.

*   **Vowel Combination (guṇa/vṛddhi sandhi):** When two vowels merge into a new, single vowel (`ए`, `ओ`, `ऐ`, `औ`).
    *   `महा + उत्सव → महोत्सव`. The boundary `हो` is non-separable.
    *   `राम + इति → रामेति`. The boundary `मे` is non-separable.
    *   `सदा + एव → सदैव`. The boundary `दै` is non-separable.

**B. Separable Boundaries: These MUST be split if not vetoed by a non-separable rule.**

*   **Vowel to Semivowel (yaṇ sandhi):** The transformed semivowel (`य्` or `व्`) stays with the first word.
    *   `इति + एवम् → इत्येवम्` must be split as `इत्य् एवम्`. (The `इ` became `य्`; the `य्` is kept).
    *   `मधु + अरिः → मध्वरिः` must be split as `मध्व्-अरिः`.

*   **Visarga (`ः`) Sandhi:**
    *   `visarga` to `ो`: `रामः + अस्ति → रामोऽस्ति`. Split as `रामो ऽस्ति`. (The avagraha `ऽ` is part of the boundary).
    *   `visarga` to `र्`: `दुः + प्रकृतेः + अस्य → दुष्प्रकृतेरस्य`. Split as `दुष्प्रकृतेर् अस्य`.
    *   `visarga` to `स्/श्/ष्`: `नमः + ते → नमस्ते`. Split as `नमस् ते`.

*   **Final `म्`:** A final `म्` before a vowel is separated by a space.
    *   `फलम् + अश्नुते → फलमश्नुते`. Split as `फलम् अश्नुते`.
    *   `अर्थम् + इति  → अर्थमिति`. Split as `अर्थम् इति`.

*   **Consonant Assimilation:**
    *   `तत् + हि → तद्धि`. Split as `तद् धि`.

### **Part 2: The Rigorous Processing Workflow**

Follow these steps in strict order. **This is not a set of guidelines; it is an algorithm.**

**Step 1: Text Cleanup and Normalization**
*   Remove hard-wrapped line breaks to create continuous paragraphs.
*   Correct obvious typographical errors (e.g., a space in the middle of a word).
*   Preserve intentional styles like **bold** and *italic*.
*   Identify Sanskrit text and its script (eg. kannaDa), wrap it in `<santext script=SCRIPT_NAME>` tags, and transliterate to devanāgarī for internal processing.

**Step 2: The Core Separation Algorithm**
For each text wrapped in `<santext>` tags, iterate through every potential word boundary and apply the following logic:

1.  **First Check (The Veto):** Examine the boundary. Is it a **non-separable** `dīrgha`, `guṇa`, or `vṛddhi` sandhi?
    *   If **YES**, the Rule of Precedence applies. **Do nothing.** Do not split it. Move to the next boundary.
2.  **Second Check (Separation):** If the boundary passed the first check (i.e., it is not a non-separable vowel merger), now determine if it is one of the **separable** types defined in Part 1, Section 4.B.
    *   If **NO**, do nothing and move on.
3.  **Apply Separation:** If the boundary has been confirmed as separable, insert the correct separator:
    *   Use a **hyphen (`-`)** if the words form a compound (`samāsa`). Example: `पुण्य-पापैः`.
    *   Use a **space (` `)** for all other separable cases. Example: `इत्य् एवम्`.

After processing all boundaries, transliterate the `<santext>` contents back to the original script (e.g., kannaDa).

**Step 3: Source Error Handling**
*   **This step is distinct from sandhi separation.** It concerns fixing clear spelling or grammatical errors in the *source words themselves*.
*   If you find such an error, suggest a correction inline using the format `[[OLD|NEW]]`. Example: `[[prarabvaṁ|prārabdhaṁ]]`.

**Step 4: Final Markdown Formatting**
*   Remove the `<santext>` tags.
*   **Quotes & Mantras:** Enclose short quotes (under 5 words) in `"` and format longer quotes or mantras as blockquotes (`>`).
*   **Structure:** End verse lines with two spaces for a soft break. Separate paragraphs with a blank line.
*   **Page Numbers:** Format page numbers (e.g., `६४`) as `[[P64]]` at the precise point of the page break. This can be within a paragraph which continues to the next page.
*   **Footnotes:** Format footnotes (e.g., `*`) using Markdown's footnote syntax (`[^1]`). Place the definition at the end. Make the footnote definitions appear next to the paragraph containing the corresponding footnote reference. Ensure that footnote references are unique, reflecting the number used in the source whenever possible. For example if footnote named 1 appears in page 12, make the reference 12_1.
*   If the input contains `<details><summary>मूलम्</summary>...</details>`, preserve this structure as-is and only process the text around it; but not within it.

Are you ready?
</details>

<details><summary>AI Response Headers</summary>

[]
</details>

<details><summary>AI Prompt</summary>

PROMPT 0:  
You are an expert Sanskrit proofreader and formatter. Your task is to process raw Sanskrit text and convert it into perfectly formatted and linguistically correct Markdown.  

Where the text provided has blocks with summary starting with मूलम्, for example `<details><summary>मूलम्</summary> ...</details>`, you should not alter text within those; but process the rest. Otherwise, fix the entire text provided.


Your entire output must be a single Markdown code block.

---

### **Part 1: Definitions and Core Principles**

#### **1. Word or Stem Boundary**

A word or stem boundary is the point where two words or stems are joined (possibly but not always involving sandhi) without a space or hyphen. It is the character sequence spanning the end of the first word and the beginning of the second.

#### **2. The Separation Principle**

The core of your task is to identify "separable" boundaries and insert the correct separator (a space or a hyphen).

The **cardinal rule** is: **Do not revert the sandhi.** You are splitting the *result* of the sandhi, not undoing it.

#### **3. The Rule of Precedence: Non-Separability is Absolute**

This is the most critical section. The rules for non-separation **always take precedence** over rules for separation.

*   **If a boundary is identified as non-separable, you MUST NOT split it for any reason, even if the words form a compound (`samāsa`).** This is a veto rule.

#### **4. Boundary Types and Examples**

**A. Non-Separable Boundaries: These MUST NOT be split.**

*   **Vowel Lengthening (dīrgha sandhi):** When two vowels merge into a single long vowel (`आ`, `ई`, `ऊ`, `ॠ`).
    *   `दया + आर्द्र → दयार्द्र`. The boundary `या` is non-separable.
    *   `अपि + इच्छा → अपीच्छा`. The boundary `पी` is non-separable.
    *   **Crucial Compound Example:** `धर्म + अर्थ → धर्मार्थ`. This is a `dīrgha sandhi` within a compound. Because the non-separation rule is absolute, this **must remain `धर्मार्थ`**, not be split into `धर्म-अर्थ`.
    *   **Error Case Study:** The input `स्वप्रकाशाद्वितीय` (from `स्वप्रकाश + अद्वितीय`) must remain `स्वप्रकाशाद्वितीय` because it is a `dīrgha sandhi`. It is incorrect to split it as `स्वप्रकाश-अद्वितीय`.

*   **Vowel Combination (guṇa/vṛddhi sandhi):** When two vowels merge into a new, single vowel (`ए`, `ओ`, `ऐ`, `औ`).
    *   `महा + उत्सव → महोत्सव`. The boundary `हो` is non-separable.
    *   `राम + इति → रामेति`. The boundary `मे` is non-separable.
    *   `सदा + एव → सदैव`. The boundary `दै` is non-separable.

**B. Separable Boundaries: These MUST be split if not vetoed by a non-separable rule.**

*   **Vowel to Semivowel (yaṇ sandhi):** The transformed semivowel (`य्` or `व्`) stays with the first word.
    *   `इति + एवम् → इत्येवम्` must be split as `इत्य् एवम्`. (The `इ` became `य्`; the `य्` is kept).
    *   `मधु + अरिः → मध्वरिः` must be split as `मध्व्-अरिः`.

*   **Visarga (`ः`) Sandhi:**
    *   `visarga` to `ो`: `रामः + अस्ति → रामोऽस्ति`. Split as `रामो ऽस्ति`. (The avagraha `ऽ` is part of the boundary).
    *   `visarga` to `र्`: `दुः + प्रकृतेः + अस्य → दुष्प्रकृतेरस्य`. Split as `दुष्प्रकृतेर् अस्य`.
    *   `visarga` to `स्/श्/ष्`: `नमः + ते → नमस्ते`. Split as `नमस् ते`.

*   **Final `म्`:** A final `म्` before a vowel is separated by a space.
    *   `फलम् + अश्नुते → फलमश्नुते`. Split as `फलम् अश्नुते`.
    *   `अर्थम् + इति  → अर्थमिति`. Split as `अर्थम् इति`.

*   **Consonant Assimilation:**
    *   `तत् + हि → तद्धि`. Split as `तद् धि`.

### **Part 2: The Rigorous Processing Workflow**

Follow these steps in strict order. **This is not a set of guidelines; it is an algorithm.**

**Step 1: Text Cleanup and Normalization**
*   Remove hard-wrapped line breaks to create continuous paragraphs.
*   Correct obvious typographical errors (e.g., a space in the middle of a word).
*   Preserve intentional styles like **bold** and *italic*.
*   Identify Sanskrit text and its script (eg. kannaDa), wrap it in `<santext script=SCRIPT_NAME>` tags, and transliterate to devanāgarī for internal processing.

**Step 2: The Core Separation Algorithm**
For each text wrapped in `<santext>` tags, iterate through every potential word boundary and apply the following logic:

1.  **First Check (The Veto):** Examine the boundary. Is it a **non-separable** `dīrgha`, `guṇa`, or `vṛddhi` sandhi?
    *   If **YES**, the Rule of Precedence applies. **Do nothing.** Do not split it. Move to the next boundary.
2.  **Second Check (Separation):** If the boundary passed the first check (i.e., it is not a non-separable vowel merger), now determine if it is one of the **separable** types defined in Part 1, Section 4.B.
    *   If **NO**, do nothing and move on.
3.  **Apply Separation:** If the boundary has been confirmed as separable, insert the correct separator:
    *   Use a **hyphen (`-`)** if the words form a compound (`samāsa`). Example: `पुण्य-पापैः`.
    *   Use a **space (` `)** for all other separable cases. Example: `इत्य् एवम्`.

After processing all boundaries, transliterate the `<santext>` contents back to the original script (e.g., kannaDa).

**Step 3: Source Error Handling**
*   **This step is distinct from sandhi separation.** It concerns fixing clear spelling or grammatical errors in the *source words themselves*.
*   If you find such an error, suggest a correction inline using the format `[[OLD|NEW]]`. Example: `[[prarabvaṁ|prārabdhaṁ]]`.

**Step 4: Final Markdown Formatting**
*   Remove the `<santext>` tags.
*   **Quotes & Mantras:** Enclose short quotes (under 5 words) in `"` and format longer quotes or mantras as blockquotes (`>`).
*   **Structure:** End verse lines with two spaces for a soft break. Separate paragraphs with a blank line.
*   **Page Numbers:** Format page numbers (e.g., `६४`) as `[[P64]]` at the precise point of the page break. This can be within a paragraph which continues to the next page.
*   **Footnotes:** Format footnotes (e.g., `*`) using Markdown's footnote syntax (`[^1]`). Place the definition at the end. Make the footnote definitions appear next to the paragraph containing the corresponding footnote reference. Ensure that footnote references are unique, reflecting the number used in the source whenever possible. For example if footnote named 1 appears in page 12, make the reference 12_1.
*   If the input contains `<details><summary>मूलम्</summary>...</details>`, preserve this structure as-is and only process the text around it; but not within it.

Are you ready?
</details>

<details><summary>AI Response Headers</summary>

[
  {
    "pages_96_to_100": {
      "sdk_http_response": {
        "headers": {
          "x-gemini-service-tier": "standard",
          "content-type": "application/json; charset=UTF-8",
          "vary": "Origin, X-Origin, Referer",
          "content-encoding": "gzip",
          "date": "Sun, 06 Sep 2026 16:37:30 GMT",
          "server": "scaffolding on HTTPServer2",
          "x-xss-protection": "0",
          "x-frame-options": "SAMEORIGIN",
          "x-content-type-options": "nosniff",
          "server-timing": "gfet4t7; dur=166944",
          "alt-svc": "h3=\":443\"; ma=2592000,h3-29=\":443\"; ma=2592000",
          "transfer-encoding": "chunked"
        }
      },
      "candidates": [
        {
          "content": {
            "role": "model"
          },
          "finish_reason": "STOP",
          "index": 0
        }
      ],
      "model_version": "gemini-3.5-flash",
      "response_id": "JJadapjPEqvfg8UPpbXH-Qc",
      "usage_metadata": {
        "candidates_token_count": 3124,
        "prompt_token_count": 4522,
        "prompt_tokens_details": [
          {
            "modality": "TEXT",
            "token_count": 1822
          },
          {
            "modality": "IMAGE",
            "token_count": 2700
          }
        ],
        "thoughts_token_count": 36282,
        "total_token_count": 43928
      }
    }
  },
  {
    "pages_101_to_105": {
      "sdk_http_response": {
        "headers": {
          "x-gemini-service-tier": "standard",
          "content-type": "application/json; charset=UTF-8",
          "vary": "Origin, X-Origin, Referer",
          "content-encoding": "gzip",
          "date": "Sun, 06 Sep 2026 16:38:35 GMT",
          "server": "scaffolding on HTTPServer2",
          "x-xss-protection": "0",
          "x-frame-options": "SAMEORIGIN",
          "x-content-type-options": "nosniff",
          "server-timing": "gfet4t7; dur=61743",
          "alt-svc": "h3=\":443\"; ma=2592000,h3-29=\":443\"; ma=2592000",
          "transfer-encoding": "chunked"
        }
      },
      "candidates": [
        {
          "content": {
            "role": "model"
          },
          "finish_reason": "STOP",
          "index": 0
        }
      ],
      "model_version": "gemini-3.5-flash",
      "response_id": "zpadarbLC-ijqfkPpKm3wQQ",
      "usage_metadata": {
        "candidates_token_count": 1,
        "prompt_token_count": 46625,
        "prompt_tokens_details": [
          {
            "modality": "TEXT",
            "token_count": 41225
          },
          {
            "modality": "IMAGE",
            "token_count": 5400
          }
        ],
        "thoughts_token_count": 14324,
        "total_token_count": 60950
      }
    }
  },
  {
    "pages_106_to_110": {
      "sdk_http_response": {
        "headers": {
          "x-gemini-service-tier": "standard",
          "content-type": "application/json; charset=UTF-8",
          "vary": "Origin, X-Origin, Referer",
          "content-encoding": "gzip",
          "date": "Sun, 06 Sep 2026 16:39:45 GMT",
          "server": "scaffolding on HTTPServer2",
          "x-xss-protection": "0",
          "x-frame-options": "SAMEORIGIN",
          "x-content-type-options": "nosniff",
          "server-timing": "gfet4t7; dur=67257",
          "alt-svc": "h3=\":443\"; ma=2592000,h3-29=\":443\"; ma=2592000",
          "transfer-encoding": "chunked"
        }
      },
      "candidates": [
        {
          "content": {
            "role": "model"
          },
          "finish_reason": "STOP",
          "index": 0
        }
      ],
      "model_version": "gemini-3.5-flash",
      "response_id": "D5edaoCIF-6_g8UP3NWi0Ao",
      "usage_metadata": {
        "cache_tokens_details": [
          {
            "modality": "TEXT",
            "token_count": 38942
          },
          {
            "modality": "IMAGE",
            "token_count": 5678
          }
        ],
        "cached_content_token_count": 44620,
        "candidates_token_count": 3209,
        "prompt_token_count": 63649,
        "prompt_tokens_details": [
          {
            "modality": "IMAGE",
            "token_count": 8100
          },
          {
            "modality": "TEXT",
            "token_count": 55549
          }
        ],
        "thoughts_token_count": 13783,
        "total_token_count": 80641
      }
    }
  },
  {
    "pages_111_to_115": {
      "sdk_http_response": {
        "headers": {
          "x-gemini-service-tier": "standard",
          "content-type": "application/json; charset=UTF-8",
          "vary": "Origin, X-Origin, Referer",
          "content-encoding": "gzip",
          "date": "Sun, 06 Sep 2026 16:40:51 GMT",
          "server": "scaffolding on HTTPServer2",
          "x-xss-protection": "0",
          "x-frame-options": "SAMEORIGIN",
          "x-content-type-options": "nosniff",
          "server-timing": "gfet4t7; dur=62371",
          "alt-svc": "h3=\":443\"; ma=2592000,h3-29=\":443\"; ma=2592000",
          "transfer-encoding": "chunked"
        }
      },
      "candidates": [
        {
          "content": {
            "role": "model"
          },
          "finish_reason": "STOP",
          "index": 0
        }
      ],
      "model_version": "gemini-3.5-flash",
      "response_id": "VZedatfSM5y0g8UPkLKn0Qg",
      "usage_metadata": {
        "cache_tokens_details": [
          {
            "modality": "TEXT",
            "token_count": 52957
          },
          {
            "modality": "IMAGE",
            "token_count": 7883
          }
        ],
        "cached_content_token_count": 60840,
        "candidates_token_count": 3239,
        "prompt_token_count": 83348,
        "prompt_tokens_details": [
          {
            "modality": "TEXT",
            "token_count": 72548
          },
          {
            "modality": "IMAGE",
            "token_count": 10800
          }
        ],
        "thoughts_token_count": 12526,
        "total_token_count": 99113
      }
    }
  },
  {
    "pages_116_to_120": {
      "sdk_http_response": {
        "headers": {
          "x-gemini-service-tier": "standard",
          "content-type": "application/json; charset=UTF-8",
          "vary": "Origin, X-Origin, Referer",
          "content-encoding": "gzip",
          "date": "Sun, 06 Sep 2026 16:41:47 GMT",
          "server": "scaffolding on HTTPServer2",
          "x-xss-protection": "0",
          "x-frame-options": "SAMEORIGIN",
          "x-content-type-options": "nosniff",
          "server-timing": "gfet4t7; dur=52464",
          "alt-svc": "h3=\":443\"; ma=2592000,h3-29=\":443\"; ma=2592000",
          "transfer-encoding": "chunked"
        }
      },
      "candidates": [
        {
          "content": {
            "role": "model"
          },
          "finish_reason": "STOP",
          "index": 0
        }
      ],
      "model_version": "gemini-3.5-flash",
      "response_id": "l5edatrIEa2yg8UPwuTxuQg",
      "usage_metadata": {
        "cache_tokens_details": [
          {
            "modality": "TEXT",
            "token_count": 70354
          },
          {
            "modality": "IMAGE",
            "token_count": 10754
          }
        ],
        "cached_content_token_count": 81108,
        "candidates_token_count": 2878,
        "prompt_token_count": 101817,
        "prompt_tokens_details": [
          {
            "modality": "IMAGE",
            "token_count": 13500
          },
          {
            "modality": "TEXT",
            "token_count": 88317
          }
        ],
        "thoughts_token_count": 10741,
        "total_token_count": 115436
      }
    }
  },
  {
    "pages_121_to_125": {
      "sdk_http_response": {
        "headers": {
          "x-gemini-service-tier": "standard",
          "content-type": "application/json; charset=UTF-8",
          "vary": "Origin, X-Origin, Referer",
          "content-encoding": "gzip",
          "date": "Sun, 06 Sep 2026 16:42:34 GMT",
          "server": "scaffolding on HTTPServer2",
          "x-xss-protection": "0",
          "x-frame-options": "SAMEORIGIN",
          "x-content-type-options": "nosniff",
          "server-timing": "gfet4t7; dur=44591",
          "alt-svc": "h3=\":443\"; ma=2592000,h3-29=\":443\"; ma=2592000",
          "transfer-encoding": "chunked"
        }
      },
      "candidates": [
        {
          "content": {
            "role": "model"
          },
          "finish_reason": "STOP",
          "index": 0
        }
      ],
      "model_version": "gemini-3.5-flash",
      "response_id": "zpedaqPfOYLCg8UPwNyB0Qg",
      "usage_metadata": {
        "cache_tokens_details": [
          {
            "modality": "TEXT",
            "token_count": 87457
          },
          {
            "modality": "IMAGE",
            "token_count": 13897
          }
        ],
        "cached_content_token_count": 101354,
        "candidates_token_count": 2676,
        "prompt_token_count": 118147,
        "prompt_tokens_details": [
          {
            "modality": "IMAGE",
            "token_count": 16200
          },
          {
            "modality": "TEXT",
            "token_count": 101947
          }
        ],
        "thoughts_token_count": 9323,
        "total_token_count": 130146
      }
    }
  }
]
</details>



[[P1]]

SRI VAISHNAVA SAMPRADAYA GRANTHAMALA—No. 7

**General Editor:—Prof. J. CHENNA REDDY, M.A., B.Ed.**  
*Director, S. V. O. Institute, Tirupati.*

# Yathiraja Vijaya Natakam
### (VEDANTHA VILASAM)
#### OF
### Sri Ghatikasatam Vatsya Varadacharya
#### (GHATIKASATAM AMMAL)

**WITH A RARE COMMENTARY "RATNADIPIKA"**  
*CRITICALLY EDITED WITH NOTES, APPENDICES ETC.*

#### BY
Sahitya, Nyaya, Vedanta Siromani Vidwan  
**Sri T. K. V. N. SUDARSANACHARYA,**  
*Formerly Editor in charge of Sri Vaishnava Sampradaya Granthamala S.V.O.I., and Head of Dept. of Nyaya in S.V.O. College, Tirupati.*

PUBLISHED BY  
**TIRUMALA-TIRUPATI DEVASTHANAMS**  
**TIRUPATI**

---

[[P2]]

339

---

[[P3]]

श्रीवैष्णव-सम्प्रदाय-ग्रन्थमाला — [[मं.|सं.]] ७

**साधारण-सम्पादकः — श्री. जी. चेन्नारेड्डी, एम्. ए., [[बि. इ, डि.|बि. एड्.]]**  
*श्रीवेङ्कटेश्वर-प्राच्य-शोधनालयाध्यक्षः, तिरुपतिः।*

### वेदान्त-विलासापर-नामधेयम्
# यतिराज-विजयम् — नाटकम्

#### प्रणेतारः —
**श्री-घटिकाशत-"अम्माळ्"-अपर-नामधेयाः**  
**श्रीवत्स-वरदाचार्याः**

#### सम्पादकः —
*(व्याख्यान-अनुबन्ध-[[टिप्पण्यादिभिसहितं|टिप्पण्यादि-सहितम्]])*  
साहित्य-न्याय-वेदान्त-शिरोमणिः  
उभय-वेदान्त-विद्वान्  
**ति. कु. वें. न. सुदर्शनाचार्यः**  
*श्रीवेङ्कटेश्वर-प्राच्य-शालायां न्याय-शास्त्र-प्रधानाचार्यः*  
**श्रीपद-पुरी**

**१९५६**

---

[[P4]]

सर्व-स्वाम्यं ति. ति. देवस्थानाधीनम्।

**प्रथमं मुद्रणम्**

तिरुपति-नगरे  
तिरुमल-तिरुपति-देवस्थान-मुद्रणालये  
मुद्रितम्।

---

[[P5]]

# FOREWORD

I have great pleasure in introducing to the public this valuable critical edition of 'Sri Yatirajavijaya' (Vedantavilasa) a philosophical allegorical play written by the wellknown Vidvatkavi Vatsya Varadacharya (Ghatikasatam Ammal) of Kancheepuram. An elaborate Introduction, Notes and Appendices etc., are the notable features of the edition added by our learned Vidvan Sri T. K. V. N. Sudarsanacharya Siromani who was the Editor in charge of Standard Religious Texts, and it is published as the 7th in series of Sri Vaishnava Granthamala under the auspices of the Sri Venkatesvara Oriental Institute, Tirupati.

The Editor a versatile scholar brought out this very attractive and valuable edition pooling up all the available information about the text from every [[accessable|accessible]] source. In his Sanskrit introduction he discussed all the fundamental principles of this drama in its various aspects and tried to present a clear and comparative picture of different schools of religious and philosophical thought as revealed by great and revered Acharyas. He finally established the Visishtadvaita theory of 'Vishnuparamya' aimed at by the author of the play. The ripe arguments of Sri Sudarsanacharya in determining 'Vedamauli' as the chief hero of the play on the basis of 'Sachivayattasidditva' as the result of all the actions of Yatiraja finally go to help realisation of the object in favour of Vedamauli, and in establishing Bhaktirasa as the chief sentiment of the play after examining the position of Vira and Santa sentiments, carefully defining the connotation of Bhaktirasa so as to form an integral part of Sringara without prejudice to the [[regid|rigid]] precepts of Alankarikas like Dhananjaya and Dhanika in Dasarupaka, afford clear evidence to his critical outlook and deep erudition.

In Sanskrit literature the allegorical plays have occupied a unique place. The elements of allegorical expression are found even in Vedic literature, though they have taken a definite shape in the Mahabharatha and several of the great Puranas. The episode of Puranjanopakhyana in Srimadbhagavatha is an outstanding



[[Pii]]

example of the type on the model of which a famous allegorical play "Prabodhachandrodaya" was written by Sri Krishna Misra. This play is the source of the entire similar literature in Sanskrit after Sri Krishna Misra.

A style that abounds in intricate and obscure figures of speech, and in thoughts couched in unintelligible phraseology is any day unsuitable for adoption in writing a stage drama intended to provide entertainment to all classes of people. That might be well appreciated after a calm and scholarly reading. The allegorical way of expression is much less suited to a play. But as we see in Sanskrit literature, majority of the plays written by the famous authors are not free from the above defects. Hence the Sanskrit play afforded a laborious study rather than an entertainment on the stage. So the allegorical drama also was equally read and enjoyed by profound scholars with a philosophical bent of mind and gained popularity.

In an allegorical play all the human qualities classed as virtues come in conflict with the opposite set of qualities—the vices—of course both personified and displayed as characters of the play. In the end the virtue prevails gaining a decisive victory over the vice.

Sri Krishna Misra was an ascetic of the Paramahamsa order. He was the follower of Sri Sankara Bhagavadpadacharya. His Prabodhachandrodaya in six acts defends Advaita Philosophy of Vishnu doctrine combining Vedanta with Vishnuism from the onslaughts of Buddhism, Jainism and Sakteyam. As Prabodhachandrodaya depicts Monism (अद्वैत), Sankalpasuryodaya of Sri Vedantha Desika and Yatirajavijaya establish qualified Monism (विशिष्टाद्वैत) on the lines propounded by Sri Bhagavad Ramanuja.

The philosophical theme in this type of play is that the Supreme Soul (परमात्मन्) gets encompassed by Illusion (माया) and the Soul (आत्मन्) is depicted in Plurality (संसार) by evil characters like Confusion (मोह), Vanity (दम्भ) and False Conception (महामोह) etc., The virtuous characters like Discrimination (विवेक), Spiritual Knowledge (विद्या) and Faith (श्रद्धा) etc., help the struggling Soul (आत्मन्) in obtaining final Emancipation (मोक्ष) when Knowledge (प्रबोध) dawns on him. In the end Trust (भक्ति) in Vishnu applauds the result. This is how Sri Krishna Misra presents the doctrine of Advaita.

---

[[Piii]]

Sri Venkatanatha in his Sankalpasuryodaya adopted the same form of play as of Sri Krishna Misra. But the content and manner of treatment of the subject matter are different. His main mission was to interpret the philosophical doctrines in conformity with those of Bhagavad Ramanuja. The religious fervour and the long and prosaic prologue have made the play less popular among the scholars of non-Vaishnavaite sects. The style of Prabodhachandrodaya is lucid and simple.

Yatirajavijaya of Vatsya Varadacharya occupies an exemplary place in Sanskrit philosophical literature. The conflict here is not between two sets of human qualities, but it is between the Visishtadvaita school of thought on one side and all other schools of thought on the other and the above mentioned qualities have merely played a secondary role. The author appears to have a thorough insight into all the Darsanas in circulation at that time and also the interpretations of the Acharyas of all the sects. Arguments and counter arguments of a very high order are advanced and eventually the doctrine of qualified Monism as preached by Bhagavad Ramanuja is established after proving that all other schools have no sustaining essence in them.

Tirupati.  
20-10 '56

**J. CHENNA REDDY**  
*Director.*

---

[[P1]]

## श्रीरस्तु
## श्रीमते वेङ्कटेशाय नमः
# प्रस्तावना

> आङ्गिकं भुवनं यस्य वाचिकं वेद-वाङ्मयम् ।  
> दश-रूप-धरं देवं श्री-निधिं तम् उपास्महे ॥  

अखिल-भुवन-जन्म-स्थेम-भङ्गादि-लीलास्य विनत-विविध-भूत-व्रात-रक्षैक-दीक्षस्य श्रुति-शिरसि विदीप्तस्य हेयप्रत्यनीकासंख्येय-कल्याण-गुण-गणाकरस्य परस्य ब्रह्मणः पुरुषोत्तमस्य श्रीनिवासस्य परम-तत्त्व-प्रकाशकं वेदान्त-विलासापर-नामधेयं मृदु-मधुर-मञ्जुलं यतिराज-विजय-नाटकम् इदम् — श्रीमत्-श्रीवेङ्कटेश्वर-प्राच्य-विद्या-परिशोधनालय-प्रथितायां श्रीवैष्णव-सम्प्रदाय-ग्रन्थमालायां सप्तमं प्रसूनम्।

ललितोचित-सन्निवेश-रम्यया काव्य-सरण्या, तत्रापि, आबाल-सुलभया दृश्य-रूपक-पद्धत्या च महा-प्राज्ञानाम् अपि दुरुहान् श्रुति-सिद्धान्त-रहस्य-भूतान् वेदान्त-सिद्धान्तान् परम-पामराणामम् अपि करतलामलकयति [[नाटकमिटमिति|नाटकम् इदम् इति]] महद् इदं प्रमोद-स्थानम्।

### धर्मप्रबोधने नाटकानां स्थानम्

विदित-चरम् एव हीदं सर्वेषामम् अपि विपश्चिद्-अपश्चिमानां यत्, शब्द-प्रधानेभ्यः प्रभु-सम्मतेभ्यो वेदेभ्यः, अर्थ-प्रधानेभ्यो मित्र-सम्मतेभ्यश् च पुराणेभ्यः, ललित-ललितया विलास-विक्रियया सर्वेषामम् अपि प्राणिनां निसर्ग-सम्प्रेयांसि मनांसि रञ्जयन्ती व्यङ्ग्य-प्रधाना कान्ता-सम्मितेव काव्य-श्रीः — कर्तव्येषु सत्सु कार्येषु प्रवर्तयति, निवर्तयति च अकर्तव्येभ्यो ऽसत्कार्येभ्यः सर्वान् अपि जनान् इति। तत्रापि पण्डितास्वादैक-विषयेभ्यः श्रव्य-काव्येभ्यः, निपुण-नट-चेष्टया समुत्तम्भितानि सकल-प्राणि-हृदयङ्गमानि दृश्य-काव्यानि चारुतराणि। अत एव “काव्येषु नाटकं रम्यम्”, “नाटकान्तं कवित्वम्” इत्यादयो महतां श्री-सूक्तयो बह्व्यो विराजन्ते।

वेद-स्मृति-पुराण-इतिहासादिष्व् इव [[भारतीयेषु|भारतीयेषु]] काव्य-नाटकादिष्व् अपि धर्म-प्रबोधनम् एव प्रधानं कृत्यम्। तथा सति सुभग-रमणीयया सरण्या आध्यात्मिक-परम-

---

[[P2]]

तत्त्व-प्रबोधकं नाटकम् इदं धर्म-प्रबोधनस्य परां कोटिम् आटीकत इति, यथावस्थितं अतिरोहितं च तत्त्वम् इदम्।

### आध्यात्मिक-नाटकानि (Allegorical Plays)

भारतीय-नाटक-प्रक्रिया चेयम् अनादि-निधना, ऋग्वेदीय-यम-यमी-संवादम् आरभ्य प्रवर्तते। एवम् इयम् आध्यात्मिक-नाटक-प्रक्रियापि समुल्लसति भृशम् अनादि-सिद्धतयैव। जन्तुषु, पुरुषस्य स्वभाव-गुणादिषु च मनुष्यत्वम् आरोप्य तानि वस्तूनि पात्रीकृत्य प्रथितानि नाटकानि — आध्यात्मिक-नाटकानि। एतेषाम् आङ्ग्ल-भाषायां (Allegorical Plays) इति व्यवहारः। तानीमानि नाटकानि वेद-कालाद् आरभ्यैव प्रसिद्धानि वर्तन्ते। वाक्-प्राण-इन्द्रियादीनां सम्भाषण-विवादादिकं वेदे समुपवर्ण्यते।

तद्यथा —

> “वाक् च वै मनश्चाहेताम्। अहं देवेभ्यो हव्यं वहामीति वागब्रवीत्, अहं देवेभ्य इति मनः। तौ प्रजापतिं प्रष्टुमैताम्। सोऽब्रवीत् प्रजापतिर् — दूत एव त्वं मनसोऽसि। यद् हि मनसा ध्यायति, तद् वाचा वदति, तदनुकृतं तुभ्यम्। न वाचा जुह्वन्त्य् अब्रवीत्। तस्मान् मनसा प्रजापतये जुह्वति” इति कृष्णयजुर्वेदे (२-५-११-४)

बृहदारण्यकोपनिषदि च इयं कथा समुपवर्ण्यते —

> “ते हेमे प्राणा अहंश्रेयसे विवदमाना ब्रह्म जग्मुः। तद् धोचुः, को नो वसिष्ठ इति। तद् धोवाच। यस्मिन् व उत्क्रान्ते इदं शरीरं पापीयो मन्यते, स वो वसिष्ठ इति ॥ ७ ॥
> 
> वाग् घोच्चक्राम, सा संवत्सरं प्रोष्यागत्योवाच। कथम् अशकत मद्-ऋते जीवितुम् इति। ते होचुः, यथाकलाः, अवदन्तो वाचा, प्राणन्तः प्राणेन, पश्यन्तश् चक्षुषा, शृण्वन्तः श्रोत्रेण, विद्वांसो मनसा, प्रजायमाना रेतसैवम् अजीविष्मेति। प्रविवेश ह वाक् ॥ ८ ॥
> 
> चक्षुर् होच्चक्राम, तत्-संवत्सरं प्रोष्यागत्योवाच। कथम् अशकत मद्-ऋते जीवितुम् इति। ते होचुर् यथान्धाः। अपश्यन्तश् चक्षुषा, प्राणन्तः प्राणेन, वदन्तो वाचा, शृण्वन्तः श्रोत्रेण,

---

[[P3]]

> विद्वांसो मनसा, प्रजायमाना रेतसैवम् अजीविष्मेति। प्रविवेश चक्षुः ॥ ९ ॥
> 
> श्रोत्रं होच्चक्राम, तत्-संवत्सरं प्रोष्यागत्योवाच, कथम् अशकत मद्-ऋते जीवितुम् इति। ते होचुर् यथा-बधिराः, अशृण्वन्तः श्रोत्रेण, प्राणन्तः प्राणेन, वदन्तो वाचा, पश्यन्तश् चक्षुषा, विद्वांसो मनसा, प्रजायमाना रेतसैवम् अजीविष्मेति। प्रविवेश श्रोत्रम् ॥ १० ॥
> 
> मनो होच्चक्राम, तत्-संवत्सरं प्रोष्यागत्योवाच। कथम् अशकत मद्-ऋते जीवितुम् इति। ते होचुर् यथा-मुग्धाः, अविद्वांसो मनसा, प्राणन्तः प्राणेन, वदन्तो वाचा, पश्यन्तश् चक्षुषा, शृण्वन्तः श्रोत्रेण, प्रजायमाना रेतसैवम् अजीविष्मेति। प्रविवेश ह मनः ॥ ११ ॥
> 
> रेतो होच्चक्राम। तत्-संवत्सरं प्रोष्यागत्योवाच। कथम् अशकत मद्-ऋते जीवितुम् इति। ते होचुर् यथा क्लीबाः। अप्रजायमाना रेतसा, प्राणन्तः प्राणेन, वदन्तो वाचा, पश्यन्तश् चक्षुषा, शृण्वन्तः श्रोत्रेण, विद्वांसो मनसा एवम् अजीविष्मेति। प्रविवेश रेतः ॥ १२ ॥
> 
> अथ ह प्राण उत्क्रमिष्यन् यथा महा-सुहयः सैन्धवः पड्वीश-शङ्कून् संवृहेद् एवम् हैवैमान् प्राणान् संववहे। ते होचुर् मा भगव उत्क्रमीः, नैव शक्ष्यामस् त्वद्-ऋते जीवितुम् इति। तस्यो मेव अस्मिन् कुरुतेति तथैति ॥ १३ ॥
> 
> सा ह वाग् उवाच, यद् वा अहं वसिष्ठास्मि, त्वं तद्-वसिष्ठो ऽसीति। यद् वा अहं प्रतिष्ठास्मि त्वं तत्-प्रतिष्ठो ऽसीति चक्षुः। यद् वा अहं [[सम्पदम्सि|सम्पद् अस्मि]] त्वं तत्-सम्पद् असीति श्रोत्रम्। यद् वा अहम् आयतनम् अस्मि, त्वं तद्-आयतनम् असीति मनः। यद् वा अहं प्रजातिर् अस्मि त्वं तत्-प्रजातिर् असीति रेतः ॥ १४ ॥” इति।

पञ्चतन्त्रादि-कथासु मृगा मनुष्यत्वेनारोपिताः मनुष्यवद्-व्यवहार-पथे स्थापिताः। अश्वघोषस्य शारिपुत्र-प्रकरणे ऽपि, बुद्धिः, कीर्तिः, धृतिः — इत्यादयो मनुष्यत्वेन रूपिता व्यवहार-पदे व्यवस्थापिताः। अन्ते च बुद्धः साक्षात्करोति। इमां प्रक्रियां [[स्वीचके|स्वीचक्रे]] कवि-कर्णपूरः स्वकीये चैतन्य-चन्द्रोदये। तत्र चैतन्यम् एव धत्ते बुद्धस्य भूमिकाम्। एतद्-दर्शीकृत्य तद्-अनन्तर-कालिका अनेके कवि-तल्लजाः आध्यात्मिक-काव्यानि प्रजानां सुलभ-सुबोध-बोधनाय विचरयामासुः।



[[P4]]

### प्रबोधचन्द्रोदयः — तस्य वैशिष्ट्यं

एवं प्रवृत्तेषु आध्यात्मिक-नाटकेषु श्रीकृष्णमिश्र-प्रणीतं प्रबोधचन्द्रोदयं नाम नाटकं प्रधान-स्थानम् अलङ्करोति।

तत्र-भवान् महा-प्राज्ञः वश्यवाक् च श्रीकृष्णमिश्र-यतिः, [[अत्यद्भूतावहेण|अत्यद्भुतावहेण]] प्रसन्न-गम्भीरं [[नाटकमिटं|नाटकम् इदं]], इतर-मत-निरसन-पूर्वकं विष्णुपारम्य-वाद्य्-अद्वैत-सिद्धान्त-व्यवस्थापनाय विरचयामास; आवर्जयामास च सर्वेषां दार्शनिकानां दृष्टिं स्वसिद्धान्त-स्थापनार्थं एतादृश-कलित-ग्रन्थ-विरचनाय। एवंविध-आध्यात्मिक-परिपक्व-नाटक-निर्माणस्य मार्गदर्शी श्रीमान् श्रीकृष्णमिश्र-यतिर् एवेति अतिरोहितं विमर्शकानाम्।

“अत्र नायको विवेकः, देव्यौ च मतिः, उपनिषच् च। वस्तु-विचारः — सेना-नायकः। तस्य सहायाः — शान्ति-करुणा-श्रद्धा-मैत्री-क्षमा-सन्तोष-वेराग्य-निदिध्यासनादयः। प्रति-नायकः — महा-मोहः। तस्य सहचारिणी — मिथ्या-दृष्टिः। सेना-नायकः — कामः, तस्य सहायाः — क्रोध-लोभ-दम्भ-अहङ्कारादयः। कामस्य रतिः, क्रोधस्य हिंसा, लोभस्य तृष्णा चेति पत्न्यः। चार्वाक-भिक्षु-क्षपणक-कापालिकादयश् च अस्य परिपोषकाः। कामादीनां विवेकादीनां च पिता मनः।

महा-प्रभाव-शालिन्या विष्णु-भक्तेर् अनुग्रहे सुसम्पन्ने, वस्तु-विचारेण कामे निहते, क्षमया च क्रोध-पारुष्य-हिंसादिषु, निहतेषु सन्तोषेण च लोभ-तृष्णा-दैन्यानृत-पैशुन्य-वाक्-स्तेय-आत्मभरि-महादिषु, अनसूयया च मात्सर्ये, परोत्कर्ष-भावनया च मदे निहते, महा-मोहः योगोपसर्गैः सह निलीनः विवेकस्य महाराजस्य विजयः सुसम्पन्नः।

ततः पुत्र-पौत्रादि-व्यसन-जनित-शोकावेगेन खिन्ने मनसि, तत्-सहायेन सङ्कल्पेन, विष्णु-भक्ति-प्रचोदितया देव्या सरस्वत्या च वैराग्यं तस्य उत्पादितम्। विकारे च शान्ते, हरिं ब्रह्म वा प्रपन्नं मनः। निवृत्तिश् च पत्नीत्वेन परिगृहीता। शम-दम-सन्तोषादिषु पुत्रेषु, यम-नियमादिषु अमात्येषु उपचरत्सु, उपनिषद्-देवी-सहायः विवेकः यौवराज्ये अभिषिक्तः, देव्याः सरस्वत्या उपदेशेन वृद्ध-महाराजेन मनसा। ततश् च विवेकेन उपनिषद्-देव्यां प्रबोधचन्द्रः उत्पादितः। पुरुषस्य च परब्रह्म-तादात्म्यं [[“तत्त्वमस्या” दि|“तत्त्वमस्य्” आदि]] श्रुति-शिरः-प्रतिपादितं सुसम्पन्नं विष्णु-भक्ति-प्रसादतः। ततो जीवन्मुक्तिः सम्प्राप्ता।”

---

[[P5]]

इति परम-सुभगया शैल्या स्व-सिद्धान्तं पण्डित-पामर-हृदयङ्गमं समुपवर्णयामास सुप्रतिभावान् सुनिपुणः चतुर-पण्डित-कवि-मण्डली-शिखामणिश् च श्रीमान् कृष्णमिश्र-यतिः प्रबोधचन्द्रोदये। अत्र षडङ्का विद्यन्ते।

### सङ्कल्पसूर्योदयः — तस्य वैशिष्ट्यं च

ततः, कवि-कथक-कण्ठीरवैः विश्वामित्र-गोत्र-भूषणैः [[उज्झितप्रतिभाप्रभावविनिर्जितसकलकथकमतैः|उज्ज्वल-प्रतिभा-प्रभाव-विनिर्जित-सकल-कथक-मतैः]] श्रीमद्भिः [[वेदान्तचार्यैः|वेदान्ताचार्यैः]], एतत्-नाटक-च्छाययैव स्व-सिद्धान्तं व्यवस्थापयितुं अन्वग्राहि, [[अतिप्रौढसन्दर्भ|अतिप्रौढ-सन्दर्भं]] लोकोत्तर-गुणोत्तरं सङ्कल्प-सूर्योदय-नाम महा-नाटकं दशाङ्क-परिकर्मितं सकल-सहृदय-हृदय-पुण्डरीक-समुन्मेष-[[सम्पत्सवस्वम्|सम्पत्-सर्वस्वम्]]।

अत्रेदम् ऐतिह्यम् आविशन्ति —

“कदाचन कृष्णमिश्र-नामा गौडो महा-विद्वान् राढामदेशाच् छ्रीरङ्गनगरम् आगतो गुरूत्तमैर् [[वदमानो|विवदमानो]] वादे च पराजितः, “मदीयः प्रबोधचन्द्रोदयो विलोक्यताम्” इति जगाद। “तर्हि, सङ्कल्प-सूर्योदयो ऽपि [[श्नो|श्वो]] भवद्भिर् अवलोक्यताम्” इति गुरुभिर् अपि प्रत्युक्तस् तथेति प्रतिपाद्य निज-मुदवासं प्रति प्रयतौ। प्रभाते च सो ऽपि रङ्गनाथ-स्थानम् आगतः, चन्द्रोदयं दर्शयन्, सङ्कल्प-सूर्योदयाविर्भाव-विजृम्भणेन विस्मितः, तत्-माहात्म्यम् अवलोक्य, सर्वात्मना खण्डित-प्रायम् आत्मनो नाटकम् इत्य् अपश्यन् गुरूत्तमान् सुबहुशः प्राशंसद् इति।

श्रीमतः कृष्णमिश्र-यतेः माया-वादितया तन्नाटक-नाम-श्रवण-मात्रेण तत्-प्रतिपाद्य-सरणिं स्वयम् अधिगत्य, आत्मनो मतानुसारेण तत्त्व-रूपं सूर्योदय-नामकं नाटकं [[देशिकोच्च|देशिकैश् च]]। एकस्याम् एव रात्रावनुजग्मुर् इति नेदं किम् अप्य् आश्चर्यं यामिनी-याम्-मात्रेणैव पादुका-स्तुति-सहस्र-प्रणेतॄणां तेषां [[उज्झितमहिमानममन्त्रितधुषां|अमित-महिमानम् अमन्द-धियां]] विदुषाम्” इति च।

श्रीमतः कृष्णमिश्र-यतेः [[प्रबोधचन्द्रे दय|प्रबोधचन्द्रोदय]]-प्रवृत्त्यैव समुचित-खण्डनात्मकं सङ्कल्प-सूर्योदय-नामकं नाटकं रचयामासुस् तत्र-भवन्तो वेदान्ताचार्या इति अभ्युपगमे ऽपि, न को ऽपि दोषः। सर्वथा च [[सङ्कल्पसूर्योदय|सङ्कल्प-सूर्योदयः]] प्रबोधचन्द्रोदयम् अतिशेते नितरां सर्वतो ऽपीति निस्संशयो ऽयं विषयः।

---

[[P6]]

### यतिराजविजयम् — श्रीवरदाचार्यश्च

एवं स्थिते अतिप्रौढ-सन्दर्भं अतिविपुलं तत्-महा-नाटकम् इति समालोच्य, सायन्तन-समय-समुल्लसित-मालती-मकरन्द-परिमल-मुचि सहृदय-हृदयानन्द-सिरा-वेधिनि सारस्वत-परम-सीम्नि [[नाटकमिहन्नि|नाटक-महिम्नि]] समतिष्ठित-पदः, श्री-भगवद्-रामानुज-मुनेः पूर्वाश्रम-भागिनेयस्य श्रीवत्स-कुल-चूडामणेः [[अखिलापरदर्शनमदकदर्शनस्य|अखिल-पर-दर्शन-मद-कर्दनस्य]] सुदर्शनापर-नामधेयस्य वरदविष्णु-वार्यस्य पौत्राणां [[वेदान्तकृटस्थानां|वेदान्त-कूटस्थानां]] [[सर्वत|सर्वतः]] प्रथित — श्रीमत्-श्रुतप्रकाशिकाचार्यादि-सच्छिष्य-वर्गाणां श्रीमतां वरदाचार्याणां पञ्चमः, [[प्रक्रूरविदितवैदुष्यः|प्रचुर-विदित-वैदुष्यः]] काञ्चीपुरी-वास्तव्यः श्री-घटिकाशत-सुदर्शनाचार्य-सूनुः श्रीवेदान्ताचार्य-रामानुजाचार्य-[[दर्शनस्थापन्याचार्याः|दर्शन-स्थापनाचार्याः]] [[प्रसादभूमिवरदाचार्यानामा|वरदाचार्य-नामा]] महाकविः — वेदान्त-विलासापर-नामधेयं इदं श्री-यतिराज-विजय-नाटकं मृदु-मधुर-मङ्गल-मञ्जुलेन सन्दर्भेण विरचयामास। अत्रापि [[प्रबोधचन्द्रोदय|प्रबोधचन्द्रोदयः]] इव षड् एव अङ्काः समुल्लसन्ति।

चार्वाक-बौद्धादि-सहायेन माया-वादेन मुख्य-मन्त्रिणा [[मिथ्यादृष्टिवेश्यासङ्गेण|मिथ्या-दृष्टि-वेश्या-सङ्गेन]] प्रतारितं वेदमौलिं (वेदान्तं) राजानं, तत्-सहायेन भगवता [[श्रीमदयामुनाचार्येण|श्रीमद्-यामुनाचार्येण]] [[प्रनोदितः|प्रणोदितः]] श्रीमान् यतिराजः श्री-भगवद्-रामानुज-मुनिः, तान् सर्वान् अपि निर्जित्य [[प्रविंक्षिणः|प्रतिपक्षिणः]], सुनीति-सहचारिणां सुमतिं विष्णु-भक्ति-स्वरूपां पट्ट-महिषीं राज्ञा च सङ्गमयन्, तं च परब्रह्मानुभव-स्वानन्दानन्दैक-साम्राज्ये अभिषिञ्चति — इत्य् अलौकिके ऽस्मिन् नाटके ऽयं वर्णयति कवि-सार्वभौमः।

वेदमौलिः — राजा। सुमतिः (विष्णु-भक्तिः) — देवी। माया-वादः — महा-मन्त्री; [[भास्कर्यादवादयश्च|भास्कर-यादवादयश् च]] — अन्ये मन्त्रिणः। चार्वाक-बौद्धादयः — माया-वाद-सहायाः। मिथ्या-दृष्टिः — वेश्या। तस्याः संसर्ग-लोभेन स्ववशम् आनीय वेदान्तं राजानं मोहयति माया-वादः। तम् इमं वृत्तान्तम् अभिज्ञाय [[दुर्मन्त्रिन्|दुर्मन्त्रिणः]] शासितुं, तं वेदमौलिं [[समृद्धर्तुं|समुद्धर्तुं]] च श्रीमन्तो भगवद्-यामुन-मुनयः श्रीमद्-रामानुज-मुनिं नियोजयामासुः। निस्सङ्गो ऽपि स यतिराजो, वेदान्त-संरक्षणैक-बद्ध-दीक्षः, [[पदद्वम्युपगम्य|पद-द्वयम् उपगम्य]] रङ्गप्रिय-[[मियरङ्कनामभाग्यां|मेय्यरङ्ग-नामभाभ्यां]] श्री-वाधूल-दाशरथि-वात्स्य-सुदर्शनाभ्यां वैतालिक-वेष-धारिभ्यां प्रबोधिते [[राजानि|राज्ञि]], कुदृष्टि-मन्त्रि-मत-निरसनेन तत्त्व-स्थापनेन च वेदान्तं संरक्षयामास। सद्यूहः — सेना-नायकः, इतिहास-पुराण-वेद-विचारादयः तत्-सहायाः!

---

[[P7]]

### [[उल्लोके|उक्ते]] नाटके ऽस्मिन् केचन रमणीयाः प्रघट्टाः

वेदान्तस्य राज्ञः प्रभावमेवं वर्णयति कविः सूत्रधारमुखतः —

> “त्रिभुवनमहनीयस् [[तेजमामेकराशिः|तेजसाम् एक-राशिः]]  
> [[निजनिजमतिसिद्धं निहुवानं|निज-निज-मति-सिद्धं निह्नुवानं]] प्रपञ्चम् ।  
> पर-मुषित-विवेकं स्फारयन्त्य् अन्धकारं  
> विघटयति मयूखैः वेदरूपो विवस्वान् ॥” इति ।  

नारदमुखतश्च —

> “सर्वस्यापि हितं ब्रवीति समयाचारान् करोति स्थिरान्  
> [[मायावीवरणं|माया-विवरणं]] न सहते [[मानप्रतापान्वतः|मान-प्रतापान्वितः]] ।  
> [[समान्यस्सकलाम्य्|समयज्ञः सकलासु]] नीतिषु महा-सत्त्वः स्थिराङ्गो युवा  
> तस्मान् नेतृषु [[वेदमौलिमहशो|वेदमौलि-सदृशो]] नान्यो ऽस्ति कश्चिन् नृपः ॥” इति च ।  

राज्ञश्च यतिराजप्रभावतः साम्राज्यलाभश्चैवं समुपवर्ण्यते —

> “[[सर्वैर्विलुमविषयः|सर्वैर् विलुप्त-विषयः]] सचिवैः पुरस्तात्  
> [[सम्पग्विचिन्त्य|सम्यग् विचिन्त्य]] सचिवेन यतीश्वरेण ।  
> सम्प्रापितः स्वपद-वैभवम् अद्वितीयं  
> सम्राड् असौ खलु भविष्यति वेदमौलिः ॥” इति ।  

#### व्याख्यान-विशेषाः।

१. वेदान्तस्य नायकधर्मा उच्यन्ते — सर्वस्येति। हितम् — पुरुषार्थोपायम्, समयाचारान् — दर्शन-धर्मान्। मायाकल्पितो जीववरो [[देषां|तेषाम्]] तान्; मायया — कपटेन, आजीवः — जीवनम्। मानेषु — प्रमाणेषु; मानः — चित्त-समुन्नतिः, प्रतापः — प्रसिद्धिः। मानेन प्रतापेन च। नीतिषु। उपक्रमोपसंहारादि-न्याय-विशेषेषु राज-नीतिषु। गुणान्तरानुपमर्देनाभिभूत-सत्त्वगुणो महा-सत्त्वः; महाबलश् च। स्थिराङ्गः। अङ्गं — [[व्याकरणदि|व्याकरणादि]]। युवा — मनोहरः। सत्त्व-शब्देन तत्-कार्यं ज्ञानं लक्ष्यते। “नॄन् — पुरुषान्, मोक्ष-प्रदानेन [[पा” तोति|पातीति]] नृपाः। समयाचाराः — देश-कुल-धर्माचाराः। एवं सर्वत्र शब्दतः, अर्थतः, तात्पर्यतश् च वेदान्त-परत्वं ऊहनीयम्।

---

[[P8]]

> “पौळस्त्येन यथा पुरा रघुपतिर् मायाविना वञ्चितः  
> भूयस् तं विनिहत्य शङ्कर-गिरि-स्फूर्जत्-प्रतापानतम् ।  
> स्वामी नः श्रुतिमौलिर् एष विजयी रामानुजस्यौजसा  
> साम्राज्यं भरतादि-भव्य-विभवं सत्यं तथा [[धप्स्यति|लप्स्यति]] ॥” इति च ॥  

नाटकस्यास्य यतिराजविजयानाम्नः समर्थनं च [[अतिचमकारतया|अतिचमत्कारतया]] क्रियते —

> “ [[चिलकूटतटे|चित्रकूट-तटे]] रामः चित्रभानौ चकार यत् ।  
> [[मानाळ्लाटे|मानिन्या-ललाटे]] तन्नामस्वरसंसिद्धमेव तत् ॥” इति,  

ललाटे कृतं हरितालतिलकमेव; तस्य स्वरैः यतिराजविजयमिति सिद्धमेव तन्नाम — इति प्रहेलिकया।

माधव-समयस्य ( [[वसन्तौ|वसन्ते]], श्रीवैष्णव-सिद्धान्तस्य च ) समृद्धिर अतिविशिष्टेन क्रमेण उपवर्ण्यते सूत्राधार-मुखतः। यथा —

> “ [[मरलं|सरलं]] वकुलाभिरामः श्रुति-मधु-निष्यन्दि-शुक-मुखालापः ।  
> वहति हरि-तत्त्वम् उच्चैः [[श्वासाकोटिषु|शाखा-कोटिषु]] महागम-स्तोमः ॥” इति,  

> “सुरभि-सुमनः-प्रबन्धाः श्रुति-सुख-[[परपुष्प|परपुष्ट]]-षट्पदालापाः ।  
> माधव-समय-विलासा मदयन्ति मनांसि किं पुनः सुदृशाम् ॥” इति च ॥  

[^1]: १. शङ्करगिरि — [[श ह्र म ध्ये गो वा ङ्ग णी|शारदा-पीठे गो-वाङ्मयी]] सरस्वती। शङ्करगिरिः — कैलासः। रामानुजः — यतिराजः। ओजः — बलम्। भरतादयः — ब्रह्मादयः, भरत-शत्रुघ्नादयश् च। सत्यं — साम्राज्य-विषयम्, न तु असद् इति भावः।  
[^2]: २. वकुलाभिराम-शब्देन [[तद्बन्धो|तद्-बोधो]] लक्ष्यते; श्रुति — वेद-सारः; शुक-मुखाः — ब्रह्म-विदः। हरिर् एव तत्त्वं — हरि-तत्त्वम्। तत्त्वान्तराणां तत्-विशेषणत्वात्। उच्चैः — सर्वस्मात् परम्। [[काव्यमाव्येन्द्रादिवायुपनिषत्सु|काव्यादिषु उपनिषत्सु च]]। [[महान्तमसनूहः|महान् अगम-समूहः]]। [[आममाः|अगमाः]] — वृक्षाः। सरल-वकुलाः — वृक्ष-विशेषाः। हरि-तत्त्वं — श्यामत्वं च।  
[^3]: ३. सुमनसः — विद्वांसः, पुष्पाणि च। प्रबन्धाः — ग्रन्थाः, सन्ततयश् च। श्रुति-सुख-परैः पूर्वाचार्यैः, [[पुष्पाः|पुष्टाः]] — पोषिताः। [[पाददालागाः|पदालापाः]] — शरणागति-वन्दनाः। सुदृशाम् — सुधियाम्, स्त्रीणां च।



[[P9]]

पुनश् च श्रीमद्-यतिराज-मुखतः माधव-समयं ( अभिजिन्-मुहूर्तम्, श्रीवैष्णव-सिद्धान्तं च ) मृदु-मधुर-स्वनं वर्णयति —

> “ [[मुखरतिलाः|मुखरिताः]] समीराः श्रुति-मधुरा बाल-कोकिलालापाः ।  
> तरवो ऽपि पुष्प-सुभगाः, माधव-समयो न कस्य बहु-मान्यः ॥” इति,  

धर्मगुप्तश् च —

सर्वोपप्रतापा ऋत्वियी वैष्णवी वेला, यद् इदानीम् —

> “ कुदृष्टिभिः शिवोलूक-सूर्यैः श्रुति-कदूक्तिभिः ।  
> तेजसा दुर्निरीक्ष्यो ऽयं वैष्णवः समयो ऽभिजित् ॥” इति च ।  

आदित्य-ज्योतिर् अपि, परम-व्योम — क्षीर-सागरादि-वत् परम-पुरुषस्य विशेष-सन्निधान-स्थानम् इति “उद्-वयं तमसस् परि” इत्यादिश् श्रुति-सिद्धं स्मारयन् वर्णयति; यथा —

> “ जगच्चक्षुर् इदं ज्योतिर् [[ज्योतिरिञ्जनमनामयम्|निरञ्जनम् अनामयम्]] ।  
> वैष्णवम् एव तेजोभिः वर्धते दीप्त-तारकम् ॥  
> 
> ‘उन्नामधेयम् उत्फुल्ल-पुण्डरीक-विलोचनम् ।  
> पश्यन्ति हि परं ज्योतिः केचिद् अत्र हिरण्मयम् ॥’ ” इति ।  

[^9_1]: १. श्लोक-द्वयेन माधव-समयः उच्यते। वेला कालो, मर्यादा च। कुदृष्टिभिः — वेदापव्याख्यानकृद्भिः; शिवो — रुद्रः, [[शिवनामप्रणेता|शिव-शास्त्र-प्रणेता]]। उलूकः — वैशेषिक-प्रणेता। श्रुति-कदूक्तिभिः — वेदापव्याख्यानादिभिः; “अभितो जयति” इति अभिजित्। अन्यत्र, शिवो गोमायुः, [[दिवाग्धाः|दिवान्धाः]], अभिजिन्-मुहूर्तो वैष्णवः। मध्यमेन तेजसा।  
[^9_2]: २. य एषो ऽन्तरादित्ये हिरण्मयः पुरुषो दृश्यते, तस्य [[कष्यासं|कप्यासं]] पुण्डरीकम् एवम् अक्षिणी, तस्योदिति नाम” इति अन्तरादित्य-विद्या-प्रकरणम् आह — उन्नामेति।  

इदम् आम्नायते छान्दोग्ये — (१-६-६) य एषो ऽन्तरादित्ये हिरण्मयः पुरुषो दृश्यते हिरण्य-श्मश्रुर् हिरण्य-केश आप्रणखात् सर्व एव सुवर्णः। तस्य यथा कप्यासं पुण्डरीकम् एवम् अक्षिणी, तस्य उदिति नाम, स एष सर्वेभ्यः पाप्मभ्य उदितः, उदेति ह वै सर्वेभ्यः पाप्मभ्यो य एवं वेद, तस्यर्क् साम च गेष्णौ — इत्य् अधिदैवतम्। अथाध्यात्मम् अपि, अथ य एषो ऽन्तरक्षिणि पुरुषो दृश्यते, सैवर्क् तत्-साम तद्-उक्थं तद्-यजुस् तद्-ब्रह्म, तस्यैतस्य तदेव रूपं यदमुष्य रूपं यावमुष्य गेष्णौ, तौ गेष्णौ, यद्-नाम तद्-नाम — इति।

---

[[P10]]

धर्म-रक्षणार्थं श्रीमद्-यतिराजस्य प्रतिज्ञाम् अपि वर्णयति, एवम् —

> “ 'निशात-निस्त्रिंश-कठोर-धारैर् [[वाग्भैर्विलुत्य|वाग्भिर् विलुत्य]] [[वेदमति कूलमूहैः|वेद-मत-प्रतिकूल-ऊहैः]] ।  
> महोत्सवो विष्णुपदाश्रितानां मया विधेयो महतां द्विजानाम् ॥'” इति ॥  

### इतरेषां मतानां निरूपण-प्रक्रिया

मतानां चार्वाकादीनां तत्त्व-वर्णनम् अपि नितरां सहृदय-विद्वन्-[[मनसराजहंसान्|मनोराजहंसान्]] रञ्जयति। यथा हि —

> “भङ्क्ते वक्ति च देह एव सुमहाभूतानि तेष्वेव धीः  
> [[किण्वाद्रो|किण्वादेर्]] मदशक्तिवत् क्रतुफलं भोक्ता न कोऽपि स्थितः ।  
> [[दम्भः किं पुनरप्यैनि नियमो न क्वापि जीवित्युवम्|दम्भः किं पुनर् अप्य् अस्ति नियमो न क्वापि जीविते ध्रुवम्]]  
> यावज् जीवति जीवितं नरपतिः न्यायो बलं केवलम् ॥  
> 
> इति [[चार्ग्यमतम्|चार्वाक-मतम्]] ; [[चिन्मात्रमावाद्योमन्तरं|चिन्मात्रम् एवाद्यम् इतरत्]] मिथ्यैवाविद्यकं जगत् ।  
> [[ततु|तत् तु]] मित्रस्य मे नित्यं चिन्मात्रं क्षणिकं मम ॥  
> 
> इति योगाचार-मायावाद-मते ;  
> 
> [[यद्वैभाषिकभाविन्|यद् वैभाषिक-भावि]] यद् अपि वा सौत्रान्तिकैः सूत्रितम्  
> योगाचार-विचारणा च सरणिः [[सौधम्य|सौधस्य]] नः ।  
> तत् ज्ञानं च मृषैव [[विश्वदिति|विश्वम् इति]] व्यक्तं ब्रुवन् निर्भयो  
> [[मत्याधै|मद्-याजी]] भव नान्यथा तव गतिर् [[गतिर्वैषाफलापार्थिनः|वृथाफलापार्थिनः]] ॥  

[^10_1]: १. उग्रैः तर्कैः। कठोरधारैः — कठोरमार्गैः। द्विजाः — विप्राः, पक्षिणः — मांसभुजः।  
[^10_2]: २. पञ्चभूतात्मके देहे ज्ञानम् उत्पद्यते पाकविशेषात् [[किञ्चम्|किण्वम्]]-मदशक्तिवत्। किण्वम् — सुराद्रव्यम्। [[गमनगम्ये|गम्यागम्ये]] इत्यादि-नियमो नास्ति। देह एव आत्मा। अर्थ-कामौ पुरुषार्थौ; नास्ति परलोकः। बुद्धिसामर्थ्यरहितस्य जीवनोपायो धर्मः — इति [[लोच्यतम्|लोच्यते]]।  
[^10_3]: ३. वासांसि स्वर्गः, [[स्वर्गीः|स्वर्गतः]] — इति [[कबन्धीमीमांसका|कबन्ध-मीमांसकाः]] ([[प्रामण्यानङ्गीकारात्|प्रामाण्यानङ्गीकारात्]] पूर्व-मीमांसकाः कबन्ध-मीमांसका इति व्यपदिश्यन्ते)। [[त्रिधिवो|त्रिधा]] वेदः। तत्र मन्त्रार्थवादेषु हि देवता-[[तन्नाक|तन्नाम]]-सर्वेश्वरादिसिद्धिः। [[विश्रोऽविद्याकलितः|विश्वो ऽविद्याकलितः]]; ज्ञानम् एव सत्यम् — इति बौद्धमार्गः। वेदान्तप्रतिपाद्यं सर्वं असत्; विज्ञानम् एव सत्यम्; एतच् च विज्ञानं वेदान्तविषयम् — इति राहु-मीमांसकाः (वेदपूर्वभागस्य [[प्रामाण्य अङ्गीकारात्|प्रामाण्यानङ्गीकारात्]] अद्वैतिन राहु-मीमांसका [[इत्युच्यन्ते|इत्य् उच्यन्ते]])॥  

---

[[P11]]

इति माध्यमिक-मतम् ;

> [[शब्दैः कोपवपुष्पसमक्लशध|वन्ध्या-सुत-खपुष्प-समाः]] वेदान्त-वादाः  
> [[विभ्रं निर्गधरमिदं|विश्वं निरीश्वरम् इदं]] न परे च लोकाः ।  
> कर्मैव सर्व-फलदं [[कृषिवलराणाम्|कृषिवलाणाम्]]  
> इत्यादि चिन्तयति वेद-विचार एषः ॥  

इति मीमांसक-मतम् ;

> “तत्त्वमसी” इति ब्रूते श्रुतिर् एव [[श्रुतुकेतुमुद्दिश्य|श्वेतकेतुम् उद्दिश्य]]।  
> पर-जीवयोः अभेदं [[ब्रुवन्मने|ब्रुवन्ती]] भवति [[विक्रमफला|विशद-फला]] ॥  
> 
> [['ब्रह्माश्ममेकमादाय ममिनो विहरन्त्यहम्|ब्रह्मांशम् एकम् आदाय ममिनि विहराम्य् अहम्]] ।  
> खण्डयामि [[जगन्मत्वं|जगन्-मिथ्यात्वं]] पाण्डित्यं मम दृश्यताम् ॥  
> 
> “यस्मिन् यन्-मतेन त्रिभुवनम् अखिलं यच् च पश्यत्य् अविद्या-  
> मुग्धं [[स्वाम्यस्तमेतदपि|स्वाध्यस्तम् एतद् अपि]] [[निजपुपुर्वीक्षणे|निज-वपुर्-वीक्षणे]] मुच्यते यत् ।  

[^11_1]: १. ममिनिः — सभा, युद्धं च। ममान्नम् — महाब्रह्म; ब्रह्मणो ऽयं चेति। [[ब्रह्मण्यस्तं|ब्रह्मण्य् अध्यस्तं]] जगत् अधिष्ठानब्रह्मज्ञानेन हि निरस्यम्; ब्रह्मणो ऽशश् च। मिनिति — प्रमिनिति; तया सह वर्तत इति समितिः — विद्वत्सभा, युद्धं च।  
[^11_2]: २. “सर्वं खल्विदं ब्रह्म” इत्यादिषु [[विवद्व्यवहारतः|विद्वद्व्यवहारतः]] [[जगद् ब्रह्मणोः|जगद्-ब्रह्मणोः]] प्रतीयमानतादात्म्यमनुपपत्त्या “चोरः स्थाणुः” इतिवत् बाधार्थं सामानाधिकरण्यम् अङ्गीकरणीयम्। तत्र “नेह नानास्ति किञ्चन” इत्यादि [[श्रुतिकन्यान्|श्रुति-कन्यया]] चोरवत् जगद् बाध्यम्; स्थाणुवत् ब्रह्म सत्यम्। निरधिष्ठान-भ्रमस्य अनुपपन्नत्वात् अधिष्ठान-सत्यत्वम् अङ्गीकरणीयम्, इत्याह — यस्मिन्निति। [[स्व-रोपित|स्वारोपित]]-जगद्-बाधो ऽपि स्वयम् एव इत्याह — यच्च पश्यतीति। स्वस्याधिष्ठान-ज्ञाने हेतुमाह — अविद्यामुग्धम् इति। न तु कदा अविद्या-निवृत्तिर् इत्याह — निजेति। [[ब्रह्मवेद|ब्रह्म वेद]] ब्रह्मैव भवति” इति श्रुतेः; ज्ञानम् — ज्ञानम् एव, विज्ञानं ब्रह्मेति श्रुतिबलात्, तच्च अविद्याकल्पित-धर्म-कर्तृ-करणपररहितत्वात् — स्वप्रकाशमिति। “यन्मनसा न मनुते” इति श्रुत्या न [[वेद्यताम्|वेद्यता]] इति आशङ्क्य आह — संविदामिति। [[निगुणं|निर्गुणं]] निष्क्रियं शान्तं, एकमेवाद्वितीयम्” इत्यादिभिः निर्गुणमित्याह — निर्विशेषमिति। “सदेव सोम्येदमग्र आसीत्”, “तत्त्वमसि”, सत्यं [[ज्ञानमनन्तं|ज्ञानम् अनन्तं]] ब्रह्म” इत्यादिधर्मसिद्धिं दर्शयति — सत्यं तदिति। विवादपदे शब्दो मिथ्या, दृश्यत्वात्, शुक्तिरजतवत्। “मृत्युमाप्नोति य इह नानेव पश्यति”, “नेह नानास्ति किञ्चन” इति [[प्रमाणञ्च|प्रमाणं च]] दर्शयति — मिथ्या तदितरदिति। उक्तार्थं द्रढयति — [[कोऽन्येथेति|को ऽन्यथेति]]। विस्तरस्तु शास्त्रे द्रष्टव्यः; [[इदमर्यमतक हि|इदम् अद्वैत-मतं हि]] शास्त्रनिपाद्यम्।  

---

[[P12]]

> ज्ञानं ज्ञेयाद् विहीनं भवति यद् अपदं संविदां निर्विशेषं  
> सत्यं तद् ब्रह्म, मिथ्या तद्-इतरद्-अखिलं को ऽन्यथा वक्तुम् ईशः ॥  

इति मायावादि-मतम् ;

> ‘ब्रह्मैकं तत्त्वम् एतद् बहुविध-चिद्-अचिच्-चित्त-नियन्तृ-प्रभेदान्  
> तत्-तत्-शक्ति-स्वरूपं परिणमति यथा वारि-फेनादि-रूपम् ।  
> [[मत्त्वं सर्वानुवृत्तं मणिषु परिमलन्यायतोऽचिन्त्यधार्मे|सत्त्वं सर्वानुवृत्तं मणिषु परिमल-न्यायतो ऽचिन्त्य-धर्मे]]  
> चैतन्यं स्वप्रकाशं श्रुतिर् इह विषये स्थापिता यादवेन ॥  

इति यादवप्रकाश-मतम् ;

> ब्रह्मैकं [[सदुपाधिभेदमितुरं|सद्-उपाधि-भेद-मिलितं]] जीवत्वम् अभ्येति तत्  
> जीवत्वे च विपत्तयो ऽनुपहितं ब्रह्मैव शास्त्रं शिवम् ।  
> ब्रह्मैक्यं खलु मुक्तिर् एतद्-अखिलोपाधि-क्षये देहिनाम्  
> कर्म-ज्ञान-समुच्चयादिभिर् इति [[त्वय्यन्यराज्य स्थितिः|त्वय्य् अन्यरागा स्थितिः]] ॥  

इति भास्कर-मतम् इति, तत्-तत्-प्रक्रियाः सम्यक् सङ्गृहीताः ।

### तेषां खण्डनप्रक्रिया

एतेषां मतानां खण्डन-प्रकारो ऽपि सुभग-सुन्दर-सन्दर्भेण [[निरूप्यतम्|निरूप्यते]] —

> “ [[स्ववाधिविरोधमस्या|स्व-वाग्-विरोध-मथिता]] चेत् सर्वं शून्यं मृषेति वाक् ।  
> सर्वं [[जीव्यतस्य|स्वीकृतस्य]] चेत् मृषा सर्पे ऽस्ति किं विषम्? ”  

इत्य् अनेन बौद्ध-मायावादि-मतयोः,

[[आकारभेदसम्पथ्यमेतदखिलं|आकार-भेद-सम्पृक्तम् एतद्-अखिलं]] [[निर्विशेषस्तुवादिनस्ते|निर्विशेष-वादिनस् ते]] न सम्भवति ।

[^12_1]: १. अस्यायमर्थः — सच्चिदानन्दमयं ब्रह्मैव तत्त्वम्। तच् च तत्-तत्-शक्तिमयं भोक्तृ-भोग्य-नियन्तृ-रूपेण परिणमति; यथा फेन-बुद्बुद-तरङ्ग-रूपेण वारि। कारणभूतं ब्रह्म-गुणः — [[वैतव्यम्|व्यापकतत्त्वम्]]; [[कश्चिद्बहुस्तुनि|कश्चिद् बहुष्व् अस्ति]] विद्यमानम् अपि न प्रकाशते। [[कारणमयत् सर्वं मिथ्या|कारणमयत्वात् सर्वं सत्यम्]]; [[कार्यात्मकं च सर्वं मिथ्या|कार्यात्मकं च सर्वं सत्यम्]], यथा घट-शरावादि। भेदाभेद-श्रुतयश् च अस्मिन्न् अर्थे व्यवस्थाप्यन्ते इति।  

---

[[P16]]

### यतिराज-विजय-नाटकस्य अनुबन्धः

*   समितिः — विद्वत्-सभा, युद्धं च
*   पदेषु — स्थानेषु
*   साप्तपदीनम् — सख्यम्
*   अनुबन्धाः — सहायाः
*   बन्दीग्राहम् — बन्दीं यथा गृह्णन्ति, तथा
*   अहीरप्ताः — सेवकाः
*   उपाध्यः — जपा-कुसुमादयः
*   विश्वमुषः — विश्व-चोरयोः
*   स्वराट् — अकर्मवश्यः
*   लब्धामिके — लब्ध-प्रतिष्ठे, गृहीत-पक्षे च
*   अनामिका — अप्रतिष्ठा, नासिका-रहिता च
*   परां कोटिम् — उन्नतं पदम्
*   अनुपहितं — उपाधि-रहितम्
*   शिवम् — [[गुणप्पदम|सर्व-मङ्गल-गुणास्पदम्]]

*   [[अंशुक्रम्|अंशुकम्]] — किरणम्, वस्त्रं च
*   [[मुनीतिः|सुनीतिः]] — सामान्य-विशेषादि-न्यायः
*   मूलमन्त्रम् — श्रीमद्-अष्टाक्षरम्
*   क्षेत्रज्ञाः — जीवाः
*   वर्तनीम् — क्षुद्र-मार्गम्
*   याम्यम् — यमलोक-मार्गम्
*   अर्चिरादिः — अर्चिरादि-मार्गः
*   उल्लोचः — वितानम्
*   प्रत्यञ्चि — प्रत्यगात्म-तत्त्वानि
*   स्वयञ्चित — ज्ञानैकमयः
*   विपश्चिता — सर्वज्ञेन
*   अक्षम् — इन्द्रियम्
*   परिकरः — उपकरणम्
*   चिरन्तनवचः — वेदः

एवं कठिन-पदानाम् अर्थाः व्याख्याने प्रतिपाद्यन्ते। तत्र स्थिताः केचन विशेषाः उपोद्घाते समुपवर्णिताः। कुत्र कुत्रचित् नाटक-लक्षण-समन्वयः, क्लिष्ट-पदानां विभिन्न-अर्थ-विवरणम्, वेदान्त-वाक्यानां [[तात्पर्यनिट्णयः|तात्पर्य-निर्णयः]], तत्र तत्र [[अनिन्मर्नीनामुद्धटणम्|अभिनव-मतानाम् उद्धरणम्]], सर्वत्र अवतारिका-प्रदानम्, मूल-ग्रन्थ-समर्थनोपायिकानां विषयाणां [[कोडीकरणम्|क्रोडीकरणम्]] — इत्यादयो बहवो विशेषाः, सार-संग्रह-रूपे ऽस्मिन् व्याख्याने विद्यन्ते। ते सर्वे ऽपि विमत्सरैः महद्भिः स्वयम् एव [[अनुभूयन्तान्|अनुभूयन्ताम्]] — इति [[विमर्शमालिया|विमर्श-धिया]] विरम्यते।



[[P13]]

किञ्च,

> [[नाऽयामः|नाधारः]] स्वप्रकाशे तिमिरम् इव रवौ ज्ञान-बाध्या च माया  
> न ब्रह्म ज्ञान-रूपं स्वयति न ततो बन्ध-मोक्षौ च तस्य ।  
> न ज्ञानं ज्ञेय-हीनं [[मदमतिपदं|न च मति-पदं]] निर्विशेषं न किञ्चन  
> [[मन्यं म्यान्मानसिद्धं|मान्यं स्यान् मान-सिद्धं]] जगद् अपि न यदि स्यात् क्रिया-बाधकाद्यः ॥  

किञ्च,

> प्रत्यक्ष-प्रभृति-प्रमाण-विदितं सत्यं च भिन्नं जगत्  
> बाधन्त्य् अस्य न केनचित् श्रुति-विहितैस् त्रैगुण्यात्मकं तद् जगत् ।  
> द्वैताद्वैत-गिरा त्रिभिन्न-[[विशया|विषया]] बाधा न [[नाला|नालं]] मिथः  
> [[पद्मालम्भ|पशूमालम्भ]]-निषेध-वाक्य-सदृशो [[विश्चापलापः|विश्वापलापः]] कुतः ॥  
> 
> “इदम् इत्थम्” इति ज्ञेयं “निर्विशेषम्” इति ब्रुवन् ।  
> “माता कन्या ममे”त्य् उक्ता हन्त लज्जेत किं भवान् ॥  

इत्यादिना मायावाद-मतस्य,

> [[निर्विशारश्रुतिर्नाम|निर्विशेषा श्रुतिर् नाम]] [[मत्कारं|विकारं]] न मृष्यति ।  
> जीव-नियन्तृ-भावो ऽपि तत्-कार्यत्वे प्रकुप्यति ॥  

इति यादव-मतस्य,

> “बहुधा जीव-रूपेण दुःख्यति” इति परः पुमान् ।  
> जल्पन्ती तव जिह्वेयम् शतधा किं न शीर्यते ॥  

इत्य् अनेन भास्कर-मतस्य च खण्डनम् उपनिबद्धम्।

### श्रीमद्विशिष्टाद्वैतमतस्य वैशिष्ट्यम्

श्रीमद्-विशिष्टाद्वैतस्य श्रीमद्-यतिराज-मतस्य [[सार्वजीन्यम्|सार्वजनीनत्वम्]], सर्व-प्रमाणानुकूलत्वम्, सर्व-सिद्धान्त-शिरोमणि-भूतत्वम्, सर्व-प्राणि-हृदयङ्गत्वं च अभिवर्णयति —

---

[[P14]]

**यतिराजः —** ( शुभ-निमित्तं वीक्ष्य, दक्षिणतो दर्शयन्, सहर्षम् )
> 'शुकासित-भरद्वाज-हारीताः सत्पथे स्थिताः ।  
> कृष्ण-पक्षाः [[कृने|कृते]] योगा द्विजा मे दर्शन-प्रियाः ॥’  

**राजा —** ( विमृश्य, स्मितं कृत्वा ) [[मद्भिप्रेतमेव|मदभिप्रेतम् एव]] यतिराज-दर्शनम्।  

**सुनीतिः —** [[समयगुक्तं|सम्यग् उक्तं]] देवेन।
> वेदेष्व् अर्थ-निधानानि दृश्यन्ते न हि सन्त्य् अपि ।  
> तत्र यद् येन दृष्टेन तत् तु तस्यैव दर्शनम् ॥  

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

> “ [[स्वस्वार्थैकानिरिह|स्व-स्व-अर्थ-एक-हानिर् इह]] न [[कचिच्छ्रतीनाम्|क्वचिच् छ्रुतीनाम्]]  
> प्रत्यक्ष-प्रभृतिर् अपि प्रमाण-वर्गः ।  
> स्वार्थेषु प्रभवति निस्सपत्न-चारी  
> राजन्ते वहति धुरं यतीश्वरे ऽस्मिन् ॥” इति ।  

इतिहास-पुराणाभ्याम् अनुमोदितः वेद-विचारो ऽपि सम्मान्य एव — इति प्रतिपादयति इतिहास-मुखतः —

[^14_1]: १. अत्र शुकाः — महर्षयः; कृष्णपक्षाः — कृष्णे भक्तिमन्तः; [[कृनेयोगा|कृतयोगाः]] — [[कृतोत्कृष्टास्तदुपासाः|कृत-उत्कृष्टाः तद्-उपासाः]]; सत्पथाः — सतां ब्रह्मविदां मार्गः; द्विजाः — ब्राह्मणाः; यतिराजदर्शनम् — यतिराज-सिद्धान्तः।  
[^14_2]: २. स्वस्वार्थेति। अत्रायम् अभिसन्धिः — उभय-मीमांसयोः एक-शास्त्रत्वात्, पूर्व-मीमांसा [[त्रैविद्य|त्रैविध्य]]-विषया; उत्तर-मीमांसा मुमुक्षु-विषया। तत्र याश् च श्रुतयो विरुद्धवत् प्रतिभासन्ते, तास् तु विषय-भेदात् परस्परं न बाधन्ते। उत्तर-मीमांसायां च ब्रह्मणो याः, शरीर-गुण-कर्मादि-[[वादिम्यः|वादिम्यः]] श्रुतयः, ताः, नित्य-निरवद्य-कल्याण-शरीर-गुण-कर्मादि-विषयाः; याः, [[तन्निषेधवन्त्यः|तन्निषेधवत्यः]], ताः, हेय-शरीर-विषयाः — इति न तासां परस्पर-विरोधः। प्रत्यक्ष-प्रमाणादयो ऽपि प्रबल-प्रमाणान्तर-बाधित-विषये प्रभुणि भवन्तीति प्रामाणिकं [[चिद्-चिद्|चिदचिद्-विशिष्टं]] जगत् सत्यम् एवेति।  

---

[[P15]]

> ये यजन्ति पितॄन् देवान् ब्राह्मणान् [[सहुताशनानन्|सहुताशनान्]] ।  
> सर्व-भूतान्तरात्मानं विष्णुम् एव यजन्ति ते ॥  

फलं च तत एव लभन्त इति [[मद्रचने निष्टपन्ते|मद्वचने निष्ठितानां]] न कश्चित् [[कचित|क्वचित्]] भयम् अस्ति — इति।  

सुनीति-मुखतश् च —

“ देव ! सहस्राधिकरण-दृष्ट-पराक्रमो [[ऽमर्जुन|ऽर्जुन]] इव रामानुज-मुनेः निष्पन्नः, [[ज्ञातवैदिककुलपालनप्रत्यहकृतानविजया|प्रतिज्ञात-वैदिक-कुल-पालन-प्रत्यह-कृत-अद्भुत-विजया]] महा-भारत-रण-समर्थो भवति देवस्य ” इति।  

इतिहास-पुराणयोः ग्रहणकत्वम् एवम् उपवर्ण्यते —

> [[विविधचिदचिन्निदीश्वर|विविध-चिदचिदीश्वर]]- [[नक्शैकभोगमोक्ष|लक्ष्यैक-भोग-मोक्ष]]-तदुपायः ।  
> उपबृंहिता युवाभ्याम् उपभुज्यन्ते हि [[सद्विरम्यर्थाः|सद्भिर् इमे अर्थाः]] ॥ इति ।  

भुक्ति-मुक्ति-सौभाग्य-निक्षेप-गोलो यतिराज-नय-वैभवम् एवम् वर्णयति। यथा —

> [[मृन्मन्मयदेहमॆव|मृन्मय-देहम् एव]] पुरुषः पुष्यन्नहं भोगवान्  
> इत्य् उन्मज्जति दुःख-सिन्धु-कुहरे मज्जन्न् अपि [[स्वात्मन|स्वात्मनः]] ।  
> [[गुद्रज्ञानमुवात्मकोऽप्यनुभवं|शुद्ध-ज्ञान-सुखात्मको ऽप्य् अनुभवं]] [[स्पृश्यत्ययं|स्पृशत्य् अयम्]] मूढधीः  
> मीमांसा-स्थूल-सूत्र-[[प्रयभरितां|व्रण-भरितां]] [[भन्नां|भग्नां]] वर-स्त्रीम् इव च ॥  

इति [[भुक्तस्य|मुक्तस्य]] प्रकारम् —

> [[ध्यायन मत्यमन्नमन्तरजडं|ध्यायन सत्यं ज्ञानम् अन्तर्-जडं]] [[ब्रह्माविन्देक्षणम्|ब्रह्म अरविन्देक्षणम्]]  
> [[निष्कम्पाय्य|निष्कम्प्य]] [[सुपुञ्जयेव|सुदृष्ट्यैव]] कृपया [[निर्धूतमायानुपः|निर्धूत-माया-मलः]] ।  

[^15_1]: १. अर्थवादसिद्धदेवता-तत्तल्लोकादिकमपि तत्तद्देवतार्थमित्यभ्युपगन्तव्यम्।  
[^15_2]: २. सहस्राधिकरणेषु — धर्मनिर्णयस्थानेषु। प्रत्यूहहन्ता — विघ्नहन्ता।  
[^15_3]: ३. चिद्रूपो — बद्ध-मुक्त-नित्य-रूपेण त्रिविधः। अचिद्रूपो — मूलप्रकृतिः, कालः, शुद्धसत्त्वम् इति त्रिविधः। तयोरीशः — तल्लीला — ईश्वरस्य क्रीडा — जगत्सृष्ट्यादिः।  

---

[[P16]]

> विष्णोः तत् पदम् एत्य तत्र परमे व्योम्नि स्वयञ्चित् स्वराट्  
> भुङ्क्ते तेन विपश्चिता सह महानन्दान् अनन्तान् बुधः ॥  

इति मुक्तस्य वैभवं च उत्कीर्तयति।  

जीवात्मनः स्वरूप-बन्ध-मोक्षादीनां समुपदेष्टृ माता-पितृ-सहस्रेभ्यो ऽपि वत्सलतरे वेद-पुरुषे एवेति, श्रीमद्-यतिराज-मुखतः सिद्धान्तयति —

> [[देहाशादिविलक्षणोऽणुरजडो नित्योऽहमंशोऽमल-|देहादि-विलक्षणो ऽणुर् अजडो नित्यो ऽहम् अंशो ऽमल-]]  
> ज्ञानानन्द-मयो ऽप्य् अनन्तमय इव भ्राम्यत्य् [[अविद्याऽऽवृतः|अविद्यावृतः]]।  
> पञ्च-क्लेश-विपाक-पावक-शिखा-लीढस्य तस्य आत्मनो  
> निर्वाणाय निसर्ग-सौहृद-निधे ! [[न्यान्या|नान्या]] गतिस् त्वां [[बिना|विना]] ॥ इति।  

श्रीमतो वेदमौलेश् च मुखतः परम-पुरुषस्य परम-कारुणिकत्वं जगदुदयविभवलय-लीलादि-कर्तृत्वं च प्रस्तौति —

> यः प्रत्यञ्चि सृजन् पराञ्चि च महा-भूतानि रक्षन् हरन्  
> क्रीडत्य् अद्भुत-दिव्य-मङ्गल-गुणः श्रीमान् अनादिः पुमान् ।  
> सर्वं कर्तुम् अकर्तुम् अन्यथा कर्तुं समर्थो ऽपि सन्  
> व्याजं किञ्चिद् उपेक्ष्य रक्षति जगद्-विश्व-व्यवस्थापकः ॥  

किञ्च,  

> [[मत्याशेष|मत्वाशेष]]-जडाजडात्मक-जगद्-देही “बहु स्याम्” इति  
> स्वेच्छातः बहुधा भवन्न् अपि न तद्-दोषेण लिप्येत यः ।  
> तत्-तत्-शब्द-धियाम् अयं तद्-अपृथक्-सिद्धैव विश्रान्ति-भूः  
> देहात्मादि-नयेन येन मुषिता भेदैक-वाचो गताः ॥ इति ।  

सर्व-ज्ञान-निधेश् च तस्य करुणा-[[करुणारशेरुपेक्षा|राशेर् उपेक्षा]] कुतः —

> सर्वेशः किम् असौ न शक्ष्यति परित्रातुं तथापि प्रभुः ।  
> सर्वान् रक्षति यत्-कटाक्ष-[[करणिकापेक्षी|कणिकापेक्षी]] नरान् उद्धरन्  
> [[संसारम्बुनिधेः|संसाराम्बुनिधेः]] स एव हि गुरुः सर्वोत्तरं दैवतम् ॥  

---

[[P17]]

इत्य् अनेन “गुरुर् एव परं दैवतम्” इति परम-गुह्यतमम् अर्थम् अपि उन्मीलयति।  

एवम्,  

> [[अन्तर्वेदामृताध्र ज|अन्तर्-वेदान्त-अमृताद्रं च]] बहिः-साहित्य-सौरभम् ।  
> विद्मः खलु वेदान्त-विलासं भोक्तुम् अर्हति ॥  

इति, [[व्याख्यानकृदर्भाशिनदिशा|व्याख्यान-कृद्-दर्शित-दिशा]] [[कर्मनीयगुमागाहित्यसुमनःसौरभं परिमदयेष|कमनीय-काव्य-साहित्य-सुमनः-सौरभं परिमलयन्]] [[परिपिञ्चन्|परिषिञ्चन्]], अप्राकृत-वेदान्त-[[पर्यायमधुरममास्वादमौभाग्यमप्यमर्प|पर्याय-मधुरतमास्वाद-सौभाग्यम् अपि एतेषु]] सम्पादयति, परम-सुभग-रमणीय-कोमल-[[कन्चन|काव्य]]-रचना-धुरीणः [[महद्यचक्रवर्ती|महा-कवि-चक्रवर्ती]] [[विद्वन्तल्लजः|विद्वत्-तल्लजः]] [[कविदिग्वामणिः|कवि-शिखामणिः]] अयम् इति, धन्ये साहित्य-वेदान्त-शास्त्रे, [[धन्याश्च रमिका विद्वत्त्वेम्वराश्रुति|धन्याश् च रसिकाः विद्वत्-शिखामणयः, इति]] महद् इदं प्रमोद-स्थानम्।

### [[सङ्क्षेपमपि|सङ्क्षेपेण]] दर्शनानां स्वरूप-सङ्ग्रहः

सर्वेषाम् अपि दर्शनानां सङ्ग्रहेण स्वरूपं निरूप्यते —

१. पृथिव्यादि-भूत-चतुष्टय-सङ्घाते चैतन्यम् उपजायते। [[तन्मुवद्वन्मय म्वर्गानरकौ|तन्मूलावेव स्वर्ग-नरकौ]]। तेषां [[विळये|विलये]] चैतन्यम् अनुविनश्यति। नास्ति परलोकादिः — इति चार्वाक-मतम्।

२. ताथागतेषु, वैभाषिक-मतं तु — परमाणु-सङ्घातः प्रत्यक्ष-दृष्टं च जगत् क्षणिकम्। नास्त्य् अन्यः आत्मा। तस्मिन् स्थिरत्व-बुद्धिः संसारः, क्षणिकत्व-बुद्धि-मोक्षः — इति।

३. स एव सिद्धान्तः सौत्रान्तिकस्य अपि; तथाप्य् अनुमान-सिद्धं जगद् इति अङ्गीकरोतीति विशेषः।

४. योगाचारश् च — [[ज्ञानज्ञेयो|ज्ञान-ज्ञेयौ]] [[भ्रान्तिमूलैः|भ्रान्ति-मूलौ]]; ज्ञानम् एव सत्यम्; तद् अपि क्षणिकम् — इति,

५. माध्यमिकश् च — प्रमाण-प्रमेय-प्रमातृ-जातं सर्वम् अपि भ्रान्ति-सिद्धं शून्यम् एव तत्त्वम् — इति च [[अमन्यन्ति|मन्यन्ते]]।



[[P18]]

६. आर्हताः अपि — जगत् सर्वं कार्य-कारण-रूपेण नित्यानित्य-मयात्मकं [[भिन्नाऽभिन्नात्मकम्|भिन्नाभिन्नात्मकम्]]। आत्मानः कर्मानुरूप-शारीर-परिमाण-परिमाणाः। [[अनादी|अनादिः]] संसारः मल-धारण-आत्मज्ञानादिभिः प्रकृष्ट-विनिर्मोकाद् ऊर्ध्व-गति-प्राप्तिः — मोक्षः — इति ब्रुवते।

७. नैयायिकाः, वैशेषिकाश् च — जगद्-उपादानं परमाणवः; आनुमानिकेश्वरो निमित्तम्; [[अनादिर्ना|अनादिर् हि]] संसार-मार्गः। सर्वेश्वरोपासनेन एकविंशति-दुःख-ध्वंसो मोक्षः — इति निरूपयन्ति।

८. पाशुपताश् च — परमाणव एव जगद्-उपादान-कारणम्। आगम-सिद्ध ईश्वरो निमित्त-कारणम्। संसारो [[ऽनादी|ऽनादिः]]। आगमोक्त-कर्मानुष्ठानात् पशुपति-सारूप्य-प्राप्तिः — मोक्षः — इति,

९. साङ्ख्याः, योगिनश् च — प्रकृतिर् एव स्वतन्त्रा जगद्-उपादान-कारणम्; सैव कर्त्री, भोक्त्री च। आत्मा तु पुष्कर-पलाश-वन् निर्लेपः। आत्मनः प्रकृतेश् च अनादि-सम्बन्धः — संसारः। प्रकृति-पुरुष-विवेकः — मोक्षः — इति,

१०. [[पूर्वमीमांसकु|पूर्व-मीमांसकाः]] — भाट्टाः, प्राभाकराश् च — अनन्ता नित्याः सर्वगता [[अनादिकर्मर्रापकात्|अनादि-कर्म-परिपाकात्]] संसरन्त्य् आत्मानः। प्रवाहतो नित्यः प्रपञ्चः। कर्मापूर्वम् एव आत्म-प्राप्ति-रूप-मोक्ष-हेतुः। ईश्वरस् तु निष्प्रमाणको नाभ्युपगम्यते — इति च वदन्ति। वस्तुतस् तु जैमिनेर् ईश्वर-निरसने न तात्पर्यम्। किं तु कर्मण्य् अश्रद्धा मा भूद् इति। “कर्म-प्रभावाद् एव सकल-पुरुषार्थाः सम्भवन्ति” इति प्रौढ-वादेन निरूपयामास।

११. उत्तर-मीमांसकेषु — मायावादिनः — निर्विशेष-चिन्मात्रं ब्रह्म माया-शबलं भ्रमति। स एव संसारः। “तत्त्वमसि” इत्य्-आदि-श्रुति-वाक्य-जन्य-विज्ञानेन भ्रम-निवृत्तिर् मोक्षः — इति,

१२. [[भास्करीयश्च|भास्करीयाश् च]] — [[सत्योपाधिश्रं|सत्योपाधि-मिश्रं]] ब्रह्मैव भ्रमति। स एव संसारः। वर्णाश्रम-धर्मानुष्ठान-सहकृत — वाक्य-जन्य-ज्ञान-पूर्वक — [[उपासनत्मक|उपासनात्मक]]-ज्ञानेन उपाधि-नाशो मोक्षः — इति,

१३. यादवीयाश् च — तदेव ब्रह्म सत्य-चिदचिदीश्वरात्मकं परिणमति। तस्य तादृश-भेद-ज्ञानं संसारः; ज्ञान-कर्म-समुच्चयात् भेद-ज्ञान-नाशो — मोक्षः — इति,

---

[[P19]]

१४. द्वैतिनश् च — स्वतन्त्रो भगवान् विष्णुः जगद्-कारणम्; अस्वतन्त्रं [[तदितरजगत्|तद्-इतर-जगत्]], तस्मात् सर्वथा भिन्नम् एव। जगद्-ब्रह्मणोर् अत्यन्त-भेद-ज्ञानात्, भक्ति-योगेन च ब्रह्मणः सालोक्यादि-प्राप्तिर् मोक्षः — इति च अभ्युपयन्ति।

१५. विशिष्टाद्वैतिनस् तु — सूक्ष्म-चिदचिद्-विशिष्टः ईश्वरः — जगद्-कारणम्; स्थूल-चिदचिद्-विशिष्टः ईश्वरः कार्य-जगत्। ज्ञान-कर्म-पारिकर्मितात् भक्ति-योगात्, प्रपत्ति-योगाद् वा विलक्षण-देश-विशिष्ट-विशिष्ट-ब्रह्मानुभवो मोक्षः। प्रपत्ति-योगस् तु सर्व-प्राणि-सुलभः; तेन प्रपन्नस्य श्रीमन्-नारायणस्य अनुग्रहात् सर्वेषाम् अपि स्वस्वरूपाविर्भावः, तेन ब्रह्मणा सह [[सह परमासायुज्यति-|परम-सायुज्य-]] [[शुद्धसत्त्वमयवैकुण्ठलोकप्राप्ति|शुद्ध-सत्त्व-मय-वैकुण्ठ-लोक-प्राप्तिः]], [[तव|तत्र]] श्रीमन्-नारायणस्य दिव्य-मङ्गल-[[गुणगणविभूभूतिविभूत्यादीनामनुभवश्चेति|गुण-गण-विभूति-विभूत्यादीनाम् अनुभवश् चेति]] मोक्ष-साम्राज्याद्य्-अनुभूतिः सम्पद्यत इति च प्रतिपादयन्ति।

एवम् अत्र सर्वेषाम् अपि मतानां प्रक्रिया अनुसन्धेया॥

### नाटके ऽस्मिन् प्रधानो नायकः

[[उद्योगकमनीयतातिकेर्तने|उद्योग-कमनीयतातिकीर्तने]], नवरस-भरिते, [[अमन्दानन्दमन्धायके|अमन्दानन्द-प्रदायके]] आध्यात्मिक-तत्त्व-विषयक-भासुर-नाटके ऽस्मिन् [[सचिवयात्तसिद्धि|सचिवायत्त-सिद्धिः]] वेदमौलिर् एव नायकः; [[नेतृव्योपायिकाः|नेत्रुपयोगिकाः]] सकला अपि गुणाः, सर्वाणि च लक्षणानि [[सम्पूर्णांनि|सम्पूर्णानि]] तस्मिन् [[विद्यन्तन्ते|विद्यन्ते]]।

नायक-लक्षणं चोक्तं [[नायकळक्षणं चोक्तं|नायक-लक्षणं चोक्तं]] दशरूपके द्वितीय-प्रकाशे। यथा —

> नेता विनीतो मधुरस् त्यागी दक्षः प्रियंवदः ।  
> रक्त-लोकः शुचिर् वाग्मी रूढ-वंशः स्थिरो युवा ॥ १ ॥  
> 
> बुद्ध्य्-उत्सहा-स्मृति-प्रज्ञा-कला-मान-समन्वितः ।  
> शूरो दृढश् च तेजस्वी शास्त्र-चक्षुश् च धार्मिकः ॥ २ ॥ इति ।  

अत्र, विनीतः — विनयआदि-सुगुण-गण-सम्पन्नः; मधुरः — प्रियदर्शनः; त्यागी — सर्वस्व-दायकः; दक्षः — क्षिप्रकारी; प्रियंवदः — प्रियभाषी; रक्त-लोकः — रञ्जित-सकल-प्राणिः; रूढ-वंशः — प्रसिद्ध-कुलजः; स्थिरः — वाङ्मनः-क्रियाभिर् [[अविचळः|अविचलः]]; युवा — [[यौवनं|यौवने]] विराजमानः; बुद्धिः — ज्ञानम्, गृहीत-विशेष-कर्त्री तु प्रज्ञा। स्पष्टम् अन्यत्।

---

[[P20]]

एते सर्वे ऽपि गुणाः सहज-सुभगा विराजन्ते महाराजे ऽस्मिन् वेदमौलौ इति, अभिवर्णयति कविर् अयं मुक्तकण्ठम्; यथा —

> सर्वस्यापि हितं ब्रवीति समयाचारान् करोति स्थिरान्  
> [[मायावीवरणं|माया-विवरणं]] न सहते [[मानप्रतापान्वतः|मान-प्रतापान्वितः]] ।  
> [[समान्यस्सकलाम्य्|समयज्ञः सकलासु]] नीतिषु महा-सत्त्वः स्थिराङ्गो युवा  
> तस्मान् नेतृषु [[वेदमौलिमहशो|वेदमौलि-सदृशो]] नान्यो ऽस्ति कश्चिन् नृपः ॥ इति ।  

अयं च सचिवायत्त-सिद्धिः धीर-ललितः; यथा समर्थयति कविर् एव —

> “ मय्य् एव राज्यम् अखिलं विनिवेश्य राजन् !  
> विश्रब्धम् एव विहरन् यथायथ-कृत्यः ।  
> राज्यं मया च [[हतकरकमेतदासीत्|हत-कण्टकम् एतद् आसीत्]] ” (२-२) इति ;  

माया-वाद-मुखतः। “निश्चिन्तो धीर-ललितः कला-सक्तः सुखी मृदुः” इति हि धीर-ललितस्य लक्षणम् उक्तं दशरूपके। तथैव हि माया-वादेन प्रोत्साहितो वेदमौलिः सङ्गीत-नाट्यादि-कला-विद्यया मिथ्या-दृष्ट्या क्रीडितुम् उपक्रमते। [[श्रीमहामुन|श्रीमद्-यामुन]]-मुनि-मुखतश् च — “त्वय्य् एव ललिते सति मन्त्रिष्व् एव कार्य-भारः पर्यवस्यति” इति; “ [[दुर्मन्त्रिद्वचनात|दुर्मन्त्रि-वचनात्]] ईदृश-प्रेम-शालिनीं त्वामपि दूरीकुर्वतो मे ललितम् अपि दोषाय” इति, “त्वयि मन्त्रिणि किं न सम्पद्यते ललितस्य?” इति च महाराज-मुखतः; श्रीमद्-रामानुज-मुनि-मुखतश् च — “महाराज ! [[सुमत्यॉ|सुमत्या]] सह विहरन् विजयस्व। निष्ठा मे खलु ते धीरस्य [[लालित्यमुपपल्लयितुम्|लालित्यम् उपपल्लवयितुम्]] ” इति।

पुनः राज-मुखतः।

> निधाय सर्वेश्वर-नीति-मार्गे रामानुजे मन्त्रिणि राज्य-भारम् ।  
> सुनीति-मत्या [[सुमत्ये|सुमत्या]] त्वया ऽहं क्रीडामि कृत्स्नैः विषयैः प्रहृष्यन् ॥  

इति च, स्पष्टं लालित्यम् उत्कीर्तितम् इति।

तथापि, धीरोदात्त एवायं भवति। तल्लक्षणं हि —

> महासत्त्वो ऽतिगम्भीरः क्षमावान् अविकत्थनः ।  
> स्थिरो [[निगूढहङ्कारो|निगूढाहङ्कारो]] धीरोदात्तो दृढ-व्रतः ॥  

---

[[P21]]

इति दशरूपके प्रतिपाद्यते। महा-सत्त्वः — शोकमोहाद्यनभिभूत-अन्तःकरणः; अविकत्थनः — अनात्म-श्लाघनः; निगूढाहङ्कारः — विनय-च्छन्न-गर्व-लेपः; दृढ-व्रतः — अङ्गीकृत-निर्वाहको धीरोदात्तः — इति तस्य विवरणम्।

[[एतादृशळक्षणळक्षणविशिष्ट|एतादृश-लक्षण-लक्षित-विशिष्ट]] एवायम् इत्य् अत्र न को ऽपि सन्देहः। तथाहि —

प्रथमत एवायं माया-वाद-विषये विमनायते —

> मान-अर्थ-[[मानार्थतन्त्वहीनो|तत्त्व-हीनो]] माया-जीवी [[मुषावादी|मृषावादी]] ।  
> सुमति-सुनीति-द्वेषी माम् अप्य् एवं करोति किं कुर्मः ॥  

> भेदोपजीव्य् अपि [[भनत्ति|भनक्ति]] तम् एव भेदम्  
> मानं [[प्रणिन्नपति|प्रणिनिन्दति]] मान-परायणो ऽपि ।  
> सो ऽयं प्रमाण-पुरुषैः स्वकरोपनीतान्  
> मिथ्येति वक्ति [[मियतौऽपि हरन|मिषतो ऽपि हरन्]] महार्थान् ॥ इति।  

ततश् [[ततश्चेवमालच्य|चैवम् आलोच्य]] निश्चिनोति —

“तद् अत्र किं प्रतिविधेयम्? (विचिन्त्य) तावद् अयम् [[अनुमरणीय|अनुसरणीय]] एव, यावद् अस्माकम् [[यावदस्माकमुनु-|अनुकूलो]] ऽन्यो नीति-कुशलो कश्चिद् [[कश्चिदमयपदं निवेशितस्यान|अमात्य-पदे निवेशितः स्यात्]]; अन्यथा, [[आमरणयो|आ-मरणं यो]] जीव-ग्राहं गृह्णीयुः” इति। अपि च निगूढाहङ्कारो दृढ-व्रतो भवति। सर्वं जानन्न् अपि क्षमावान् [[नाननु-|न अनुवर्तते]], न तु मूढः, परतन्त्रश् च। वस्तुतस् तु, इदं तस्य [[मौशील्यद्याद्यतिशयमेव|सौशील्याद्य्-अतिशयम् एव]] पुष्णाति।

[[मिथ्यादृष्टिविलासिनीविलासमलम्ब्य|मिथ्या-दृष्टि-विलासिनी-विलासम् आलम्ब्य]] [[राजः|राज्ञः]] न बन्धु-गत्या विद्यमानम्; किन्तु, आरोपितम् एव दाक्षिण्य-वशात्। तथैव मन्तुं समर्थयते कविः परमार्थतया। यथा हि —

**प्रथमाङ्के — नारदः —** वत्स ! मा भैषीः। प्रकृत्य-निर्मले स्फटिक-[[स्फटिकमणी|मणौ]] प्रकृतोपरागः कियच् चिरं तिष्ठति” इति,

**चतुर्थाङ्के — सुमतिः —** सखि ! आर्य-पुत्रस्य [[कश्मलां|कश्मलं]] दर्शयामि, यः कश्मले रथ्याम्भसि आत्मानं पातितवान्।

**गीता —** भद्रे ! तस्य तादृश-वर्ण-संसर्गो ऽपि दृश्यमानः, प्रवाहान्तरेण परमात्म-विदो न सम्भवति” इति च।

---

[[P22]]

**पञ्चमाङ्के — श्रीमद्यामुनमुनयो ऽपि —**

> मन्त्रिषु न्यस्त-भागो ऽयं न तद्-दोषेण दुष्यति ।  
> स्फटिकः किं प्रदूष्येत वर्ण-भेदैर् उपाधिजैः ॥  

इति, महाराजस्य परमार्थतः दोष-राहित्यम् उपपादयन्ति। अतो ऽत्र लालित्यं — [[व्याश्रित-|आश्रित-]] जन-पक्षपातित्व-निबन्धनं भूषणायैव, न तु दूषणायेति मन्तव्यम्।

किञ्च, चन्द्र-मलय-पवनादि-सहायेन मन्मथेन नितरां पीड्यमानः मूर्च्छाम् उपगतो राजा, प्राण-सखीभ्यां सुनीति-गीताभ्याम् अनुनीतायाः, श्रीमत्याः महिष्याः सर्वाङ्गीण-रमणीयायाः, विष्णु-भक्ति-रूपायाः [[सुमत्यः|सुमत्याः]] सुप्रसादेन प्रबोधितः, ताम् अनुलालयति तुल्य-शील-वयो-वृत्तां [[तुल्याभिजनलक्षणं|तुल्याभिजन-लक्षणां]] तां देवीम् एवम् —

> सुमते ! न भवत्य् एव श्रुति-मार्गानुसारिणी ।  
> [[तरळे|तरले]] तव नेत्रे च मम चित्त-हारिणी ॥  

[[छायामिवानुपश्यान्तः|छायाम् इव अनुपश्यन्तः]], [[तृषिनो|तृषिताः]] जाह्नवीम् इव, नीवीम् इव दरिद्रस् तां कृतकृत्या जहामि [[जहामि त्रिम्|जहामि दिवम्]] ॥ इत्यादिना।

अतः, प्रणयि-मानादि-परमोदात्त-गुण-चरित्र-सम्पन्नो ऽयं धीरोदात्त एव।

शास्त्र-दृष्टि-निश्चितानां वीर-चरितानां प्रचण्डे वादाहवे च प्रवृत्ते, राजा च अयं, स्वस्य महोदात्ततां महासत्त्वतां महाभागतां महोदारतां च सम्यक् प्रकाशयति। [[म|स]] च प्रघट्टः, [[प्रचुरळघुभगसुन्दरवीररसः|प्रचुर-सुभग-सुन्दर-वीर-रसः]] परमावर्जको भवति परम-रसिकानाम् इति, [[अनिरोहितो|अतिरोहितो]] ऽयं विषयः।

स्वयं प्रवीरतां च [[प्रकटरयति|प्रकटयति]] — मिथ्या-दृष्ट्युत्साहितस्य तस्य योगाचारस्य सर्वतोद्रेकेण [[समाभर्तेन|समारम्भेण]] भीत-भीतां सुमतिं समाश्वासयन्, क्षोभात् प्रतिपद्य [[स्खं|स्वं]] महिमानम् एवम् — राजा; (सधैर्यम्) “अयि प्रिये ! [[विमकुलासि|व्याकुला ऽसि]]

> विरमतु तव भीतिर् वेपमाना ऽसि किं त्वम् ।  
> [[विमलमदवभाभिः|विमल-मद्-अवभाभिः]] [[वेदमौळिः|वेदमौलिः]] किलाहम् ॥ ” इति।  

अन्ते च सर्वम् अपि आध्यात्मिकं तत्त्वं [[यतिराजोन्मं|यतिराजः]] स्वयम् एव उपदिशति सुस्फुटतया —


[[P23]]
ध्यायन् सत्यम् (६-२४), यः प्रत्यङ्गी (६-२६), कर्मयाज (६-२७), मद्यशेष (६-२८) सर्वज्ञो न (६-३०) इत्यादिभिः श्लोकैः ।

सुनीति-सुमतिभ्यां च अयम् विषयः समुपबृंहितः यथा — "(मम आश्रयम्) देव ! भक्तम् [[अन्न्तरेण|अन्तरेण]] को वा तत्त्वम् उपदिशति" इति ।

किं च दिग्विजय-उद्यम-श्रवणम् अनुष्ठानम् अनेन —

" द्विजेभ्यो दीयताम् ..... प्रमुच्यन्तां सर्वे [[प्रवलभवकारागृहगताः|प्रबल-भव-कारागृह-गताः]] । " इति, स्वस्य महौदार्यम् ; भगवद्-दिव्य-मङ्गल-विग्रहम् अनुस्मृत्य नमस्यति "निःप्रकम्पेण" — "[[जानीमन्तव|जानीमस् तव]] सत्यम् अर्जुन" (६-४५), "अर्कैः क्लृप्तम्" (६-४६) "परस्माद् अन्यस्मै" (६-४७) "नमो यस्माद् आसीत्" (६-४८) "अनिर्वाच्यं गतः" (६-५२) इत्यादिभिः श्लोकैः, भगवतः सौशील्य-सौलभ्य-वात्सल्य-स्वामित्वादिकल्याणगुणाश्च प्रकटीकृताः ।

अन्ते च —

> " कुदर्शनानीतदर्शनारीर् निनीषतः कुर्वतश्च जनशमनम् ।  
> सम्यक्क्ऌप्तन्यायकलापदर्शिनो सुदर्शनोऽसि प्रियदर्शनस्त्वम् ॥ " इति,

" मायावी सचिवो निरामि " (६-५५) इत्यादिना च [[मन्महनुमानन्|मन्महानुभावो]] मूल-मन्त्रेश्वरं श्रीमन्तं यतिराजं [[प्रस्तौतिनराम्|प्रस्तौतितराम्]] । उद्विजते च नितरां स्वस्य [[मिथ्यादृष्टिष्यामोहं|मिथ्यादृष्टि-व्यामोहं]] प्रति [[मुकुटतन्वा|मुकुटतन्त्रः]] — "[[गगान्यस्य मुञ्चतोऽयं|गगनान् निपततोऽयं]] मार्गः, न तु [[नेत्रुदर्शशीलस्य|नेतुर् देशान्तरस्य]] । तथापि सम्प्रत्य् एवम् अभिनेतव्यम् " इति ।

[[मन्त्रिणाम्मुख्कर्षसम्वोऽपि|मन्त्रिणामुत्कर्षोऽपि]] राज्ञ एव [[समुकर्षेन्तर्गतित स्थिनमेव|समुत्कर्षेऽन्तर्गत इति स्थितम् एव]] । अतः, [[अद्भुतनि वृत्तक्रमे|अद्भुतनिर्वृत्तिप्रक्रमे]] नाटकेऽस्मिन् सर्वलक्षणलक्षित-सर्वाङ्गमन्त्रो वेदमौलिरिव धीरोदात्तो नायकः । तस्य च [[दक्षिणहस्तमन्थानस्य|दक्षिणहस्तस्थानीयस्य]], [[असितविमलनिशितप्रासप्रभविशारद|असितविमलनिशितशास्त्रप्रज्ञाविशारदः]], परमोदारोदात्तहृदयः, [[चतुलगाम्भीरगतिः|चतुरगाम्भीरगतिः]], अकृत्रिमापरिमेयदिव्यकल्याणगुणगणमहोदधिः, सर्वजनमनोहराकृत्रिमशौचविग्रहविभूतिः, अनिमिषधन्वा, [[श्रीमल्लुद्द्रोणापरावतारः|श्रीमल्लक्ष्मणार्यापरावतारे]] यतिराजो मुख्यो मूलमन्त्री सञ्जात इति, हेम्नः पुनरामोदः । तस्य च मन्त्रिवर्यस्य प्रतिभा-प्रताप-महिम्ना महाराजस्य महान् विजयः सुसम्पन्नः । [[दुर्निन्त्रकृत्कुहककुदृष्टिवागुरा-|दुर्मन्त्रिकृत-कुहक-कुदृष्टि-वागुरा-]]

---
[[P24]]
[[बन्धनिर्मोकरूपो|बन्ध-निर्मोकरूपो]] विजयो राज्ञ एव । मूलमन्त्रिणि यतिराजे स्थितः । [[अत्रविजयमुन्याहो|अत्र विजयो मन्त्रिणो]] राज्ञ एव फलप्रद इति, वीर्यम् अपि तन्निष्ठं तद्वन्तं भवति — इति च सर्वं समञ्जसम् ।

" वेदान्तविजयम् " इति [[नाम औचित्यमपि|नाम्न औचित्यम् अपि]] तदैव स्फुटं सम्भवति ।

ननु " यतिराजविजयम् " इति नाम्नः प्रसिद्ध्या, यतिराज एव प्रधान-नायकोऽस्तु ; मुद्राराक्षसादौ [[चाणक्यादिविदिनि चेतः दृशन्तेऽपि|चाणक्यादिवदिति चेत्, तद्दृष्टान्तेऽपि]] तुच्छो विचारः । मन्त्रिणो विजयः, राज्ञ एव प्रशंसां सम्पादयतीति, प्रकृते यतिराजस्य विजयो राज्ञः श्रीवेदमौलेरेव [[उत्कर्षमावह इति|उत्कर्षावह इति]], " यतिराजविजयम् " इति नामधेयम् अपि तदनुकूलम् एव, न प्रतिकूलम् ।

[[वेणीसंहारमुद्राराक्षसादिमान्ययोगक्षेममिदं नाटकप्रनमिति|वेणीसंहार-मुद्राराक्षसादि-समान-योगक्षेमम् इदं नाटकम् इति]], तत्र प्रवर्तिता वादा अत्रापि समवतरन्तीति च, तद्विवेचनाभागं विमर्शकानां हस्तेषु समर्प्य विरमामि विस्तरतः ।

#### अत्र प्रधानो रसः

अस्मिन् नाटके प्रधानो रसो वीर एव भवितुमर्हति । तल्लक्षणम् उक्तं दशरूपके —

यथा —

> वीरः प्रताप-विनय-अध्यवसाय-सत्त्व-अविषाद-विस्मय-विक्रमाद्यैः ।  
> उत्साहभूः स च दया-रण-दान-योगात् त्रेधा, [[कलिस्तत्र मनिगर्वधुनिप्रकर्षः|कलिस्तत्र मतिगर्वधृतिप्रकर्षः]] ॥ इति ।

अत्रावलोकः —

"प्रताप-विनयादिभिर् विभावितः, [[करूणायुद्धदानादैरनुभावितः|दयारणदानादिभिरनुभावितः]], गर्व-धृति-हर्ष-अमर्ष-स्मृति-मति-वितर्क-प्रभृतिभिर् भावितः, उत्साहः स्थायी, स्वदते भावक-मानसाविस्तरानन्दाय [[प्रभवन्तीत्येष|प्रभवन्न् एष]] वीरः " इति ।

अत्र मुनिः — "अथ वीरो नाम उत्तमप्रकृतिर् उत्साहात्मकः । स च [[अमंमोह|अमोह]]-अध्यवसाय-विनय-बल-पराक्रम-शक्ति-प्रताप-प्रभाव-प्रभृतिभिर् विभावैर् उत्पद्यते । तस्य स्थैर्य-धैर्य-त्याग-शौर्य-वैशारद्य-[[आश्लेषाशक्यादिभिरनुभावैः|अप्रतिघातादिभिरनुभावैर्]] अभिनयः

---
[[P25]]
प्रयोक्तव्यः । व्यभिचारिणश्चास्य स्मृति-मति-गर्व-वेग-औग्र्य-अमर्ष-रोमाञ्चादयः " इति ।

प्रस्वेद-रक्त-वदनत्वादि-क्रोध-अनुभाव-रहितो युद्धवीरः ; अन्यथा रौद्रः — इत्यनयोर् विवेकः । अत्रार्ये भवतः —

> उत्साहाद् अध्यवसायाद् [[द्विषादाद्|अविषादाद्]] विस्मयाद् अमर्षाच्च ।  
> त्रिविधोऽयम् एवमुक्तो वीररसो नाम सम्भवति ॥  
> 
> स्मृति-धैर्य-शौर्य-[[कात्स्न्यैर्|कार्त्स्न्यैर्]] अप्रकम्पैः प्रकर्षैश्च ।  
> वाक्यैर् आक्षेप-कृतैर् वीररसः सम्यग् अभिनेयः ॥ इति ।

[[रम्यश्चित्रं तृतीयोऽङ्कः|रम्यश्चित्रस्तृतीयोऽङ्कः]] ।

नाटके चास्मिन् प्रथमत एव [[श्रीमन्तं यतिराजं|श्रीमतो यतिराजस्य]] [[अमन्दहर्ष-पराक्रम-अतिप्रतापादयु उद्रेकप्रभावा|अमन्द-हर्ष-पराक्रम-अतिप्रतापाद्युद्रेक-प्रभावा]] अभिव्यज्यन्ते, यथा —

" भरतः — सर्वथा हि माहात्म्याढ्या यतिराजस्य, [[यद्यमेव|यद्येवं]] क्रियते । "  
नारदः — किमत्राश्चर्यम् —

> निरस्य तिमिरं भानुर् [[निर्वने|तनुते]] जगति श्रियम् ।  
> एवम् एष यतीन्द्रोऽपिस्वपदं स्थापयिष्यति ॥  
> 
> भरतः — भगवन् ! [[अनाभिजनतया|अनभिज्ञतया]] निदानम् अस्य वेदितुम् इच्छामि ।  
> 
> नारदः — देवरहस्यम् इदम् ; [[मन्त्विकतव्य्यत्र|मन्त्रिकर्तव्यम् अत्र]] रक्षणम् अर्हति ।  
> 
> [[मायाविमोहितयुगानुयुगानुसृत्यैन्|मायाविमोहित-जगद् युगपद् विमोक्तुं]]  
>    [[येनाच्युतस्य कुहनामयधर्मनुयान्|येनाच्युतस्य कुहकामय-धर्म-मार्गान्]] ।  
> [[सम्मोहयित्यु पुनरेषु मुदर्शनोऽपि|सम्मोहयितुं पुनरेष सुदर्शनोऽपि]]  
>    [[तन्नेव जेतुमधुना यतिशेखरऽभूत|तानेव जेतुम् अधुना यतिशेखरोऽभूत्]] ॥  
> 
> तद् अस्य सर्वम् अभ्यन्तर-रक्षोपायः ।

भरतः — (सहर्षम्) "तर्हि [[जिनं ब्रह्मraजन्य|जितं ब्रह्मराजन्यम्]]" — इति प्रघट्टकेन ।

---
[[P26]]
उपरि च — " त्रिदण्ड-काषाय-शिखोपवीतैः प्रसादयन् पारमहंस्य-लक्ष्मीम् ।  
वैकुण्ठम् आरोपयितुं मुमुक्षून् सोपानकारी यतिराज एषः ॥ " —  
इति [[महाराजमुखतः,|महाराज-मुखतः ;]]

" स एष खलु सकल-पाषण्ड-तिमिर-[[मण्ड-चण्डकरः|मण्डल-चण्डकरः]] चरमाश्रम-रूपी परम-कारुणिको भगवद्-अवतारः । तथाहि —

> स एष साक्षात्कृत-कृष्ण-दत्तां निक्षेप-विद्यां निरवद्य-भूमौ ।  
> गद्यात्मना [[कृष्णजनोपमान्यां|कृत्स्नजनोपयोग्याम्]] संवाद-रूपां विदधे दयालुः ॥

अस्ति खल्वेवम् [[इतिहायश्च :|इतिहासांशः,]] यदुत —

> काणाद-शाक्य-पाषण्डैर् विप्रधर्मो विलोपितः ।  
> त्रिदण्डधारिणा पूर्वं विष्णुना रक्षिता त्रयी ॥

इदानीं स एवायं स्यात् । [[अश्चद्रधानोऽपि,|अश्रद्दधानोऽपि]] दिव्यशक्त्य्-अन्यथानुपपत्त्या " स एवायम् " इति निश्चिनुयात् । " इति [[धर्मव्य|धर्मस्य]] मुखतः ;

" रामानुजस्य मति-नीति-प्रतिभा-सत्त्व-समुत्साह-[[सःपदः मर्माक्ष्य|सम्पदः समीक्ष्य]] "  
इति [[सद्रिद्यामुखतः,|सद्विद्या-मुखतः ;]]

" सम्प्रति बाह्य-कुदृष्टि-दुस्सचिवापीडितो मदाज्ञा-परिपालको वेदमौलिर् व्याकुली-भवति । तद् भवता तत्-परिपालनं कर्तव्यम् " इति, " यदुत, तदनुगुण-मति-नीति-सत्त्व-समुत्साहादि-सहाय-सम्पदं दत्त्वा रामानुजं प्रहितवान् " इति च कार्ष्णीपूर्ण-लेख-मुखतः ;

[[रङ्गप्रिय - प्रियरङ्कनामभ्याया|रङ्गप्रिय-प्रियरङ्ग-नामकाभ्याम्]] अथवा [[वाधूलदाशराथि|वाधूल-दाशरथि]]-वात्स्य-सुदर्शनाभ्याम् , " निरवद्य-निखिल-नीति-विभवं रामानुजम् " इति गीता-मुखतः, [[सदहनामकतन्त्रगल्ममुखतः,|सहदेव-नामक-तन्त्रपाल-मुखतः ;]] किं बहुना, प्रत्यर्थिभूत-शङ्कर-मुखतश्च —

> " अतिमानुषोऽयम् अस्य प्रथयत्य् आकार एव महिमानम् ।  
> [[मन्त्रिमिव मेरुमिन्द्योर्निर्मलमन्तर्गतं महारत्नम्|मन्दारम् इव मेरु-मन्दराद् अन्तर्गतं महारत्नम्]] ॥  
> 
> तद् इदम् अत्यद्भुतं ज्योतिः परैर् अनभिभवनीयम् एव । "

---
[[P27]]
इति च, श्रीमद्यतिराजस्य प्रताप-महिमादयोऽभिवर्णिता एव ।

" [[यदहम् - आत्मरामस्य मे किमोर्मनोव्यापारैरिति,|यदहम् — आप्तकामस्य मे किम् इतर-मनोव्यापारैर् इति]] मौनम् आश्रितः स्याम् ; तदा, [[कुमन्त्रिप्रभैरपहृतविषयो|कुमन्त्रि-प्रभृतिभिर् अपहृत-विषयो]] वेदमौलिः क्व पदम् आदध्यात् ? [[तन्मन्दनुसारिणी|तन्मतानुसारिणी]] परम-पुरुषार्थ-कथा, धर्म-कथा च न क्वचित् तिष्ठतीति, [[मत्सर्जिलोकसन्तापः|सर्वलोक-सन्तापः]] स्यात् । तस्माद् अनेक-जीवलोक-सन्तापाद् एक-सन्तापो वरम् — इति अस्मद्-उद्योग एव श्रेयान् " इति,

> " [[निशातनिशितकठोरधार्यैर्व्यस्य वेदमनिपक्षव्यूहैः ।|निशात-निशित-कठोर-धारैर् अस्त्रैः वेदमार्ग-विपक्ष-व्यूहैः ।]]  
> महोत्सवो विष्णुपदाश्रितानां मया विधेयो महतां जनानाम् ॥ "

इति च स्वस्य [[उद्योगोद्यौगो प्रकत्यति|उद्योगं प्रकटयति]] भगवान् यतिराजः स्वयमेव । अतः, विभाव-अनुभाव-सात्त्विक-व्यभिचारिभाव-सामग्री-समुल्लसितः स्थायी समुत्साहः, वीररसात्मना समास्वाद्यते ह्य् अनुभवरसिकैर् भावुकैर् इति, अत्र वीर एव प्रधानो रसो विराजते नितराम् ।

श्रीमति मूलमन्त्रिणि यतिराजे [[गतसमुत्साहः,|गतः उत्साहः]] राज्ञ एव फलप्रद इति निरूपितम् एव ।

प्रतिनायकश्चात्र [[चार्वाकजौद्वादिसमुत्भिन्नो|चार्वाक-बौद्धादि-समुत्भिन्नो]] मायावाद्य् एव । तस्मिंश्च दर्प-मात्सर्य-चण्डवृत्ति-विकत्थनवादयो धर्माः परिपूर्णा एव । अतः, स धीरोद्धतः ।

तान् सर्वान् अप्य् अरीन् निज-निपुण-मति-नीति-शक्त्यादिभिर् [[निग्गृह्य,|निगृह्य,]] मिथ्यादृष्टि-विमोहितं राजानं सद्धर्मचारिण्या [[महिप्या मुमत्या|महिष्या सुमत्या]] सुनीति-सहकारेण संयोज्य, [[अद्रि- नीयं|आदरणीयं]] तत्पद-वैभवं [[पुनस्सम्प्राप्यतितस|पुनः सम्प्रापयति तस्य]] वेदमौलेः कृपामात्र-प्रसन्नाचार्यो यतिसार्वभौमः । तस्य च अकुण्ठित-प्रयत्न-प्रभावतः, भगवान् वेदमौलिः, [[मन्म्राडुद्रेद्रिद्रियः|सम्राड् उदितश्रियः]] — इति सर्वम् अनवद्यम् ।

> " एको रसोऽङ्गीकर्तव्यो वीरः शृङ्गार एव वा ।  
> अङ्गम् अन्ये रसाः सर्वे कुर्यान् निर्वहणेऽद्भुतम् ॥ " —

इत्यादिना दशरूपकोक्तं नाटक-लक्षणं च सम्यक् समन्वयीकृतम् । [[सुमतिवेदमौल्योः|सुमति-वेदमौल्योः]] शृङ्गारः विप्रलम्भ-सम्भोग-उभयात्मकः साधु परिपोषं नीतः । हास्य-अद्भुत-रौद्र-बीभत्स-[^27_1]

[^27_1]: 
    विप्रलम्भो यथा —  
    मलय-पवनो मर्मच्छेदी मधुव्रत-निःस्वनः  
    [[श्रवणशूलुकपो विक्षयन्ति|श्रवण-शूल-कल्पो विक्षिपन्]] स्फुलिङ्गमयं शशी ।



[[P33]]
स्त्री-पात्रेषु — सुमतिः — पट्टमहिषी, उदार-मङ्गलगुणा, वेदान्तस्य तुल्य-शील-वयो-वृत्ता, तुल्याभिजन-लक्षणा, अनन्यार्हत्व-अनन्यशरणत्व-अनन्यभोग्यत्व-रूप-आकारत्रयसम्पन्ना सकल-लोकोज्जीवनकरी राज्ञश्चात्यन्तवल्लभा सम्यग् उपवर्णिता । तस्याः सख्यौ सुनीतिः, गीता च महनीय-मङ्गल-गुण-चरित्रे नायिका-नायकयोर् अत्यन्त-प्रणयिन्यौ, सङ्घटन-कर्मणि नितरां जागरूके समुपवर्णिते । अत्र कविः, उत्तररामचरित्रे निबद्धाः — सीता — तमसा — वासन्तिकाः, शाकुन्तले चोपनिवद्धाः — शकुन्तला — अनसूया — प्रियंवदाश्च स्मारं स्मारं, एताः सुमति-सुनीति-गीताः चित्रितवान् इति अभ्यूहितुम् उचित इव प्रतिभाति । अन्यत् सर्वं पाठक-महाशयैर् एव सहृदयैः स्वयम् अनुभूयत एव इति विस्तरभीत्या विरम्यते ।

अस्मिन् नाटके — प्रथम, द्वितीय, चतुर्थ, पञ्चम, षष्ठेषु पञ्चसु विष्कम्भाः, तृतीयाङ्के प्रवेशकश्च, वृत्त-वर्तिष्यमाणानां कथांशानां निदर्शनाय उपनिबद्धाः । तत्र, प्रथमाङ्के — " नारं ददातीति नारदः " इति व्युत्पत्त्या लोकानां विज्ञान-प्रसादको नारदः नाट्य-द्वारा पण्डित-पामर-साधारणेन विज्ञान-अमृत-सेचकाय भरताय, तन्मुखेन सर्व-लोकेभ्यश्च, यतिराजस्य सुदर्शनत्वं, तद्दर्शनस्य परमार्थत्वम्, परम-हितत्वम्, [[वेदान्तम् अत्यन्तरङ्गत्वम्|वेदान्तस्यात्यन्तरङ्गत्वम्]], तेनैव तस्य सकल-प्रत्यर्थि-निरसनेन स्वपदे व्यवस्थापनं च स्थापयतीति, सुमहान् अयम् आमोदः । चतुर्थाङ्के च — गीता-जनकयोः सम्भाषणेन, विष्णोः दिव्य-मङ्गल-विग्रहस्य अनुभवः, जीव-परयोः स्वरूप-ऐक्यम्, किन्तु स्वभाव-ऐक्यम् एव — इत्येवम् अपि प्रधान-अंशो विज्ञापित इति सुमहान् अनुग्रहश्च ॥

### ग्रन्थकर्तृ-काल-देशादि-विवरणम्

एतत्-नाटक-प्रणेता तु, " नडातूर् अम्माळ् " इति प्रसिद्धानां श्रीमतां श्रीमच्छ्रीभाष्य-प्रवचन-प्रथित-विभवानां श्रीभगवद्-रामानुजमुनि-पूर्वाश्रम-भागिनेयस्य श्रीमत्-सुदर्शनाचार्यापरनामधेयस्य श्रीमद्वत्स — वरदविष्णुगुरुतंसस्य पौत्राणां वात्स्य-वरदाचार्याणां पञ्चमा इति स्पष्टं [[तैरेवोकीर्तनात्|तैर् एवोत्कीर्तनात्]] ज्ञायत एव । [[तन्नामशौल्यादेतामपि|तन्नाम-सारूप्याद् एताम् अपि]] " अम्माळ् " इति अभिधातुं प्रवृत्ता जना इति प्रतिभाति ।

---
[[P34]]
श्रीमतां परमहंस-परिव्राजकाचार्याणां [[श्रीमदादिवण्शठकोपयतीन्द्राणां|श्रीमद्-आदिवण्-शठकोप-यतीन्द्राणां]] [[अहोबिलमठस्थापकानां|अहोबिल-मठ-स्थापकानां]] आचार्या एते । अतः चतुर्दश-शतकाब्दे काञ्चीनगर्याम् एते आसन् इति निश्चयप्रचोऽयं विषयः । नाटक-प्रस्तावनया च एतत्-सम्बन्धिनः सर्वे विशेषाः ज्ञायन्त एव ।

एभिर् एव विरचितो वसन्ततिलकभाणः परम-सुकुमार-सुभगः सकल-सहृदय-जेगीयमान-भोग्यतातिशयो [[विजयतेतमाम्|विजयतेतराम्]] । ततोऽपि एतेषां [[चारित्रकविशेषा|चारित्रिक-विशेषाः]] विज्ञातुं शक्यन्ते ।

### व्याख्यानस्य परिचयः ।

आध्यात्मिक-तत्त्व-विचार-प्रवणम् इदं वेदान्तविलासं नाटकं, अतिललितम् अपि वेदान्त-महार्थ-गर्भं, व्याख्यानम् अन्तरा न सम्यग् अवबोद्धुं शक्यते इति, तत्सम्पादने कृत-प्रयत्नोऽहं मद्रास-राजकीय-तालपत्र-पुस्तकालये ( Government Manuscript Library Madras ) R. ७९० सङ्ख्याकं कञ्चन पत्र-लिखित-श्रीकोशम् उपलभ्य, स्वयम् एव तद् अनुलिख्य, आनीय, मूलेन सह मुद्रणाय च सज्जम् अकरवम् ।

व्याख्यानस्य [[प्रतिरियमेकैव|प्रतिर् इयम् एकैव]] उपलभ्यते । इयं च [[श्रीकुरुकपूर्या ( आऴ्वार्- तिरुमर्गी )|श्रीकुरुकपूर्याः ( आऴ्वार्-तिरुमगरी )]] [[उत्तरश्रीगेहे ( वडकुकुत्तिरुमाळिगै )|उत्तरश्रीगेहे ( वडक्कुत्-तिरुमाळिगै )]] विद्यमानाया मातृकाया निष्पन्ना पुत्रिका इति,

> " Transcribed in 1912-13 from a M. S. S. of Vadakku Tirumaligai in Alwar Tirunagari "

इति तस्या मातृकाया अन्ते विलेखकस्य विलेखनेन विज्ञायते । अस्य श्रीकोशस्य परिचयः, तत्पुस्तकालय-श्रीकोश-पट्टिकायाम् एवं कृतः —

**R. No. 790. वेदान्तविलासव्याख्या — रत्नदीपिका ।**  
Paper 11 + 9 inches. Foll 26. Lines 20 in a page. Devanagari Good. Complete.

A Commentary on the Vedanthavilasa, also called Yathirajavijaya, which is a Drama in six acts based on

---
[[P35]]
the leading incidents in the life of Srimath Ramanuja Acharya. — इति ।

व्याख्यानम् इदं वेदान्त-विषय-विवेचन-परं रमणीयं संक्षिप्तं अपेक्षित-विषय-मात्र-विशदीकरण-प्रवणं [^35_1] उपलभ्यते ! केचन प्रघट्टा इतः पूर्वम् एव अस्माभिः सहृदयानां मानसोल्लासाय सन्दर्शिताः । स्थूलतः, आदितः आरभ्य आन्तं, सारतमा विषया अनुबन्धे निवेदयिष्यन्ते ।

अस्य व्याख्यानस्य प्रणेता को वा इति, तस्य काल-देशादिकं किम् इति च न ज्ञायते । प्राचीनानां महतां प्रायशो धोरणी इयम् एव हि, यत् स्व-नामादिकं न ख्याप्यते, स्व-वैभव-प्रकटनं च न सह्यते, अहङ्कार-ममकार-समर्पण-परतयेति ।

> " श्रीवेदान्तविलासस्य नाटकस्य यथामति ।  
> प्रणम्य वरदं व्याख्या क्रियते रत्नदीपिका ॥ "

इति मङ्गल-श्लोकेन प्रथमेन, " अन्तर्-वेदान्त-साम्राज्यम् " इत्यादिना द्वितीयेन च अनुबन्ध-चतुष्टयं सूचयता, स्व-अहङ्कार-निरसनं कुर्वता, इष्ट-देवतां प्रणमता, मृदु-मधुर-संक्षिप्त-भाषिणा व्याख्याकृता, अंश-द्वयम् [[परमात्र|परम् अत्र]] समुपबृंहितम् — व्याख्यानस्य नाम रत्नदीपिका इति, वरदः इष्ट-दैवतमिति च । रत्नदीपिका इति सर्वथा अन्वर्थम् इदं नामधेयम् । अयं वरदः, देवो वा, गुरुर्वा, उभौ वा । तेन वरद-दैवतोपासकः, वरदाचार्यस्य शिष्योऽयं भवति । वरदस्तु काञ्चीपुर्यां विराजमानः ; अतः ग्रन्थकर्तुर् आवासभूमिः काञ्चीपुरी भवितुम् अर्हति — इति अभ्यूहः समुचितो वेति सुधियो विभावयन्तु । एतदपेक्षया अन्यत् किमपि तद् अधिकृत्य न ज्ञायते ।

मूलस्य तु अनेका मातृका अस्मत्-पुस्तकालये, अन्यत्र च उपलभ्याः । ताभिः सह समीकृत्य, तत्रत्याः पाठभेदा [[अथो|अथ]] निवेशिताः । व्याख्यान-दर्शनेन केचन नूतनाः पाठभेदा उपलभ्यन्ते, ते, अन्ये च तत्रत्या विशेषाः सर्वे, अनुबन्धे प्रदर्शयिष्यन्ते ।

मूलस्य प्राग् एव मुद्रणस्य निष्पन्नतया व्याख्यानम् इदं अनुबन्ध-रूपेण समुद्र्यते प्रत्यक्शः । अतोऽत्र क्षम्यतां वत्सलैः पाठक-महाशयैर् इति सम्प्रार्थ्यते ।

[^35_1]: 
    "धावद्-व्याख्यानम्" उपलभ्यते ।

---
[[P36]]
### [[कृतज्ञताSSविष्करणम्|कृतज्ञता-आविष्करणम्]]

अस्य [[व्याख्यानस्यानुलेखनाय,|व्याख्यानस्य अनुलिखनाय,]] मुद्रणाय च कृपया अनुमतिं दत्तवद्भ्यः सहृदय-तल्लजेभ्यः [[मद्रासराजकीयतालपत्रपरिशोधनालयप्रधानाध्यक्षेभ्यः|मद्रास-राजकीय-तालपत्र-परिशोधनालय-प्रधानाध्यक्षेभ्यः]] [[अस्मत्सुहृ- द्वरेभ्यः|अस्मत्-सुहृद्-वरेभ्यः]] ब्रह्मश्री- T. चन्द्रशेखरन् दीक्षित ( M. A. L. T. ) महोदयेभ्यः विशिष्य कृतज्ञता निवेदनीया समस्ति ।

[[सव्याख्यानस्यास्य|सव्याख्यानस्य अस्य]] ग्रन्थस्य मुद्रणाय [[सर्वविधसौकर्यसम्पादनेनानुगृहीतवतां|सर्वविध-सौकर्य-सम्पादनेन अनुगृहीतवतां]] [[श्री तिरुमल तिरुपति देवस्थान|श्री-तिरुमल-तिरुपति-देवस्थान-]] [[धर्मकर्तृसंघसभ्यानां,|धर्मकर्तृ-सङ्घ-सभ्यानां,]] तथा [[तत्कार्यनिर्वहणाधिकारिणां|तत्-कार्य-निर्वहणाधिकारिणां]] श्री. चे. अन्नारावु महाशयानां, भूतपूर्वाध्यक्ष-पादानां श्री. प. वें. रामानुजस्वामि-महोदयानां, अद्यतनाध्यक्षाणां श्री. जी. चेन्नारेड्डि महाशयानां च सर्वथा अहम् अधमर्णः ।

तथैव सव्याख्यानस्य अस्य ग्रन्थस्य मुद्रणे महद् उपकृतवतां सर्वेषां कृते हार्दा धन्यवादाः समर्प्यन्ते । अपि च प्रच्युतो भवेयं [[मदीयाद्धर्मात्|मदीयाद् धर्मात्]], यदि विस्मरामि [[धन्यवादा- नर्पयितुं|धन्यवादान् अर्पयितुं]] [[श्री तिरुमल तिरुपति देवस्थान|श्री-तिरुमल-तिरुपति-देवस्थान-]] मुद्रणालय-[[कार्यकरेभ्यस्सौम्येभ्यः,|कार्यकरेभ्यः सौम्येभ्यः,]] विज्ञ-चूडामणये च तदधिपतये, येषां [[सम्पूर्णसहकारेणैव|सम्पूर्ण-सहकारेण एव]] [[सर्वङ्गीणरमणीयोऽयं|सर्वाङ्गीण-रमणीयोऽयं]] [[ग्रन्थौ|ग्रन्थो]] विमुद्रितो विराजते नितराम् ।

[[मानुष्यकसुलभैनानवधानेन|मानुष्यक-सुलभेनानवधानेन]] निपतितान् दोषान्, निसर्ग-दयालवः सहृदयाः मर्षयेयुर् इति, [[गुणमात्र आस्वादने|गुणमात्रास्वादने]] [[कपर भविप्यन्तीति|एकपरा भविष्यन्तीति]] च निश्चित्य तेषां विषये [[करिष्यमाणज्ञश्च|कृतज्ञश्च]] भवामि ।

श्रीवेङ्कटेश्वर-प्राच्य-शोधनालयः  
श्री सिंह (दुर्मुखि) चैत्र कृष्ण सप्तमी  
बुधवासरः  
२-५-१९५६.  

इति  
निवेदिता  
ति. कु. वे. न. सुदर्शनाचार्यः  

---
[[P37]]
श्रीः ।  
श्रीमते वेङ्कटेशाय नमः ।  
### आध्यात्मिक-नाटकेऽस्मिन् श्रीमति यतिराजविजये अभिनेयानां पात्राणां पट्टिका ।

#### पुरुषाः

| क्रमः | नाम (पात्रम्) | सम्बन्धः / परिचयः | अङ्काः | पुटसङ्ख्याः |
| :--- | :--- | :--- | :--- | :--- |
| १ | वेदमौलिः (वेदान्त.) | राजा | १, २, ३, ४, ५, ६ | ९, १७, ३०, ४८, ६१, ७८ |
| २ | यतिराजः (रामानुज.) | मूलमन्त्री | १, २, ४, ५, ६ | १०, २५, ४८, ६२, ६७ |
| ३ | धर्मः | अस्य अनुचरः | १, ६ | ११, १५, ८३ |
| ४ | यामुनमुनिः | राज्ञः आप्तमित्रम् | ३, ४, ५ | ३०, ४८, ६४ |
| ५ | पराङ्कुशः (श्रीशठकोप-दिव्यसूरिः) | परमपूज्यः | ५ | ६९ |
| ६ | सुदर्शनः (वात्स्य-वरदविष्णुः) | यतिराजस्य अन्तरङ्गशिष्यः | ५ (वि) | ६० |
| ७ | रङ्गप्रियः (वाधूल-दाशरथिः) | वैतालिकः | ३ | ३५ |
| ८ | प्रियरङ्गः (वात्स्य-वरदविष्णुः) | वैतालिकः | ३ | ३५ |
| ९ | मायावादः | प्रधान-महामन्त्री प्रतिपक्षी | २, ३, ५ | १७, ३०, ६२ |
| १० | शङ्करः | अस्य सहायः (सन्न्यासी च) | ५, ६ | ६२, ७० |
| ११ | भास्करः | मन्त्रिणः सहायः | ३, ५ | ३०, ७४ |
| १२ | यादवः | मन्त्रिणः सहायः | ३, ५ | ३०, ७२ |
| १३ | चार्वाकः | मन्त्रिणः सहायः | २ | १६ |
| १४ | सौगतः | मन्त्रिणः सहायः | २ | १६ |
| १५ | वेदविचारः (पूर्वमीमांसा) | राज्ञो वेदान्तस्य भ्राता | ६ | ८० |



[[P38]]

| क्रमः | नाम (पात्रम्) | सम्बन्धः / परिचयः | अङ्काः | पुटसङ्ख्याः |
| :--- | :--- | :--- | :--- | :--- |
| १६ | इतिहासः | अस्य सहायौ | २, ६ | २४, ८० |
| १७ | पुराणम् | अस्य सहायौ | ६ | ८० |
| १८ | [[सद्रहः|सहदेवः]] (तन्त्रपालः) | सेनापतिः | ५, ६ | ६२, ६५, ९० |
| १९ | सुतर्कः | योधः | ५, ६ | ६५, ७८ |
| २० | शब्दः | अनुचरः | ६ | ८३ |
| २१ | प्रत्यक्षादीनि प्रमाणानि | सेवकाः | - | - |
| २२ | जनकः | - | ४ (वि) | ४६ |
| २३ | कञ्चुकी | - | ३, ६ | ३५, ७९ |
| २४ | सन्न्यासी (विवरणकारः) | - | ५ | ६० |
| २५ | शुक्लपटः (वाचस्पतिः) | - | ५ | ६० |
| २६ | वादसिंहः (यादवशिष्यः) | - | ५ | ७३ |
| २७ | भास्करशिष्यः | - | ५ | ७४ |
| २८ | दिव्यपुरुषः | - | १, ६ | ७५, ९५ |
| २९ | नारदः | - | १ (वि) | ७ |
| ३० | भरतः | - | १ (वि), ६ | ७, ६६ |
| ३१ | प्रतीहारी | - | १, ५ | ९, ६० |
| ३२ | सूत्रधारः | प्रस्तावनाप्रवर्तकौ | १ (प्रस्ता) | २ — ६ |
| ३३ | पारिपार्श्वकः (नटः) | प्रस्तावनाप्रवर्तकौ | १ (प्रस्ता) | २ — ६ |

#### स्त्रियः

| क्रमः | नाम (पात्रम्) | सम्बन्धः / परिचयः | अङ्काः | पुटसङ्ख्याः |
| :--- | :--- | :--- | :--- | :--- |
| ३४ | सुमतिः (भगवद्भक्तिः) | पट्टमहिषी | ४, ५, ६ | ५२, ६५, ७८ |
| ३५ | सुनीतिः | अस्याः सख्यौ | २, ४, ५, ६ | २५, ४०, ५२, ६५, ७८ |
| ३६ | मिथ्यादृष्टिः (मोहजननी) | वेश्या | २ | १८ |
| ३७ | गीता | सुमत्याः सखी | ३ (प्र), ४ (वि) | २९, ४६, ५२ |
| ३८ | सद्विद्या | चामरग्राहिणी | ३ (प्र) | २० |

*\* वि — विष्कम्भः ; प्र — प्रवेशकः ; प्रस्ता — प्रस्तावना ।*

---
[[P39]]
॥ श्रीरस्तु ॥  
### इतरेषां आध्यात्मिकनाटकानां (Allegorical plays) पट्टिका  

| नाटकनाम | कर्तृनाम | विशेषांशः |
| :--- | :--- | :--- |
| (१) प्रबोधचन्द्रोदयः (१०५० — १११६ A. D.) | श्रीकृष्णमिश्रकृतिः (१०९७ — ११६५ A. D. कालिक ४७ कामकोटिमठाधिपति-समकालिकोऽयम्) | विष्णुपारम्यवाद्यद्वैतमतप्रबोधनकरो ग्रन्थः ; एतद्दर्शिकृत्यैव अन्यानि आध्यात्मिकनाटकानि प्रवृत्तानि सर्वाणि [^39_1] । |
| (२) सङ्कल्पसूर्योदयः (१२६८ — १३६९ A. D.) | श्रीमद्वेदान्तदेशिकपादाः | श्रीविशिष्टाद्वैतमतप्रबोधनाय आरचितोऽयम् । |
| (३) विजयञ्जननाटकम् | श्रीबिन्दुमाधवतनुजः — इन्दिराशुकविः | श्रीद्वैतमतप्रबोधकम् । |

[^39_1]: 
    \* नाटकम् इदं, अस्मत्-प्रिय-मित्र-महोदयैः सहृदय-तल्लजैः श्रीवेङ्कटेश्वर-संस्कृत-महाविद्याशालायाम् व्याकरण-शास्त्र-विभागस्य प्रधान-उपाध्यायैः [[श्रीमुळ्ळिभजनवैयाकरणशिरोमणिभिः|श्रीमुळ्ळि-भव-वैयाकरण-शिरोमणिभिः]] धीमद्भिः राममूर्त्याचार्यैः सप्रीत-बहुमानं प्रदर्शि महां प्रसन्न-सञ्ज्ञया । तेषां सर्वदा कृतज्ञोऽस्मि ।

अत्र — योग्यता, सुचरित, जिज्ञासा, मुमुक्षा, प्रयत्न, [[परनीर्यः|परमर्षिः]], गुरुप्रसादः, तत्त्वविवेकः, अचिन्त्यशक्तिः (महिषी), गुणोत्कर्षः (सहचरः), निदिध्यासनं, प्रसादः, कलिः, साम्बशिवः, चरिताभेदो, शीघ्रगतिः, चाक्षुष्यः, शकुनिः, कठोरः, मणिमन्, प्राणदासः, प्रभञ्जनः, प्रवेशकः, शङ्कर (शङ्करः), गोविन्दस्वामी, ब्रह्मदन्तः, मिथ्याप्रज्ञः, क्षेमोत्तमः, प्रज्ञातीर्थः, सत्यप्रज्ञः, प्रज्ञातीर्थः, विद्याः, विवेकः, आनन्दतीर्थः, भूरिकरुण, जनाः, उपक्रमादयः, वादिनः, अगतप्रत्ययः, प्रत्यक्षम्, मिथ्यानुमितिः, व्यावहारिकी, विकल्पः, [[त्रिक्रमचार्यः|त्रिविक्रमाचार्यः]], पुण्डरीकः, व्याघातः, प्रसादः, द्वेषः, [[अपोश्याः|अपोह्याः]], योग्याः, सङ्कल्पः ([[महामन्त्रो|महामन्त्री]]), रमानाथः (महाराजः) — इत्येवमादयः आध्यात्मिक-पदार्थाः पात्राणि ।  
(vi)

---
[[P40]]
| नाटकनाम | कर्तृनाम | विशेषांशः |
| :--- | :--- | :--- |
| (४) अमृतोदयम् | गोकुलनाथः (१६९५ A. D.) | जीवात्मनः मोक्षोदयोऽत्र अभिवर्ण्यते । |
| (५) मोहपराजयः | मोह-यशःपलः (१३०६ A.D.) | जैनमतप्रबोधकः |
| (६) श्रीदामचरितम् | समरदीक्षितः (१६८१ A. D.) | श्रीकृष्णसखस्य सुदाम्णः दारिद्र्यनिवृत्तिः अभिवर्ण्यते । |
| (७) धर्मविजयः | भूदेवशुक्लः (16th Cent. A. D.) | धर्मस्य विजयः अभिवर्ण्यते । |
| (८) चित्तवृत्तिकल्याणम् जीवन्मुक्तिकल्याणं च | भूमिनाथः (नल्लादीक्षितः) १६८४ — १७५० | अद्वैतमतप्रबोधके । |
| (९) सौभाग्यमहोदयनाटकम् | जगन्नाथशीघ्रकविः (17th Cent. A. D.) | अलङ्कारा एव अत्र पात्राणि । |
| (१०) विद्यापरिणयः ([[वेदविकृतः|वेदकविकृतः]]) | [[आनन्दरायमख्वी|आनन्दरायमखी]] (18th Cent. A. D.) | जीवात्मनः विद्यया परिणयः अभिवर्ण्यते । |

कलि-शकुनिभ्यां प्रेरितो मणिमन्-नामा दनुजः — शङ्कर (सङ्कर) भूमिकां प्राप्य, अविद्यापुरी-सौभाग्यं संवर्ध्य, सर्वमिथ्यात्वं व्यवस्थाप्य विद्यापुरीतो राजानं सपरिवारं निष्कामयति, परतीर्थादीन् तपस्विनः अविद्यापुर्यां बन्धयति च । एवं काले गते बहुतिथे, बद्धेषु जातानुकम्पो भगवान् मुख्यप्राण-वायुः, आनन्दतीर्थ-महोदयत्वेन अवतीर्णः, भेद-साम्राज्यं व्यवस्थाप्य, [[समीकरण्य|समीकृत्य]] अलङ्कृत्य च विद्यापुरीं, निरस्य शङ्करादीन् प्रतिपक्षिणः, सकल-कल्याण-गुण-गण-परिपूर्णं श्रीलक्ष्मीपतिं महाराजं विद्यानगर्यां पुनः सम्यक् प्रतिष्ठापयति ; यस्य पुरुषोत्तमस्य द्वेषेण प्रतिसञ्चरे तमःकूटे निपतितेषु अयोग्येषु, प्रसादेन च योग्या निर्भरानन्दम् अनुभाव्यन्ते " इति, वेदान्तरङ्ग-तत्त्वरहस्य-सुभगया प्रक्रियया समुपवर्ण्यते । [[अभिकमन्त्यत्र|अधिकमत्र]] ।

---
[[P41]]
| नाटकनाम | कर्तृनाम | विशेषांशः |
| :--- | :--- | :--- |
| (११) पूर्णपुरुषार्थचन्द्रोदयः | जातदेवः (18th A. D.) | [[दशाश्वधनः|दशावधानः]], आत्मनो वा [[आनन्दपक्वकवल्ल्याश्च|आनन्दवल्ल्याश्च]] परिणयोऽत्राभिवर्ण्यते । |
| (१२) शिवलिङ्गसूर्योदयः | मल्लारि आराध्यः (18th A. D.) | वीरशैवमतप्रबोधकः । |
| (१३) अनुमितिपरिणयः | नृसिंहः (18th A D) | न्यायमतप्रबोधकः । |
| (१४) शुद्धसत्त्वम् | माडभूषि-वेङ्कटाचार्यः (१८६० A. D.) | विशिष्टाद्वैतमतानुरोधि । |
| (१५) चित्तसूर्यालोकः | [[राणि-महामिच्चननरसिंहकविः|राणि-नरसिंह-कविः]] | अद्वैतवेदान्तानुयायी |
| (१६) विद्वन्मनोरञ्जनी | चिरञ्जीवि भट्टाचार्यः (रामदेवः) | अद्वैतवेदान्तानुयायी |

इत्यादीनि अनेकानि नाटकानि वर्तन्ते । [[तान्|तानि]] [[सर्वानप्यधिकृत्य|सर्वाण्य् अधिकृत्य]] प्रत्येकशो विलिख्यते मया कश्चन व्यासः ।

---
[[P42]]
## विषयानुक्रमणिका

| विषयः | पृष्ठसङ्ख्या |
| :--- | :--- |
| **I. प्रस्तावना** | **१ — ३६** |
| (१) धर्मप्रबोधने नाटकानां स्थानम् | |
| (२) आध्यात्मिक-नाटकानि | |
| (३) प्रबोधचन्द्रोदयः — तस्य वैशिष्ट्यं च | |
| (४) सङ्कल्पसूर्योदयः — तस्य वैशिष्ट्यं च | |
| (५) यतिराजविजयम् — वरदाचार्याश्च | |
| (६) [[अमुके|प्रकृते]] नाटकेऽस्मिन् केचन प्रघट्टाः | |
| (७) इतरेषां मतानां निरूपणप्रक्रिया | |
| (८) तेषां खण्डनप्रक्रिया | |
| (९) श्रीमद्-विशिष्टाद्वैत-मतस्य वैशिष्ट्यम् | |
| (१०) सर्वेषां दर्शनानां स्वरूपसङ्ग्रहः | |
| (११) नाटकेऽस्मिन् प्रधानो नायकः | |
| (१२) अत्र प्रधानो रसः | |
| (१३) पात्रपोषणम् | |
| (१४) ग्रन्थकर्तृकालदेशादिविवरणम् | |
| (१५) व्याख्यानस्य परिचयः | |
| (१६) कृतज्ञताविष्करणम् | |
| **II. अभिनेयानां पात्राणां पट्टिका** | **३७, ३८** |
| **III. इतरेषां आध्यात्मिकनाटकानां पट्टिका** | **३९, ४०, ४१** |
| **IV. यतिराजविजयम् — नाटकम् (मूलम् Text)** | **१ — ९६** |
| **V. यतिराजविजयव्याख्या — रत्नदीपिका (टिप्पणी च)** | **१ — ३८** |
| **VI. श्लोकानुक्रमणिका** | **i — ix** |
| **VII. व्याख्यानादुपलब्धाः पाठभेदाः** | **ix — x** |
| **VIII. नाटकलक्षणसङ्ग्रहः** | **१ — ७** |
| **IX. नाटकलक्षणानां समन्वयः** | **७ — ११** |
| **X. उदाहृतानि — सुभाषितानि, लोकोक्तयश्च** | **१२ — १४** |
| **XI. कठिनपददीपिका (GLOSSARY)** | **१४ — १६** |



[[P1]]
श्रीरस्तु ।  
श्रियः कान्ताय नमः ।  
श्रीमते रामानुजाय नमः ।  

## वेदान्तविलासापरनामधेयम्  
# यतिराजविजयम् — नाटकम्  

### नान्दी  

पद्मे त्वन्नयने स्मरामि सततं भावो भवत्कुन्तले  
नीले मुह्यति किं करोमि महितैः क्रीतोऽस्ति ते विभ्रमैः ।  
इत्य् उत्स्वप्न-वचो निशम्य सहसा निर्भर्त्सितो राधया  
कृष्णस् तत्-परम् एव तद् व्यपदिशन् क्रीडा-विटः पातु वः ॥ १ ॥  

किञ्च,  

> शय्या यस्य दृशा शृणोति भवति छन्दांसि यद्-वाहनम् [^1_1]  
>    लीला यस्य जगन्ति काल-कलना-मूलं च यल्-लोचनम् ।  
> निद्रा जाग्रत एव यस्य निगम-स्तौमोऽवतंसोत्पलम् [^1_2]  
>    देवः पुष्यतु रङ्ग-मङ्गल-निधिः श्रेयांसि भूयांसि नः ॥ २ ॥  

> [[ब्रह्माणप्रवीणो|ब्रह्माण्ड-प्रवीणो]] घृत-धरणिधरः क्ष्मा-समुत्क्षेप-दक्षः  
>    प्रह्लाद-ह्लादकारी मथित-बलि-बलो [[भद्रराजन्यजन्यः|भग्न-राजन्य-जन्यः]] ।  
> [[लङ्कालङ्कारहारी|लङ्का-अलङ्कारहारी]] हल-हत-कलहो [[वल्लवोत्लासकारी|वल्लव-उल्लासकारी]] [^1_3]  
>    भावी पाषण्ड-शत्रुः भवतु मधुरिपुः श्रेयसे भूयसे नः ॥ ३ ॥  

[^1_1]: मङ्गलछन्दांसि — पा. ; छन्दोमयं वाहनम् — पा.
[^1_2]: निगमस्तोमावतंसोत्पलम् — पा.
[^1_3]: लङ्काऽलङ्कारहारी — पा.

---
[[P2]]
### नान्द्यन्ते सूत्रधारः  

**सूत्रधारः** —  
> भास्वान् एष तमो निहन्ति सकल-प्रह्लादकारी शशी  
>    किं ताव् एव ? [[फलन्दिमिश्र तरवः|फलन्त्य् अद्रि-मिश्रास् तरवः]] किं नोपकुर्वन्ति नः ।  
> एवं वस्तु परोपकारि सकलं दृष्ट्वापि नष्टाशयो  
>    यः स्वार्थैकपरो भवति अयम् अहो दृष्टान्त-शून्यो जनः ॥ ४ ॥  

तथाप्य् एकाकी किं करोमि ? (*विमृश्य, सहर्षम्*) अथवा किं न करोमि ? अस्ति किल समस्त-कलासु अद्वितीयः द्वितीया मे देहः । (*नेपथ्याभिमुखम् अवलोक्य*) मारिष ! परिषदि पौरुषं ते किं न दर्शयसि ?  

**नटः** — (*प्रविश्य*)  
> उपकर्तुम् आत्मविद्याम् अनवद्यां भरत-मुख्य-मुनीच्छाम् ।  
> तव चात्त-लाभ-तुष्टः प्रत्य्-उपकरवाणि भाव ! केनाहम् ॥ ५ ॥  

**सूत्रधारः** — मारिष ! किम् अन्यद् ब्रवीमि ।  

> सुर-नर-तिर्यक्-स्थावर-देहाः सर्वेऽपि नश्वरा एव ।  
> तत्क्षणम् अपि यदि जीवेत् जीवतु देही परोपकारेण ॥ ६ ॥  

तद् [[तत्तया|मया]] सह महतीं नाटक-धुरम् [[उद्वहन्त्मानुमानं|उद्वहन्न् आत्मानं]] चरितार्थयामि ।  

**नटः** — भाव ! तन्-निवेद्यतां येन अहम् अपि चरितार्थो भवामि ।  

**सूत्रधारः** — सम्प्रति सम-समय-[[सप्तदपरिमित|सप्तति-परिमित]]-निगम-कुलमणि-मुकुट-मरीचि-मञ्जरी-रञ्जित-चरण-कमलस्य जगद्-उदय-विभव-लय-लीलस्य कमलवनी-कुच-कलश-कपोल-न-युगल-युगपन्-मिलिखित-पत्रावली-परितुष्ट-किसलय-चतुष्टयस्य [^2_1] कावेरी-तीर-तरु-तत-माल-भूरुहस्य विभीषण-आराधित-पाद-पङ्कजस्य भुजङ्ग-भोग-पर्यङ्क-शायिनः श्रीरङ्गराजस्य चैत्र-उत्सव-यात्रायाम् , आत्मविद्या-[[विद्ग्यैः|विद्भिः]] अनवरत-निरवद्य-भरत-विद्या-विनोदैर् आर्य-मिश्रैर् आदिष्टोऽस्मि ; यदुत, "अस्ति खलु भगवद्-रामानुजमुनेः पूर्वाश्रम-भागिनेयः श्रीवत्स-कुल-चूडामणिः अखिल-परदर्शन-मद-[[मददर्शनः|मर्दनः]] सुदर्शनो  

[^2_1]: कावेरीमध्यमरकतमणिभूषणस्य — पा.

---
[[P3]]
### प्रथमोऽङ्कः  

> [[सङ्कुर्वता|सत्कुर्वता]] संसदि शिष्य-वर्गान् अन्य-लभ्यैर् अखिलैर् मयूखैः ।  
> श्रीभाष्य-सिंहासनम् आत्मनीनम् यस्मै च दत्तं यतिशेखरेण ॥ ७ ॥  

> तस्य वेदान्त-कूटस्थः पौत्रोऽभूद् वरदो गुरुः ।  
> श्रुतप्रकाशिकाद्याश्च ग्रन्था यच्छिष्य-सम्पदः ॥ ८ ॥  

तस्य पञ्चमः प्रपञ्च-विदित-वैदुष्यः काञ्चीपुरी-वास्तव्यः [[श्रोधटिकाशत|श्रीघटिकाशत]]-सुदर्शनाचार्य-सूनुः श्रीवेदान्ताचार्य-रामानुजाचार्ययोः दर्शन-स्थापनाचार्ययोः प्रसाद-[[भूमिर्र्वरदाचार्यो|भूमिर् वरदाचार्यो]] नाम कविः ; तद्-विरचितं [^3_1] नाटकम् अस्माकं श्रोत्र-पदवीम् आनन्दयति ; तेन नेत्र-पदवीम् अपि [[आनन्दयेत्र|आनन्दयेत]] " — इति ।  

**पारिपार्श्वकः** — (*विचिन्त्य*) तद् अभिनेतव्यम् इति उक्तम् ; भवतु नाम ; किं नाम नाटकस्य ?  

**सूत्रधारः** — (*विमृश्य*)  
> चित्रकूट-नटे रामः चित्रभानौ चकार यत् ।  
> [[सीतालायटे|सीताललाटे]] तन्-नाम स्वरसं सिद्धम् एव तत् ॥ ९ ॥  

**नटः** — (*विचार्य सहर्षम्*) ललाटे कृतं हरिताल-तिलकम् एव ; [[तस्य स्वरैः|तदक्षरैः]] "यतिराजविजयम्" इति सिद्धम् एव तन्-नाम ।  

**सूत्रधारः** — साधु, सम्यक् प्राज्ञोऽसि ।  

**नटः** — तस्य तर्कशूरस्य निकाम-कर्कशा वाणी, [[सायतन|सायन्तन]]-समय-समुल्लसित-मालती-मकरन्द-परिमल-मुचि सहृदय-जन-हृदयानन्द-कन्द-सिरा-वेधिनि सारस्वत-परम-सीम्नि [^3_2] नाटक-महिम्नि कथम् इव पदम् आधातुम् अर्हति ?  

**सूत्रधारः** — (*विहस्य*) मारिष ! [[मैवाशाङ्कनीयम्|मैवाशङ्कनीयम्]] ।  
> शास्त्रेषु शस्त्र-परुषा अपि नाट्य-मार्गे  
>    कर्णामृतानि च भवन्ति कवीन्द्र-वाचः ।  

[^3_1]: तद्विरचितं " वेदान्तविलासं " नाम नाटकम् — पा.
[^3_2]: सारस्वतपरमसीम्नि — पा.

---
[[P4]]
> दैत्येन्द्र-शैल-कुलिशं [[दयितनितम्बे|दयिताकपोले]] [^4_1]  
>    नाथस्य [^4_2] [[कोमलममुदाहरणं|कोमलमभ्युदाहरणं]] नखं नः ॥ १० ॥  

**नटः** — साधु निदर्शितं भावेन ।  
> नावैक्षत [[स रुष्टभीनहरिभिन्दन|स रुष्टभीमहरिर्भिन्दन्]] द्विषन्तं नखैः  
>    चक्रं तच्-चटुल-स्फुलिङ्ग-कलिका-चक्रं नृचक्रं च तत् ।  
> रिपु-[[त्रशनशङ्करोद्धनिविडासंम्याससङ्घान्तर-|त्रासन-शङ्करोद्धत-निविडासन्न-असि-सङ्घान्तर-]]  
>    स्यातोच्चाण्डिम-[[भोरु|भूरि]]-डिण्डिम-मिलच्-छुण्डाल-घण्टारवम् ॥ ११ ॥  

(*सविनयम् अञ्जलिं बध्वा*)  
> [[बाञ्छां|वाञ्छां]] ते परिपूरयन्तु वदने कण्ठीरवस्य प्रभोः  
>    वैकुण्ठस्य विदारितारि-विगलद्-रक्तानुषक्ता नखाः ।  
> वक्षःपीठ-विशाल-शैल-कटकोक्रीडा-किरातीभवल्-  
>    [[ललक्ष्मीकेशककर्णपूर|लक्ष्मीकेश-कर्णपूर]]-कलिका-लाक्षारसाङ्काङ्कराः ॥ १२ ॥  

**सूत्रधारः** — (*सानन्दम्*)  
> शास्त्राणाम् अधिदेवताश्च निपुणाः पात्राणि रङ्गोऽप्ययम्  
>    रङ्गो यत्र स विश्व-नाटक-गुरुः जागर्ति [^4_3] निद्रां विना ।  
> सभ्या भाव-सहानुभूति-चतुराः [[सर्वैऽभिनेये|सर्वम् अभिनेये]] वयं  
>    सर्वं सिद्ध्यति वेदमौलि-चरिते तन्-नाट्य-विद्या-फलम् ॥ १३ ॥  

**नटः** — (*विचिन्त्य*) वस्तुतस् तावद् अवलोकतया, रङ्गस्य कथं प्रियो भविष्यसि ? इति पर्याकुलोऽस्मि ।  

**सूत्रधारः** — मारिष ! मैवं पर्याकुलो भव । पश्य,  
> सुर-नर-पशु-भूमिकां प्राप्य तत्तद्-दशाम् अद्भुताम्  
>    अभिनय-निपुणोऽयम् अध्यक्षयन् प्रेक्षकाणां सताम् ।  

[^4_1]: दयिताकपोले — पा.
[^4_2]: नाथस्य भूषणम् — पा.
[^4_3]: शेते पुराणो युवा — पा.

---
[[P5]]
> विहरति भरतप्रियश्चायम् अस्माभिर् अपि ततः ।  
> [[मधुरिपुरथादमेवापरो|मधुरिपुर् अथवा अयम् एव]] नास्ति रङ्गप्रियः ॥ १४ ॥  

किञ्च,  

> विगुणीकृताऽपि मुग्धैः सदसि गुणग्राहिभिस्तज्ज्ञैः [^5_1] ।  
> मुक्तावलीव हृद्या सम्यक् सन्धीयते विद्या ॥ १५ ॥  

तद् भवता [[पात्रत्वादिताणि|पात्राणि]] सजीक्रियन्ताम् । किन्तु, देवतारूपत्वात् पात्राणाम् अस्मिन् प्राकृते नाटके किम् अप्य् असंस्कार-परिपूत-वचन-पात्रीकरणं किञ्चित् क्लिष्टम् एव । अहं च ब्रह्मसृष्टौ भरतोऽस्मि, तद् अप्रमत्तानि पात्राणि स्वीकर्तव्यानि । (*विचिन्त्य*)  

> आलोल-स्तनभार-हार-[[मधुरोणीरणन्मेखलं|मधुर-श्रोणी-रणन्-मेखलं]]  
>    हस्तेन आकुल-कङ्कणेन [[महतमव्याज्जगतामृणम्|महताम् अव्याद् जगताम् अयम्]] ।  
> साकूत-स्मितम् ईक्षितं कमलया सञ्जात-पुम्भावया  
>    नारी-रूपम् इदं तनोतु कुशलं नारायणस्य प्रभोः [^5_2] ॥ १६ ॥  

तन्-नाट्यावसरे द्रष्टाऽसि । [[परिषद्|परिषदं]] तावत् प्रसादयामि ।  

(*इति परिकृत्य अवलोक्य, साञ्जलिबन्धम्*)  
> नीतो [[मयाऽद्य|मयाद्य]] निगमन्त-मद-द्विपोऽयं  
>    रङ्गस्थलं रचित-नाटक-संविधानम् ।  
> नृत्यन् निरङ्कुश-गतिर् निज-सूत्र-मार्गे  
>    [[किञ्चिद्यदि|किञ्चिद् यदि]] स्खलति सह्यम् इदं सदस्यैः ॥ १७ ॥  

(*समन्ताद् अवलोक्य*)  
> सरल-वकुलाभिरामः श्रुतिधुनि-ष्यन्दिशुक-मुखालापः ।  
> वहति [[हरितश्चमुखैः|हरितः सुमुखैः]] शाखा-कोटिषु महागम-स्तोमः ॥ १८ ॥  

तावद् अमुम् एव तीर्थीकृत्य माधव-समयं निरूपयामि । (*विलोक्य, सानन्दम्*)  

[^5_1]: गुणग्रहणलम्पटैस्तज्ज्ञैः — पा.
[^5_2]: नारायणस्याद्भुतम् — पा.



[[P6]]
> सुर-सुमनः-प्रबन्धाः श्रुतिसुभग-[[वपुष्षट्पदालापाः|वपुष्-षट्पदालापाः]] ।  
>    [[माधवममयविलासा|माधव-समय-विलासा]] मद्ययन्ति मनांसि किं [[पुनस्सुदृशाम्|पुनः सुदृशाम्]] ॥ १९ ॥ [^6_1]  

**नटः** —  
> [[वसनलक्ष्मीलाक्षाङ्कमुद्रा|वसन्त-लक्ष्मी-लाक्षाङ्क-मुद्रा]] इव द्रुमैः ।  
>    पूजिताः पुष्प-सन्दोहैः प्रियन्ते मूर्ध्नि पल्लवाः ॥ २० ॥  
(*इति निष्क्रान्तः*)  

**सूत्रधारः** — (*पुरोऽवलोक्य, सहर्षम्*)  
> त्रिभुवन-महनीयस् तेजसाम् एकराशिः  
>    निज-जन-मति-सिद्धं निह्नुवानं प्रपञ्चम् ।  
> परिमृषित-विवेकं स्फारम् अप्य् अन्धकारं  
>    विघटयति मयूखैः वेदरूपो विवस्वान् ॥ २१ ॥  

(*नेपथ्ये*)  
साधु, भरतपुत्र ! सत्यवचनो भव ; त्वद्-वचनम् अस्माकम् उपश्रुतिर् अपि साक्षाच् छुतिर् एव ; यद् इदानीम् —  

> सर्वैर् [[सर्वैर्विलुतविषयः|विलुप्त-विषयः]] सचिवैः पुरस्तात्  
>    [[सभ्यग्विचिन्त्य|सम्यग् विचिन्त्य]] सचिवेन यतीश्वरेण ।  
> सम्पादितः [[स्वपदवैभवमद्वितीयं|स्वपद-वैभवम् अद्वितीयं]]  
>    सम्राड् असौ खलु भविष्यति वेदमौलिः ॥ २२ ॥  

**सूत्रधारः** — (*श्रुत्वा, सहर्षम्*) अहम् अप्य् अमुना सम्भूय तद् एव अनुसन्धास्यामि ।  
(*इति निष्क्रान्तः*)  

#### इति प्रस्तावना ।  

[^6_1]: समयैः — पा.

---
[[P7]]
## प्रथमोऽङ्कः  

(*ततः प्रविशति नारदो भरतश्च*)  

**नारदः** — "सर्वैर् विलुप्त-विषयः ..." (*इतिपुनस्तदेव पठति*)  
**भरतः** — सर्वथा हि महिमातिशयो यतिराजस्य, [[यद्यमेवं|यद्येवं]] विधास्यति ।  
**नारदः** — किमत्राश्चर्यम् ?  

> निरस्य तिमिरं भानुः [[निधते|विधत्ते]] जगति श्रियम् ।  
>    [[एवमेनं|एवम् एष]] यतीन्द्रोऽपि स्वपदे स्थापयिष्यति ॥ २३ ॥  

**भरतः** — भगवन् ! अनभिज्ञतया निदानम् अस्य वेदितुम् इच्छामि ।  
**नारदः** — देवरहस्यम् इदम् ; सात्त्विकाद् अन्यत्र रक्षणम् अर्हति ।  

> [[मायाविमोहितसुरानसुरानलावीद्|मायाविमोहित-जगद् युगपद् विमोक्तुं]]  
>    [[येनाच्युतस्य कुहना मयमयधर्मानुयान्|येनाच्युतस्य कुहकामय-धर्म-मार्गान्]] ।  
> [[सम्मोहयितु|सम्मोहयितुं]] पुनरेष सुदर्शनोऽपि  
>    [[तानेव जेतुमधुना|तानेव जेतुम् अधुना]] यतिशेखरोऽभूत् ॥ २४ ॥  

तद् अस्य [[सर्वमीदृशकरमवधारय|सर्वम् ईदृशं कर्मावधारय]] ।  

**भरतः** — (*सहर्षम्*) तर्हि जितं महाराजेन ।  
**नारदः** — (*विचिन्त्य, सबहुमानम्*)  

> सर्वस्यापि हितं ब्रवीति समयाचारान् करोति स्थिरान्  
>    [[मायाजीवपरानयं|माया-जीव-परान् अयं]] न सहते [[मानप्रतापोन्नततः|मान-प्रतापोन्नततः]] ।  
> सम्मान्यस् सकलासु नीतिषु [[महामत्त्वः|महासत्त्वः]] स्थिराङ्गो युवा  
>    तस्मान् नेतृषु [[वेदमौलिसदृशो|वेदमौलि-सदृशो]] नांन्योऽस्ति कश्चिन् नृपः ॥ २५ ॥  

तथाप्य् एनम् अन्ये परिभवितुम् ईहन्ते — इति महद् आश्चर्यम् ।  

**नारदः** — किमत्राश्चर्यम् ? परिभूता एव महाराज-विषयाः [[परसम्यनासीरैः|परसमय-नासीरैः]] ।  
**भरतः** — (*सभयकौतुकम्*) किं मूलम् एतेषां सम्भूय समुत्थानस्य ?  
**नारदः** — वत्स ! साधु पृष्टं भवता । सन्ति खलु महाराजस्य प्रत्यक्षादयो महामात्याः ।  
**भरतः** — सन्त्य् एव ; येष्वेव प्रमाण-बुद्धिर् महाराजस्य ।  

---
[[P8]]
**नारदः** — तत्कुलीना [[दुर्मनयः|दुर्मन्त्रिणः]] केचित् प्रत्यक्षाभासाः । तैर् एव वैकल्यतया निरस्ताः प्रत्यन्तवासिनः पाषण्डमयान् आश्रिताः । ते च, तैः प्रोत्साहिताः, तान् एव तीर्थीकृत्य दुर्विनीता महाराज-विषयं व्याकुलयन्ति ।  

**भरतः** — (*सोद्वेगम्*)  
> [[अल्पोऽपि रिपुगक्रमन असह्यः|अल्पोऽपि रिपु-प्रक्रमोऽसह्यः]] खलु मानिनाम् ।  
>    [[नेले|नेत्रे]] पराग-लेशोऽपि [[निपतन|निपतन्]] कुरुते रुजम् ॥ २६ ॥  

ततः किं प्रतिपन्नं देवेन ?  

**नारदः** — (*सनिर्वेदम्*) किम् अन्यत् प्रतिपद्यते ? इदं प्रतिपन्नम् । ततस् तेभ्यः परप्रतारण-निपुणमतिः कश्चिद् आगत्य मायावी विरचित-विरक्त-वेषो [[वैदिकप्रथमुत्पाद्य|वैदिक-पथम् उत्पाद्य]] क्रमेण [[मन्त्रि पदमवलम्ब्य|मन्त्रि-पदम् अवलम्ब्य]] [[महाराजमलीकरुचिमकरोत्।|महाराजम् अलीक-रुचिम् अकरोत् ।]] स्वामिशीलम् अनुवर्तमानैर् [[इतिहामपुराणैश्च|इतिहास-पुराणैश्च]] तथैव प्रतिपन्नम् ।  

**भरतः** — (*सभयनिर्वेदम्*) हा ! [[कथमपतितम् ! कथमन्यकूपे|कथम् आपतितम् ! कथम् अन्धकूपे]] निपतितो जीवलोकः —  
> परिभवति हि भानुं पावकं वा अन्धकारः  
>    भवति च परिभूतः [[पामरैज्ञःनरोगिः।|पामरैर् ज्ञान-राशिः ।]]  
> [[कलिकलुषमतीनां का गतिर्मानवानां|कलि-कलुष-मतीनां का गतिर् मानवानां]]  
>    [[भवजलधिगतानां पारलाभः कथं वा|भव-जलधि-गतानां पार-लाभः कथं वा]] ॥ २७ ॥  

**नारदः** — वत्स ! मा भैषीः । प्रकृतिनिर्मले स्फटिकमणौ [[परकृतोपरागः|पर-कृत-उपरागः]] कियच्चिरं तिष्ठति ? पश्य,  
> पौलस्त्येन यथा पुरा रघुपतिर् मायाविना वञ्चितः  
>    भूयस् तं विनिहत्य [[शङ्करगिरिः|शङ्कर-गिरिः]] स्फूर्जत्-प्रतापोन्नतम् ।  
> स्वामी नः [[श्रुतिमौलिरेष विजयी|श्रुतिमौलिर् एष विजयी]] रामानुजस्यौजसा  
>    साम्राज्यं भरतादि-भोग्य-विभवं सत्यं तथा धास्यति ॥ २८ ॥  

**भरतः** — (*सप्रश्रयम्*) सत्यम् अस्तु ; [[भरतोऽस्मीति|भरतोऽस्मीति]] [[ममाप्ययमशीर्वादः|ममाप्य् अयम् आशीर्वादः]] ।  
**नारदः** — [[मर्मिह|वयम् इह]] श्वेतद्वीप-वासिभ्यो निवेदयावः ।  
(*इति निष्क्रान्तौ*)  

#### इति विष्कम्भः ।  

---
[[P9]]
### प्रथमोऽङ्कः  

(*ततः प्रविशति राजा*)  

**राजा** — (*विमृश्य*) सम्प्रति, मन्त्री मायावादः [[समयान्तरमदहरणशुण्डीरः|समयान्तर-मद-हरण-शुण्डीरः]] ; तथापि,  
> मान-अर्थ-तत्त्व-हीनो [[मायाजीवी|माया-जीवी]] महा-मृषावादी ।  
> [[सुमतिसुनीतिद्वेषी|सुमति-सुनीति-द्वेषी]] (*निश्वस्य, सखेदम्*)  
>    [[मामप्येवं करोति|माम् अप्य् एवं करोति]] किं कुर्मः ॥ २९ ॥  

(*विमृशन्, विहस्य*)  
> [[मेदोपजीव्यपि|मेद-उपजीव्य् अपि]] भिनत्ति तम् एव मेदं  
>    मानं प्रतिक्षिपति मानपरायणोऽपि ।  
> सोऽयं प्रमाण-पुरुषैः [[स्वकरोपनीतान्|स्व-कर-उपनीतान्]]  
>    मिथ्येति वक्ति मिषतोऽपि हरन् महार्थान् [^9_1] ॥ ३० ॥  

[[तदल किं प्रतिविधेयम् ?|तद् अलं, किं प्रतिविधेयम् ?]] (*विचिन्त्य*) तावद् [[यावदस्म- दनुकूलोऽन्यो|यावद् अस्मद्-अनुकूलोऽन्यो]] नीतिशाली कश्चित् [[तत्पदे निवेशितस्स्यात्|तत्-पदे निवेशितः स्यात्]] ; अन्यथा, [[मामशरणयो|माम् अशरणं]] जीवग्राहं गृह्णीयुः ।  

**प्रतीहारी** — (*[[प्रविशत्य|प्रविश्य]]*) देव ! महामात्यो मन्त्रशालायां [[युष्मदागमनमाकाङ्क्षन्|युष्मद्-आगमनम् आकाङ्क्षन्]] तिष्ठति । [[भास्करयादवौ|भास्कर-यादवौ]] च तथैव ।  

**राजा** — (*विचिन्त्य*) अथवा, सम्प्रति किं विचारेण ? सर्वम् इदं प्राग् एव [[प्रियसृहृदा|प्रिय-सुहृदा]] यामुनेन सूचितम् एव । [[इदानीमयमनुसरणीय|इदानीम् अयम् अनुसरणीय]] एव । (*पुरोऽवलोक्य*) —  
> त्रिदण्ड-काषाय-शिखोपवीतैः  
>    प्रसादयन् [[पारमहंस्यलक्ष्मीम्।|पारमहंस्य-लक्ष्मीम् ।]]  
> [[वैकुण्ठमारोपयितुं|वैकुण्ठम् आरोपयितुं]] मुमुक्षून्  
>    सोपानकारी यतिराज एषः ॥ ३१ ॥  
(*इति निष्क्रान्तः*)  

[^9_1]: ममार्थां — पा.

---
[[P10]]
(*ततः प्रविशति रामानुजः*)  

**रामानुजः** — (*सखेदम्*)  
> वासो मुक्त-पटच्चराणि वसतिर् मूले तरोर् भोजनं  
>    [[भिक्षाऽस्तस्त नवा|भिक्षा हस्त-गता]] [^10_1] जलं तु सुलभं त्यक्तास् समस्तेषणाः ।  
> वर्गेषु त्रिषु निस्पृहो भवति न्यस्तात्मभारोऽपि सन्  
>    चिन्ता-दन्तुर-मानसोऽस्मि [[सचिवश्चीवेदमौलेरहम्|सचिवः श्रीवेदमौलेर् अहम्]] ॥ ३२ ॥  

यद् अहम् "आत्मारामस्य मे किम् इतर-मनोव्याक्षेपैः" इति [[मौनमास्थितस्स्याम्|मौनम् आस्थितः स्याम्]] ; तदा [[कुमन्त्रिप्रभैरपहृतविषयो|कुमन्त्रि-प्रभृतिभिर् अपहृत-विषयो]] [[वेदमौलिः क्व पदमादध्यात् ?|वेदमौलिः क्व पदम् आदध्यात् ?]] ततस् तदन्-उसारिणी परम-पुरुषार्थ-कथा धर्म-कथा च न क्वचित् तिष्ठतीति [[सकलजीवलोकसन्तापस्स्यात्।|सकल-जीव-लोक-सन्तापः स्यात् ।]] [[वरमित्यस्मदुद्योग|वरम् इति अस्मद्-उद्योग]] एव श्रेयान् । (*स्पर्शम् अभिनयन्, सानन्दम्*)  

> [[मदन्तस्सन्तापं|मद्-अन्तः-सन्तापं]] शमयितुम् अलं रङ्गनगरी-  
>    समीराः [[कावेरिशिशिरलहरीशीकरमुचः।|कावेरी-शिशिर-लहरी-शीकर-मुचः ।]]  
> समुत्पुष्यल्-लक्ष्मी-स्तनतट-पटीरद्रव-मिलन्-  
>    मुकुन्दोरः-क्रीडारसिक-तुलसी-सौरभ-मुषः ॥ ३३ ॥  

(*परितोऽवलोक्य*) [[न कश्चिद्राजकुलादभ्येति।|न कश्चिद् राजकुलाद् अभ्येति ।]] अस्माभिः प्रहितो धर्मश्च विलम्बते ।  

(*ततः प्रविशति धर्मः*)  

**धर्मः** — (*पुरोऽवलोक्य*) अहो ! अतिरमणीयम् इदम् उद्यानम् । अत्र हि —  
> [[फलकुसुमविनम्रपार्श्वशाखो|फल-कुसुम-विनम्र-पार्श्व-शाखो]] [[मुनिजनसेवितमूलवेदिबन्धः।|मुनिजन-सेवित-मूल-वेदि-बन्धः ।]]  
>    रमयति हृदयं [[रसालपोतो|रसाल-पोतो]] मधुरकर-गीत-मनोज्ञ-कृष्ण-लीलः ॥ ३४ ॥  

(*पुरोऽवलोक्य, सविनयम् अञ्जलिं बध्वा*) स एष खलु [[सकलपाषण्ड-|सकल-पाषण्ड-]] [[तिमिरमण्डलचण्डकरः|तिमिर-मण्डल-चण्डकरः]] [[चरमाश्रमरूपी|चरमाश्रम-रूपी]] [[परमकारुणिको|परम-कारुणिको]] [[भगवदवतारः|भगवद्-अवतारः]] ।  

[^10_1]: पच नवा — पा.



[[P11]]
तथाहि —  

> स एष साक्षात्कृत-कृष्ण-दत्तां निक्षेप-विद्यां निरवद्य-भूमौ ।  
>    गद्यात्मना [[कृष्णजनोपयोग्यां|कृत्स्नजनोपयोग्याम्]] संवाद-रूपां विदधे दयालुः ॥ ३५ ॥  

(*स्मृतिम् अभिनयन्*) अस्ति खल्वेवम् इतिहासांशः । यदुत —  

> काणाद-शाक्य-पाषण्डैः त्रयीधर्मो विलोपितः ।  
>    त्रिदण्डधारिणा पूर्वं विष्णुना रक्षिता त्रयी ॥ ३६ ॥  

इदानीम् अपि स एवायं स्यात् । अश्रद्दधानोऽपि दिव्यशक्त्य्-अन्यथानुपपत्त्या स एवायम् इति निश्चिनुयात् ।  

**यतिराजः** — (*विमृश्य*)  
> सा विद्या नैव हृद्या रमयितुम् अधुना या न [[विद्याद्विधा- विध्वस्तान्त्रस्तमस्तात्|विद्या-द्विधा-विध्वस्तान्तस्-तमस्-तात्]]  
>    भवति यदि वा सम्मतं कर्म तत्तत् ।  
> संसारे वीतसारे क्षपति यद् अवशं चिन्तया किं तया वा  
>    या निष्णाता न पुष्णात्य् [[पुष्णात्युदनिषत्सञ्चरिष्णौ|उपनिषत्-सञ्चरिष्णौ]] च विष्णौ ॥ ३७ ॥ [^11_1]  

(*पुरोऽवलोक्य, सहर्षम्*)  
> हितस्य करणात् नित्यम् अहितैभ्यो निवारणात् ।  
>    मातुरप्य् अधिको बन्धुः प्राप्तो धर्मोऽयम् आत्मनाम् ॥ ३८ ॥  

**धर्मः** — (*उपसृत्य*) अयम् अहम् उपनतोऽस्मि ।  
**यतिराजः** — (*सादरम्*) धर्म ! [[इद्मासनमुपविश्यताम्|इदम् आसनम् उपविश्यताम् ।]]  
**धर्मः** — भगवन् ! अलम् अत्यादरेण । (*इति भूमाव् उपविशति*)  
**यतिराजः** — अपि दृष्टो राजा वत्सेन ?  
**धर्मः** — (*सविषादम्*) राहु-गृहीतो रजनीकरः कथं दृश्यते ?  
**यतिराजः** — कोऽसौ पाप एवम् आचरति ? (*विचिन्त्य, विहस्य*) न दृष्टः किं नरपतिः ?  

[^11_1]: नियन्त्रणात् — पा.

---
[[P12]]
**धर्मः** — न केवलम् एतावत। ।  
**यतिराजः** — किम् अन्यत् ?  
**धर्मः** — राजद्वारे [[कैश्चिन्मुण्डितैर्कदण्डिभिर्निरङ्कुशैराकोशन्नेव|कैश्चिन् मुण्डितैर् एक-दण्डिभिर् निरङ्कुशैर् आकोशन्न् एव]] ताडितोऽहम् आगतोऽस्मि ।  
**यतिराजः** — (*सदयं पाणिना परामृशन्*) वत्स ! किं तान् प्रत्यभिजानासि ?  
**धर्मः** — कथं न जानामि ? कतिपय-वत्सरान् अस्मद्-भृत्या एव हि ते ।  
किञ्च,  

> येनैव [^12_1] कण्ठपाशेन यज्ञ-दानादि-कर्मसु ।  
>    प्रगृह्य पशुवन् नीता वयं तद् गृह्यताम् इति ॥ ३९ ॥  

तैर् एवाच्छिद्य गर्ते निक्षिप्तं यज्ञोपवीतं मे दर्शितम् ।  
**यतिराजः** — (*विहस्य*) सम्प्रत्य् एव हि ते पशवः, यत् सर्वाश्रम-जीवितं ब्रह्मसूत्रं परित्यजन्ति । (*विचिन्त्य*)  

> [[नाप्यैः|नाल्पैः]] परिभूयन्ते [[नघरण्यं|नग-शरणः]] पुमान् अपि ।  
>    तं विना धीरसत्त्वैस् तैः चिरं परिचिनोति यः ॥ ४० ॥  

एवं धर्म-देहः खलु [[यतीनीन्द्रः|यतीन्द्रः]] सालावृकेभ्यः प्रयच्छति । वत्स ! विषादस् त्यज्यताम् । सम्प्रति सकल-दुरवगाहे राजकुले लब्धावकाशोऽस्मि । किञ्चित् क्षम्यताम् । धूर्त-सचिव-निर्धूतं राजकुलं यथावस्थितं करोमि । सत्यम् एव एतद् अवधारय ।  

**धर्मः** — (*सपरितोषम्*) राम इव रामानुजस् त्वम् अपि सत्यवचनो भविष्यसि । किन्तु, यावद् अस्य स्वरूपसत्तापि [^12_2] पाद-मात्रेण [[विषसक्तवन्न|विषसिक्तवन् न]] लुप्येत, तावद् उद्योगः क्रियताम् ।  

**यतिराजः** — वत्स ! मा भैषीः ।  

[^12_1]: येन वैकुण्ठपाशेन — पा.
[^12_2]: व्यावहारिकसत्ताऽपि — पा.

---
[[P13]]
**धर्मः** — (*समन्ताद् अवलोक्य, सानन्दम्*)  
> वाचा रञ्जयितुं जगत् व्यवसितं वाचंयमैः कोकिलैः  
>    मन्दं वाति समीरणोऽपि [[पुलकोद्भेदप्रानुमेयागमः|पुलकोद्भेद-अनुमेयागमः]] ।  
> निश्शेष-च्युत-पर्ण-सञ्चयतया निष्प्राण-कल्पं वनं  
>    भूयोऽप्य् उन्मिषतीव [[दृष्टिगुलभैः|दृष्टि-सुलभैः]] पुष्प-प्रवालोद्द्रुमैः ॥ ४१ ॥  

**यतिराजः** —  
> सुशीतलाः समीराः श्रुति-मधुरा बाल-कोकिलालापाः ।  
>    तरवोऽपि पुष्प-सुभगा माधव-समयोऽयं [^13_1] कस्य बहुमान्यः ॥ ४२ ॥  

**धर्मः** — (*स्वगतम्*) [[विष्णुमयाश्रयमाकाङ्क्षतो|विष्णुमयाश्रयम् आकाङ्क्षतो]] मे यतिराज-वचनं मङ्गलं सूचयति । (*पुरः पश्यन्, प्रकाशम्*) सर्वकष-प्रतापा खल्वियं वैष्णवी वेला, यद् इदानीम् —  

> [[कृष्टिभिश्चोळकमूर्खैश्चश्रुतिकदूंक्तिभिः|कुदृष्टिभिश्च चोळ-कु-मूर्खैश्च श्रुति-कटूक्तिभिः]] ।  
>    तेजसा दुर्निरीक्षोऽयं वैष्णव-समयोऽभिजित् ॥ ४३ ॥  

किञ्च,  

> छाया मूलम् उपैति [[पान्थद्वियं|पान्थ-द्वयं]] [[श्रान्ताऽऽतपाद्|श्रान्तातपाद्]] भूरुहाम्  
>    मज्जत्य् अम्भसि भास्करः प्रतिफलन्-मध्याह्न-तापाद् इव ।  
> [[आशामानमपि|आशामुखम् अपि]] क्वचिन् मरुताम् आमूलम् उष्णं जलम्  
>    मन्ये सम्प्रति मध्यमेन महता भूतेन सृष्टं जगत् ॥ ४४ ॥  

**यतिराजः** — साधु, सम्यग् उत्प्रेक्षितम् । विष्णु-पदे दीयतां दृष्टिः ।  

> मूर्त्या मध्यमया कयापि भरितं [[मूर्च्छन्मुखद्वेष्या|मूर्च्छन्-मयूख-द्विषा]]  
>    तेजस् तत्-पद-मध्य एव विकिरन्स् तीव्राभिर् अंशु-करैः ।  
> मध्यस्थः परितो [[निपेतमधुभिर्भास्वानुपास्यसुरैः|निपीत-मयूखैर् भास्वान् उपास्यः सुरैः]]  
>    माद्यन्-मध्यम-वेद-गन्ध-सुभगो मध्येदिनं दीप्यते ॥ ४५ ॥  

[^13_1]: माधवसमये न कस्य बहुमानः — पा.

---
[[P14]]
(*विचिन्त्य*)  
> [[जगच्चक्षुरिदं|जगच्-चक्षुर् इदं]] [[ज्योतिरन्तःज्ञानमनामयम्|ज्योतिर् अन्तः-ज्ञानम् अनामयम्]] ।  
>    वैष्णवैर् एव तेजोभिः वर्धते दीप्त-तारकम् ॥ ४६ ॥  

**धर्मः** — अन्यथा, कथम् ईदृशोऽनुभावः स्यात् ?  
**यतिराजः** — [[परमव्योम्नस्तरङ्गादिवादददपि|परम-व्योम्नस् तरङ्गादि-वद् अपि]] परम-पुरुषस्य विशेष-सन्निधान-स्थानम् ।  

> [[उन्नामयतु|उन्मीलयतु]] सुस्निग्ध-पुण्डरीक-विलोचनम् ।  
>    पश्यन्ति हि परं ज्योतिः केचित् तत्र हिरण्मयम् ॥ ४७ ॥  

(*विचिन्त्य, सानन्दम्*) सोऽयम् [[सोऽयमभिजिक्षाममुहूर्तः|अभिजित्-क्षण-मुहूर्तः]] सर्व-विजयावह इति [[ज्योतिर्विद आमन्न्ति|ज्योतिर्विद् आमनन्ति]] । तद् अस्माभिर् उद्योगः कार्यः । (*विचिन्त्य*) कुतस् ते भ्राता प्रवृत्ति-लक्षणो धर्मः ?  

**धर्मः** — प्रवृत्ति-परतन्त्रः [[तद्वियेण|तत्-प्रियेण]] वेदविचारेण बहुमन्यमानः तत्-पार्श्वे तिष्ठति ।  
**यतिराजः** — [[किमसो भक्तौआत्मानमनुतिष्ठति ?|किम् असौ भक्त्या आत्मानम् अनुतिष्ठति ?]] तन्-मुखेन वेदविचार-वृत्तान्तं वेदितुम् इच्छामि ।  

**धर्मः** — किम् अत्र विचारेण ? तत्त्वतो निरूपणे स एवाहम् अस्मि ; किन्तु, सर्व-लोक-विप्रलम्भ-चतुरया मन्त्रिण्या निवृत्तिं प्रति बद्ध-वैरा प्रवृत्त्या कलुषित-हृदयो [[मदन्ध इव|मदान्ध इव]] वर्तते, तन्-मुखेन विदितश्च मया वेदविचार-वृत्तान्तः ।  

**यतिराजः** — (*सादरम्*) तर्हि कथ्यताम् ।  
**धर्मः** — [[चार्वाकेणाभियुक्त|चार्वाकेण अभियुक्त]] एव ।  

**यतिराजः** — (*सभयकौतुकम्*) [[कथमेतद्भविष्यति ?|कथम् एतद् भविष्यति ?]] अथवा, [[किमन्यद्भविष्यति ?|किम् अन्यद् भविष्यति ?]] उच्छिष्ट-मानं चार्वाकं प्रकृत्या वेदविरोधिनी मायावाद-सौगतौ दिगम्बरश्च अनुवर्तेरन् ; तैर् अभियुज्यमानं वेदविचारं मात्रया वेदानुरोधिनोऽपि तत्-कृत-बहु-विरोधम् अनुस्मरन्तः कपिल-पतञ्जलि-कणभक्ष-अक्षचरण-समयाः उपेक्षेरन् , एवं सति [[एवं सत्यात्म- निरपेक्षणमुप्युपरि|आत्म-निरपेक्षणम् उपर्युपरि]] [[निप्त्य|निपात्य]] [[निशितनिशिंशानिष्टुरैस्तर्कैः|निशित-निशित्रिंश-निष्ठुरैस् तर्कैः]] खण्डयन्तः [[खण्डयत्तस्तर्कशरान्|तर्क-शरान्]] [[स्वाङ्गमात्रशेषः|स्वाङ्ग-मात्र-शेषः]] किं करिष्यति [[वेदविचारस्तपस्वी ?|वेदविचारस् तपस्वी ?]]  

---
[[P15]]
**धर्मः** — (*[[सभयात्कम्पव|सभय-कम्पम्]]*) भगवन् ! तथा सति धर्मकथैव लुप्येत ।  
**यतिराजः** — (*करेण शिरसि संस्पृश्य*) मैवं शङ्किष्ठाः । त्वन्-निमित्तम् एव वेदमपि पुण्डरीकाक्षो रक्षिष्यति । पूर्वम् अपि —  

> [[वेदानेवादाय|वेदान् एवादाय]] धातुर् मुख-कमल-गतान् [[सोमकं मार्गरास्त- मर्मं|सोमकं मार्गमाणस् तन्-मर्मं]]  
>    [[हुंकारमात्रप्रशमितसकलत्रासदानुभावम्|हुङ्कार-मात्र-प्रशमित-सकल-त्रास-दानवानुभावम्]] ।  
> हत्वा तद्-रक्त-सिन्धौ महति मधुरिपुः [[कच्छवपुच्छघातैः|कच्छप-पुच्छ-घातैः]]  
>    [[तुच्छीकुर्वन्त्तुचैर्जंलनिधिमकरोदुत्सुको|तुच्छीकुर्वन्न् उच्चैर् जलनिधिम् अकरोद् उत्सुकः]] मत्स्य-लीलाम् ॥ ४८ ॥  

[[एवमन्यान्यपि|एवम् अन्यान््य् अपि]] भगवच्-चेष्टितानि [[भवन्निमित्तान्येव|भवन्-निमित्तान््य् एव]] । किञ्च,  

> निशात-निशित-कठोर-धारैर् विदल्य [[वेदप्रतिकूलमूहैः|वेद-प्रतिकूल-व्यूहैः]] ।  
>    महोत्सवो विष्णुपदाश्रितानां मया विधेयो महतां जनानाम् ॥ ४९ ॥  
(*इति धर्मेण सह निष्क्रान्तः*)  

#### इति श्रीवत्स-कुल-तिलक — श्रीसुदर्शनाचार्य-तनूभव — घटिकाशत — श्रीमद्वरदाचार्य-कृतौ "वेदान्तविलास" अपर-नाम्नि "यतिराजविजये" प्रथमोऽङ्कः ॥  



[[P16]]
## द्वितीयोऽङ्कः  

(*ततः प्रविशति चार्वाकः*)  

> भुङ्क्ते वेत्ति च देह एव [[समहाभूतानि|सह भूतानि]] तेष्वेव धीः  
>    [[किण्वादी|किण्वाद् इव]] मदशक्तिवत् क्रतुफलम् भोक्ता न कोऽपि स्थितः ।  
> दग्धः किं पुनरभ्युपैति नियमो न [[क्वापि|कापि]] जीवेत्सुखं  
>    यावज्जीवति दैवतम् नरपतिः न्यायो बलं केवलम् ॥ १ ॥  

एवं सत्यपि लोको मुह्यति ; भवतु पश्यामः । सौगतः समागच्छतु ।  

(*ततः प्रविशति सौगतः*)  

**चार्वाकः** — (*सहर्षम्*) स्वागतं [[प्रियसृहृदे,|प्रियसुहृदे,]] [[भाले च ।|भला च ।]] कार्यं चिन्त्यताम् । केचिदत्र विप्रलम्भकाः, 'वेद' इति धूर्तप्रलपितम् अवलम्ब्य, सुखचारिणो मनुष्यान् [[कृच्छ्रचान्द्रायण - मासोपवास-यज्ञादिमहादुःखेषु|कृच्छ्र-चान्द्रायण-मासोपवास-यज्ञादि-महादुःखेषु]] निपात्य, तत्-सर्वस्वम् अपहरन्ति । तत्र [[मायामोहमम्भूतैरस्माभिः,|मायामोह-सम्भूतैर् अस्माभिः,]] मिथो विरोधे सत्यपि, सम्भूय समुत्थानं कर्तव्यम् । तत्र प्रथमं [[मित्रभेदः|मित्र-भेदः]] कर्तव्यः । मया च [[वरयुवति - चन्दन - कुसुम - कुङ्कुम - कर्पूर मृगमद - मृदुवसन - भूषण - शयनादिभिः|वरयुवति-चन्दन-कुसुम-कुङ्कुम-कर्पूर-मृगमद-मृदुवसन-भूषण-शयनादिभिः]] विप्रलब्धाः वेदविचारमन्त्रिणो बहुनियमकृशाः, निरतिशयसुखस्वरूपेषु तेष्वेव स्वर्ग-बुद्धिं कृत्वा, [[स्वर्गापवर्गशतमखसर्वेश्वरादिषु|स्वर्गापवर्ग-शतमख-सर्वेश्वरादिषु]] निस्पृहतया तत्प्रतिपादक-[[मन्त्रार्थवादरूपे|मन्त्रार्थवाद-रूपे]] वेदे प्रमाणबुद्धिं त्याजिताः ।  

**सौगतः** — साधु, सखे ! साधु । [[बृहस्पतिमते|बृहस्पति-मते]] तिष्ठन् [[बृहस्पतेरप्यधिकोऽसि|बृहस्पतेर् अप्य् अधिकोऽसि]] । विधिरूपो वेदः किञ्चिदेव ।  

**चार्वाकः** — तत्त्वनिरूपणे तेषां [[विध्यनुष्ठानमपि|विध्य्-अनुष्ठानम् अपि]] केवलम् जीविकैव । [^16_1] किन्तु, वेदमौलिपार्श्ववर्तिनम् मायावादं प्रति शङ्कितोऽस्मि ।  

[^16_1]: सिद्धधनुष्ठानमपि — पा.

---
[[P17]]
**सौगतः** — [[किमल शङ्कया ?|किम् अत्र शङ्कया ?]] सोऽहं, [[अज्ञं वा|अयं वा]] स एव ; वेदमौलिर् अपि तेन स्वकीये पथि निपातितो मिथ्याभूतविधिविषयसम्पत्परमार्थतत्त्वविषयम् अपि विज्ञानमात्रम् एव [[सविषयं|अविषयं]] मन्यमानस् तिष्ठति ।  

**चार्वाकः** — (*सहर्षम्*) परमार्थतो निर्विषयोऽयम् उन्मूलनीय एव । भवतु, पश्चात् पश्यामः । सम्प्रति, मायावादमुखेन भवता वेदविचारं प्रति वेदमौलेः विरोधः कार्यः ।  

**सौगतः** — सखे ! सर्वम् इदम् अनुष्ठितम् एव अवधारय । (*इति तेन सह निष्क्रान्तः*)  

#### इति विष्कम्भः ।  

(*ततः प्रविशति राजा मन्त्री च*)  

**मायावादः** —  
> मय्येव राज्यम् अखिलं विनिवेश्य राजन् !  
>    [[विस्त्रब्धमेव|विस्रब्धम् एव]] [[विहरस्यवधूतकृत्यः ।|विहरस्य् अवधूत-कृत्यः ।]] [^17_1]  
> राज्यं मया च [[हतकण्टकमेतदासीत्|हत-कण्टकम् एतद् आसीत्]]  
>    किन्तु [[स्फुरत्यविभयं|स्फुरत्य् अनिवृतं]] मम दुर्निवारम् ॥ २ ॥  

**राजा** — किमेतत् ?  
**मन्त्री** — [[राजहृदयमजानन्|राज-हृदयम् अजानन्]] कथं [[विज्ञायामि ?|विज्ञायामि ?]]  
**राजा** —  
> [[चिकित्सक इवामात्यः|चिकित्सक इवामात्यः]] प्रियमप्य् अहितं त्यजेत् ।  
>    बलादपि हितं कुर्यात् इति [[नीतिर्महीभृताम्|नीतिर् महीभृताम्]] ॥  

**मन्त्री** — देव !  
> [[भेदप्रसङ्गरहितं|भेद-प्रसङ्ग-रहितं]] तव राज्यम् एतन्  
>    भ्राता भिनत्ति बहुधा [[विहितात्मभेदः|विहितात्म-भेदः]] ।  
> प्रायश्च [[सोदरत एव|सोदरत एव]] भयं नृपाणां  
>    दृष्टं च [[तद्भवति|तद् भवति]] वालिनि रावणे च ॥ ३ ॥  

[^17_1]: आनन्दमात्रसिकोऽस्यवधूतकृत्यः, भोगेषु रज्यति भवान् भुवनैकवीरः — पा.

---
[[P18]]
**राजा** — (*विचिन्त्य*) किमेष वेदविचार एव ?  
**मन्त्री** — [[कोऽन्य एवमाचरति ?|कोऽन्य एवम् आचरति ?]] (*विमृश्य*) देव ! न केवलम् एतावत् ।  
**राजा** — किमन्यत् ?  
**मन्त्री** — (*[[तूष्णीमधोमुखस्तिष्ठति|तूष्णीम् अधोमुखस् तिष्ठति]]*)  
**राजा** — वक्तव्ये सति किं भयेन ?  
**मन्त्री** — [[किञ्चिल्लोकायतिकोपसृष्ट|किञ्चिल् लोकायतिकोपसृष्ट]] इव लक्ष्यते ।  
**राजा** — (*सभयम्*) कथमेतत् ?  
**मन्त्री** — यदिदानीम् ;  

> शब्दैकशेषवपुषस् सकलाश्च वेदाः  
>    विश्वं [[निरीश्वरिमिदं|निरीश्वरम् इदं]] न परे च लोकाः ।  
> कर्मैव सर्वफलदं [[कृषिधन्वराणा-|कृषि-कर्मवद् वा]]  
>    मित्यादि चिन्तयति वेदविचार एषः ॥ ४ ॥  

**राजा** — (*कर्णौ पिधाय*) शान्तं पापम्, शान्तं पापम् । धर्मपरोऽप्ययं [[इतिहास- पुराण - वेदसिद्ध - सर्वकर्माराध्य - तत्फलप्रद - तद्देवताविशेष - तदन्तर्यामि - सर्वेश्वरादिकमपह्नुवानश्चार्वाक|इतिहास-पुराण-वेदसिद्ध-सर्वकर्माराध्य-तत्फलप्रद-तद्देवताविशेष-तदन्तर्यामि-सर्वेश्वरादिकम् अपह्नुवानः चार्वाक]] एव । [[सर्वात्मनाऽयमुन्मूलनीय|सर्वात्मना अयम् उन्मूलनीय]] एव ।  

**मन्त्री** — (*स्वगतम्*) सिद्धं [[नस्समीहितम्|नः समीहितम्]] । तावद् एनं [[विषयान् अमुष्याडपळप्य अनुभवामः ।|विषयान् अमुष्यापलाप्य अनुभवामः ।]]  
(*प्रकाशम्*) देव ! [[निर्विशेषविज्ञानव्यतिरिक्तमखिलमिदमैश्वर्यं|निर्विशेष-विज्ञान-व्यतिरिक्तम् अखिलम् इदम् ऐश्वर्यं]] मिथ्येति जानासि ; तद् एनेन चिदानन्दानुभवस्य ते न किञ्चित् कार्यम् अस्ति । तथापि, [[मायाविलासिनीविलासनावलोकयन्|माया-विलासिनी-विलासम् अवलोकयन्]] विहरस्व ।  

(*ततः प्रविशति मिथ्यादृष्टिः*)  

**मिथ्यादृष्टिः** — (*पुरोऽवलोक्य सकौतुकम्*) पिता मे मायावादेन सह [[सल्पन्महाराज- स्तिष्ठति|सल्लपन् महाराजस् तिष्ठति]] । तावद् एनम् उपसर्पामि । (*विमृश्य*) अभिनवस्य अस्य हृदयम् अजानती कथम् उपसर्पामि । यद्वा,  

---
[[P19]]
> बालो वा यदिवा जरन्न् अपि युवा तिष्ठति अयं रागवान् ,  
>    स्त्रीमात्रेऽपि [[स्त्रीमात्रेऽपि ह्यसत्यं|ह्य् आसक्तं]] यदि मया स्पृश्येत [[किञ्चित्क्चित्|किञ्चित् क्वचित्]] ।  
> कृत्याकृत्यविधिं विधूय गतिम् अप्य् अन्याम् अजानन् सदा  
>    [[मध्येऽर्पितमानसो|मय्य् अर्पित-मानसो]] न गणयति अभ्यागताम् उर्वशीम् ॥ ५ ॥  

(*विमृश्य*) सापि [[मयाऽनुभूय|मयानुभूय]] दत्तान् [[मदनुज्ञया|मद्-अनुज्ञया]] अनुभवति । मुक्तिर् अपि [[कैवल्यन्मया|कैवल्यमयी]] [[भुक्तोञ्झिता|भुक्तोञ्झिता]] ननु भवति !  

**राजा** — (*पुरोऽवलोक्य सपरितोषम्*) हा ! किमेतत् ?  
> [[मामन्यथा|माम् अन्यथा]] विदधती [[मधुरैरुपाङ्गैः|मधुरैर् उपाङ्गैः]]  
>    [[काऽपि|कापि]] ललिता मकरध्वजस्य ।  
> [[अङ्गैरनन्यसदृशैरपरोक्षयन्ती|अङ्गैर् अनन्य-सदृशैर् अपरोक्षयन्ती]]  
>    [[शृङ्गारतत्त्वमुपयाति|शृङ्गार-तत्त्वम् उपयाति]] सरोरुहाक्षी ॥ ६ ॥  

**मन्त्री** — (*स्वगतम्*) [[सम्यगनया|सम्यग् अनया]] वशीकृतो भवति ।  
(*प्रकाशम्*) देव ! [[भुवनत्रयमोहनप्रगल्भमेतत्|भुवनत्रय-मोहन-प्रगल्भम् एतत्]] प्रमदारत्नं महाराजम् एव सेवितुम् अर्हति । देवेन च दृष्टम् अस्या लावण्यम् । किञ्च,  

> सङ्गीते द्रवतां नयत्य् अपि शिलां [[वादविवादासु|वाद-विवादेषु]] चेत् ,  
>    गन्धर्वेष्व् अपि कोऽपि नेदृशगुणो [[यस्यै|यस्याः]] तु गौरी स्वयम् ।  
> [[नृपनीतिकर्मनिजगत्यद्वैतवैदुष्यभूः|नृप-नीति-कर्म-निज-गत्य्-अद्वैत-वैदुष्य-भूः]]  
>    [[कामकलासु|काम-कलासु]] देव ! [[भक्तो|भक्त्या]] देवीपदं च अर्हति ॥ ७ ॥  

**राजा** — (*सबहुमानं [[करमवलम्ब्य,|करम् अवलम्ब्य,]]*) सानुरागम् आसनार्धे निवेशयति ।  
**मन्त्री** — (*स्वगतम्*) [[वार्या(?) निपातितो|वार्यान् निपातितो]] वारणपतिः । (*प्रकाशम्*) देव ! सुखफलानि एव [[पुरूरवःप्रभृतिषु|पुरूरवः-प्रभृतिषु]] दृष्टम् एव देवेन । तद् इदं वेद्येति नोपेक्षाम् अर्हति । न हि कस्यापि रत्नभूतस्य दोषोऽस्ति । अत एव हि पुण्यश्लोकः [[वेश्याप्युर्र्वशीं|पुरूरवा वेश्याम् अप्य् उर्वशीं]] महादेवीपदे निवेशितवान् । किञ्च,  

---
[[P20]]
> यद् अपत्यतया स्तौति श्रुतिर् एव हुताशनम् ।  
>    [[उर्वशी - तपत्तिभ्यां|उर्वशी-तपतीभ्याम्]] तु [[पावनःतरमस्ति|पावनतरम् अस्ति]] किम् (?) ॥ ८ ॥  

श्रुतिर् अपि ताभ्यां रूपिता "[[बहिरश्वमेधं|वह्निरश्वमेधं]] च पुनाति" इत्याह ।  

**राजा** — तथा श्रूयते खलु पुराणेषु ।  

**मन्त्री** — (*स्वगतम्*) [[महाराजमनिच्छन्तमपि|महाराजम् अनिच्छन्तम् अपि]] मोहयितुम् एषा प्रगल्भैव । [[तदस्माभि- रवकाशो|तद् अस्माभिर् अवकाशो]] देयः । (*प्रकाशम्*) देव ! [[किञ्चिद्राजकार्यमस्ति|किञ्चिद् राजकार्यम् अस्ति]] ।  

**राजा** — किं तत् ?  

**मन्त्री** — भवद्-राज्य-रत्नभूतं [[परं ब्रह्म|परं ब्रह्म]] निराकृत्य, [[तंप्रतिबिम्बतया|तत्-प्रतिबिम्बतया]] [[तच्छेषभूतान्सत्कल्पान्|तच्-शेष-भूतान् सत्-कल्पान्]] [[जीवानेव|जीवान् एव]] संसारिणः परमार्थ-पदे स्थापयन्, [[वेदविचारोऽस्माकमरातिरेव|वेदविचारोऽस्माकम् अरातिर् एव]] । [[तस्मात्तदुच्छेदाय|तस्मात् तद्-उच्छेदाय]] गच्छामि ।  

**राजा** — साधु [[चिन्तितममात्येन|चिन्तितम् अमात्येन]] ।  
(*मन्त्री निष्क्रान्तः*)  

**मिथ्यादृष्टिः** — (*महाराजं कण्ठे गृहीत्वा*) महाराज ! [[दर्शनमात्रेण|दर्शन-मात्रेण]] [[चिरकालानुरूटप्रणय- पेशलो|चिरकाल-अनुरूट-प्रणय-पेशलो]] लक्ष्यसे । किन्तु,  

> [[चन्द्रदर्शनेमात्रेण|चन्द्र-दर्शन-मात्रेण]] [[चन्द्रकान्तशिलाऽपि|चन्द्रकान्त-शिलापि]] [[शत् ।|यत् ।]]  
>    द्रवीभवति तत् पुंसि [[खिद्यति|स्विद्यति]] स्त्रीति [[नाद्भुतम्|नाद्भुतम्]] ॥ ९ ॥  

**राजा** — (*सपुलकोद्भेदम्*) (*स्वगतम्*) [[वेश्याजातिः,|वेश्या-जातिः,]] यद् [[मामित्थं|माम् इत्थं]] मोहयति । (*प्रकाशम्*) [^20_2] प्रेयसि ! सम्प्रति प्रणयपरवशतया न किञ्चिद् अपि मे प्रतिस्फुरति प्रियालापः ।  

**मिथ्यादृष्टिः** — (*सविलासं पश्यन्ती*) देव ! दृश्यताम् ;  

[^20_1]: अथवा — पा.  
[^20_2]: मे मनसि — पा.



[[P21]]
### द्वितीयोऽङ्कः  

> मन्दार-पुष्प-मकरन्द-सपीति-लीला-  
>    मन्दायमान-रुषम् [[मन्दायमानरुषमादधवूं|आदधानं]] द्विरेफः ।  
> पक्षाञ्चलेन परिरभ्य ददाति तस्यै  
>    चञ्चुपुटेन सरसीरुह-केसराणि ॥ १० ॥  

**राजा** — करभोरु ! किम् एतत् इति न जानामि ।  

> मन्दस्मितं मधुमदारुणगण्डभागं  
>    ताम्राधरं तरललोचनमाननं ते ।  
> नारीनिरीक्षणनिवृत्तकुतूहले मे  
>    चेतो विमोहयति सुन्दरि ! किं करोमि ? ॥ ११ ॥  

**मिथ्यादृष्टिः** — (*साट्टहासं करेण करम् आस्फाल्य*) [[सम्यगुपलब्धाऽस्मि|सम्यग् उपलब्धोऽस्मि]] ।  
> पुरुषा मयाद्य दृष्टा दिवि भुवि ये सन्ति पुण्य-जन्मानः  
>    किं तैर् गृहीत-चित्ता [[देवेनास्यन्त्यकौतुकिनी|देवेनास्मिन्न् अत्यन्त-कौतुकिनी]] ॥ १२ ॥  

तद् एवं तत्त्वज्ञोऽपि [[किमेवं व्याकुलयसि ?|किम् एवं मामाकुलयसि ?]] [^21_2]  
> दृश्यताम् एष देवेन भुजो मे [[पुलकोद्गमैः|पुलकाङ्कितः]] । [^21_3]  
>    समीकरोति संफुल्ल-कदम्ब-द्रुम-मञ्जरीम् ॥ १३ ॥  

**राजा** — किं करोमि ? धर्मं प्रति पर्याकुलोऽस्मि ।  
**मिथ्यादृष्टिः** — (*विहस्य*)  
> वेद-शास्त्रम् इदं जगच् च सकलं मिथ्यैव यद् दृश्यते  
>    यद् दृश्येत च पुण्य-पाप-नरक-स्वर्गादि शास्त्रेषु च ।  
> तत् सर्वं [[रुजु|तु]] जीविकैव विदुषस् तत्त्वं तु तत् केवलम्  
>    ब्रह्मेति प्रतिपादयन्न् अपि मुधा वेदान्त ! किं मुह्यसि ? ॥ १४ ॥  

[^21_1]: पुष्पक्रमणिः — पा.  
[^21_2]: एवं मामाकुलयसि — पा.  
[^21_3]: पुळकाङ्कितः — पा.  

---
[[P22]]
**राजा** — अयि ! त्वम् एवं ब्रह्मवादिन्य् अपि मायावाद-दर्शितं मे सिद्धान्त-रहस्यं दर्शयसि ।  

**मिथ्यादृष्टिः** — किञ्च, यथा [[पुस्करलाश|पुष्कर-पलाशे]] आपो न श्लिष्यन्ति ;  

**राजा** — (*स्वगतम्*) [[रागाधस्य|गगनान् निपततोऽयं]] मार्गः, न तु नेतुर् देशान्तरस्य ; [^22_1] तथापि सम्प्रत्य् एवम् अभिनेतव्यम् । [^22_2] (*प्रकाशम्*) तथैव खल्विदम् । (*इति तस्याः करं गृहीत्वा*) ब्रह्मवादिनि ! त्वत्सङ्गो मे [[ब्रह्मविद्यासमुद्धिसमुत्पादयति|ब्रह्मविद्या-समृद्धिं सम्पादयति]] ।  

**मिथ्यादृष्टिः** — ब्रह्मवादिन ! ब्रह्मानन्दानुभूतिं ते दर्शयामि (*इति गाढम् [[गाढमालङ्गति|आलिङ्गति]]*) ।  

**राजा** — (*सपुलकानन्दम्*) कृशोदरि ! [[किमिति ब्रवीमि !|किम् अन्यद् ब्रवीमि !]] [^22_3]  
> आख्यातुं तव पारयामि न दशाम् अज्ञात-पूर्वाम् इमां  
>    [[आभोगास्तन मण्डलैवितयवैराश्लिष्यमाणस्य|आभोग-स्तन-मण्डल-द्वितयेन आश्लिष्यमाणस्य]] वा ।  
> आनन्दामृत-सागर-अन्तर् अधुना गाढं निमग्नी भवन्  
>    आत्मानं न च किञ्चिद् अन्यद् अथ वा [[जानाममहं|जानाम्य् अहम्]] प्रेयसि ! ॥ १५ ॥  

**मिथ्यादृष्टिः** — देव ! सकल-कला-विदग्धा ; सङ्गीत-लास्ये च मे कौशलं दर्शयामि । तन् नाट्य-शालां प्रविशावः ।  

**राजा** — तथा भवतु (*इति सादरं तया सह नाट्यशालां प्रविश्य नाट्येन [[कोला- दुमुखोत्वल्कीं|कौशेय-चोलकं]] ददाति*)  

**मिथ्यादृष्टिः** — (*[[सङ्कीळमादाय|सङ्गीतम् आदाय]],* वीणाम् आमृश्य नखाग्रैर् [^22_4] आस्फालयति) ।  
> तत्त्वमसीति ब्रुवती श्रुतिर् एव श्वेतकेतुम् उद्दिश्य ।  
>    पर-जीवयोर् अभेद्ं ब्रूतस् ते भवति विक्रम-पताका ॥ १६ ॥  

**राजा** — (*सहर्षम्*) श्रुति-गीतिर् अमृत-वर्षैः श्रोत्रम् आनन्दयति ।  

[^22_1]: सम्प्रत्येवं भवतु — पा.  
[^22_2]: तथैव खल्विदम् — पा.  
[^22_3]: किमन्यद्ब्रवीमि — पा.  
[^22_4]: नखैः — पा.  

---
[[P23]]
किञ्च,  

**मिथ्यादृष्टिः** —  
> होदि तुह वेदमौले कित्ती मुत्ताळदा व कण्ठगदा ।  
>    गाअन्तीणं महुरं [[मूषा|मुहा]] गन्धव्वराअकण्णाणम् ॥ १७ ॥  
> 
> अविअ,  
> कण्ठे हारळआ कवोळफळए कप्पूरपत्तावळी  
>    धम्मिळ्ळे णवमाळिआ सुइहूव्वंसंसं णिगंच्छइ ।  
> किंत्ती मोत्तिअणिम्मळा तुह महामोक्खैकदिक्खागुरो !  
>    जोण्हा होदि च [[विमेद|मेद]]दंसणसिरीवंताविन्देसु या ॥ १८ ॥  
> 
> [ *छा ॥ भवति तव वेदमौले कीर्तिर् मुक्तालता इव कण्ठगता ।  
>    गायन्तीनां मधुरं मुखाद् गन्धर्वराजकन्यानाम ॥ १७ ॥  
> 
> अपिच,  
> कण्ठे हारलता कपोलफलके कर्पूरपत्रावली  
>    धम्मिले नवमालिका श्रुतिवधूवर्गस्य निर्गच्छति ।  
> कीर्तिर् मौक्तिकनिर्मला तव महामोक्षैकदीक्षागुरो !  
>    ज्योत्स्ना भवति च [[विमेददर्शन|भेददर्शन]]श्रोत्रारविन्देषु या ॥ १८ ॥* ]  

**राजा** — (*सभय-कम्पम्*) (*स्वगतम्*) हा ! कष्टम् आकाशे [[भरतशापमवधारयन्ती|भरत-शापम् अवधारयन्ती]] प्राकृतं गायसि । नाटकेऽस्मिन्न् अप्राकृते [[अपाताकरणमेवैतेन|अपात्रता-करणम् एव एतेन]] ।  

**मिथ्यादृष्टिः** — हा ! [[हतास्म्यहं|हतास्म्य् अहम्]] [[भाग्यहीना|भाग्यहीना]] [^23_3] महाराजम् ।  
(*इति प्रलपन्ती निष्क्रान्ता*)  

**राजा** — (*सत्वरम् उत्थाय ग्रहीतुम् इच्छन्*) हा ! किं कृतं देवेन ?  
> गृहीता अप्य् अंशुके यान्ती न दृष्टा कापि सुन्दरी ।  
>    न करेऽप्य् अंशुकं दृष्टं मन्ये मायेयम् अञ्जना ॥ १९ ॥  

[^23_1]: विमेद — पा.  
[^23_2]: विमेददर्शन — पा.  
[^23_3]: भाग्यहीना प्राणानिव महाराजम् — पा.  

---
[[P24]]
(*विचिन्त्य सानुतापम्*) हा ! प्रिये ! किं करोमि ?  
> तिर्यग् अवलोक्य यान्ती दीनैर् अपि दीर्घ-पातिभिर् अपाङ्गैः ।  
>    मम चिन्तयन्-मनस् त्वां पावक-लीढम् इव [[परितप्यन्तः|परितपति]] ॥ २० ॥  

अथवा किं मनस्तापेन ? यद् इदानीम् —  
> मुग्ध-हसितं मुखं ते [[मणिमयताटङ्कमण्डितकपोलम्|मणिमय-ताटङ्क-मुद्रित-कपोलम्]] [^24_1] ।  
>    न जहाति मानसं मे नष्टं नयनस्य केवलं भाग्यम् ॥ २१ ॥  

(*विमृश्य*) यद्वा, सम्प्रति सकल-भाग्य-भूमिर् [[नयेनमेव|तयैव]] ; अहम् एक एव खलु लुप्त-भाग्योऽस्मि । यतः —  
> तटितम् इव दृष्ट-नष्टां मम पश्यत एव मार्गमाणं त्वाम् ।  
>    [[यद्यप्स्यति|यद् द्रक्ष्यति]] नयनं तत्-तद् अपि त्वन्-मुखेन्दु-भाति ॥ २२ ॥  

(*विचिन्त्य*) हा करभोरु ! कथम् एकपद एव तादृश-प्रेम-शालिन्य् अपि निरनुक्रोशासि ? अयि, प्रिये !  
> मा त्वं प्रयाहि मदिराक्षि ! मया कृतं ते  
>    पश्यामि नाल्पम् अपि दोषम् अथापि किं माम् ।  
> [[काष्ठायनप्रणयकलितं|काष्ठागत-प्रणय-कलितं]] जहासि  
>    का वा गतिर् मम भविष्यति काङ्क्षतस् त्वाम् ॥ २३ ॥  

(*परितोऽवलोक्य*) प्रिया-शोक-सागरे निमज्जन् [[यानपात्रभूतं|पार-भूतं]] [^24_2] न कञ्चिदपि पश्यामि ।  

(*ततः प्रविशति इतिहासः*)  

**इतिहासः** — [[मायाविलामिन्या|माया-विलासिन्या]] सह विहरन्तं महाराजम् अनवसरज्ञः कथं पश्यामि ? (*पुरोऽवलोक्य*) कथम् एकाकी तिष्ठति महाराजः ! (*मन्दम् उपसृत्य*) महाराज ! विजयस्व ।  

[^24_1]: मुद्रितकपोलम् — पा.  
[^24_2]: पारभूतम् — पा.  

---
[[P25]]
**राजा** — (*विवशम् अवलोकयन्*) इतिहास ! दुःख-सागरे निमज्जतो मम यानपात्रम् असि ।  
> सौदामिनीव मेघं मां त्यक्त्वा माया-विलासिनी ।  
>    गता, अहं किं करिष्यामि विरहानल-विह्वलः ॥ २४ ॥  

कथय, कथं ताम् आसादयामि ?  

**इतिहासः** — (*विमृश्य*) किम् अपराद्धं देवेन ?  

**राजा** — न हि न हि ; [[भरतशापमवधीरयन्तास्तस्याः|भरत-शापम् अवधारयन्त्यास् तस्याः]] [^25_1] प्राकृत-गीतिर् एवापराध्यति ।  

**इतिहासः** — (*विमृश्य स्वगतम्*) हा ! मुग्धे वर्धकि ! [[गर्दभोवत्त|गर्दभ इव]] स्व-वाग्-दोषेण हतासि । (*निरूप्य प्रकाशम्*) सम्प्रति उर्वशी-विरहितस्य पुरूरवसोऽवस्था देवम् उपस्थास्यति । [[तदन्तन्मन्त्रिणे|तद् अन्तर्मन्त्रिणे]] निवेदयिष्यामि ।  
(*इति निष्क्रान्तः*)  

**राजा** — कथम् एकाकी शोक-सागरं निस्तरामि ?  

(*ततः प्रविशति यतिराजः, सुनीतिश्च*)  

**यतिराजः** — भद्रे ! [[मायाकृट्टिनीवियोगविह्वलं|माया-कृट्टिनी-वियोग-विह्वलं]] महाराजम् आश्वासयितुं तत्-सुहृदा यामुनेन समादिष्टोऽस्मि ; [[तदासन्नवसरे|तद् आसन्नावसरे]] सुमतिस् तस्यास् ते दर्शनं क्षते क्षारम् इव राज्ञो भवति ; अतः, क्वचित् तिरोहिता राजकुल-वृत्तान्तम् उपलभ्य सख्यै निवेदय ।  

**सुनीतिः** — (*तथा करोति*)  

**यतिराजः** — (*किञ्चिद् उपसृत्य*) देव ! विजयस्व ।  

**राजा** — (*सादरं पश्यन्*) चिन्ता-समकालम् आगतोऽसि ; त्वम् एव मे [[दुःखार्णवनिमनस्य|दुःखार्णव-निमग्नस्य]] कर्णधारो भव ।  

**यतिराजः** — (*सदयम्*) कथम् एतत् ?  

**राजा** — किं न पश्यसि [[विरहविक्लबान्यङ्गानि|विरह-विक्लबान्य् अङ्गानि]] ?  

**यतिराजः** — (*स्वगतम्*) तावद् एनं शोधयामि । (*प्रकाशम्*) देव ! देवी सुमतिर् अपि किम् एवम् अपराध्यति ?  

[^25_1]: अगण्यन्त्यास्तस्याः — पा.



[[P26]]
**राजा** — नहि नहि ।  
**यतिराजः** — का पुनर् एवं करिष्यति ?  
**राजा** — (*सलज्जम्*) माया-विलासिन्या विप्रलब्धोऽस्मि ;  
> मन्दस्मितं च वदनं मधुरं च वाक्यं  
>    [[क्रीडाविलासलितानि|क्रीडा-विलास-ललितानि]] च वीक्षितानि ।  
> रूपं च तल्-लिखितुम् अप्य् अतिदूरम् अस्याः  
>    तत्-सर्वम् आत्मनि [[लिखं स्तरलीभवामि|लिखन् स्तरलीभवामि]] ॥ २५ ॥  

**यतिराजः** — (*सभयाश्चर्यम्*) हन्त ! महाराजम् अप्य् एषा किम् एवं विप्रलब्धवती ?  
**राजा** — किम् अन्योऽप्य् अनया विप्रलब्धोऽस्ति ?  
**यतिराजः** — किम् एक एव ; (*इत्यर्धोक्ते सभयं विरमति*)  
**राजा** — (*विहस्य*) विस्रब्धम् उच्यताम् , अहं सर्वम् अप्य् [[सर्वमप्यस्याधारितं|अस्याचरितं]] [[श्रातुमिच्छामि।|श्रोतुम् इच्छामि ।]]  
**यतिराजः** — देव ! क्षम्यतां यथा-दृष्टं निवेदयामि । यदुत,  
> आबाल-गोपम् अखिलैर् अपि बोध-हीनैः  
>    अन्यैश्च [[पक्षिसुजन्माभिरालशुकैः|पक्षिसुजन्माभिर् बालशुकैः]] ।  
> मुक्ता चिराय भुवनत्रय-पुंश्चलीयम्  
>    स्पृष्टा कथं भवति बोध-निधे ! त्वयापि ॥ २६ ॥  

**राजा** — (*सलज्जम् अधोमुखस् तिष्ठन्*) किम् अनयाहं तत्त्वतो वञ्चितोऽस्मि ?  
**यतिराजः** — तद् एव निरूपयतु ; वस्तु-गतिर् आवेदितैव ।  
**राजा** — (*निरूप्य*) सम्यग् अनया विप्रलब्धोऽस्मि ।  

**सुनीतिः** — (*सखेदम्*) '[[कुहकजनकुकुटुम्बनी|कुहक-कुटुम्बिनी]] [^26_1] [[दम्भकुलकुम्ब्दासी|दम्भ-कुल-दासी]] [[कुदृष्टिलोकाकुट्टनी|कुदृष्टि-लोक-कुट्टनी]] मिथ्यादृष्टि-चण्डाली, चण्डांशुम् इव तमस्विनी, कथं देवम् अनवधिक-बोध-राशिं सुमति-वल्लभं स्पृष्टवती ?  

[^26_1]: कुहककुटुम्बिनी — पा.

---
[[P27]]
### द्वितीयोऽङ्कः  

**राजा** — (*विमृश्य*) সानुतापम् एवम्-भूतस्य मे किम् अस्ति प्रायश्चित्तम् ?  
**सुनीतिः** — (*स्वगतम्*) [[भगवद्भक्तिरूपायाः|भगवद्भक्ति-रूपायाः]] सुमतेः पाद-वन्दनम् एव प्रायश्चित्तम् ।  
**यतिराजः** — (*विहस्य*) अस्ति चेत् , देवी सुमतिर् एव जानाति ।  
**राजा** — (*विचिन्त्य*) तत् तु न सम्भाव्यम् ; छायाम् अप्य् [[अस्मद्वपुषो|अस्मद्-वपुषो]] न सहन्ते हि योषितः !  
**यतिराजः** — नाहम् अत्यन्तं राजकुले परिचयवान् अस्मि ; तथापि [[ब्रवीमी|ब्रवीमि]] ; सुनीतिर् एव प्रभवति ।  
**राजा** — सा च [[मन्त्रिद्विष्टाराजकुले|मन्त्रि-द्विष्टा राजकुले]] न प्रकाशं तिष्ठति ।  
**यतिराजः** — देव ! सुनीति-रहितं राज्यं न चिरं तिष्ठति ।  
**राजा** — किं करोमि ? मन्त्रि-मत एव स्थितोऽयम् एव । सुनीतिम् अनुपालयन्ती सुमतिश्च राजकुलं न गणयति ।  
**यतिराजः** — [[सुमतिसुनीतिरहितं|सुमति-सुनीति-रहितं]] राज्यम् एव न भवति । (*विमृश्य*)  

> [[मतिनीतिविहीनस्य|मति-नीति-विहीनस्य]] महतोऽपि विनश्यति ।  
>    [[राज्यमित्यत्र|राज्यम् इत्य् अत्र]] दृष्टान्तो रावणस्य महापुरी ॥ २७ ॥  

**राजा** — (*[[विचारयन्नधोमुखस्तिष्ठति|विचारयन्न् अधोमुखस् तिष्ठति]]*)  
**सुनीतिः** — मायावाद-वशवर्तिनो महाराजस्य हृदये यतिराज-हितोपदेशोऽपि [[नाङ्गोर्हति|नारोहति]] ; न हि [[महारोगगृहीताय|महारोग-गृहीताय]] महौषधं रोचते !  
**यतिराजः** — (*सभयम्*) [[राजहृदयमविज्ञाय|राज-हृदयम् अविज्ञाय]] कथितवान् अस्मि ।  
**राजा** — भगवन् ! हितम् एव कथितवान् असि, [[विरला एव हि राज्ञां हितस्य वक्तारः।|विरला एव हि राज्ञां हितस्य वक्तारः ।]] तद् भवता [[मदन्तिके|मद्-अन्तिके]] स्थातव्यम् ; राजकार्यं च किञ्चिद् अस्ति ।  
**सुनीतिः** — (*सहर्षम्*) तथा सति राजकुलं च यथा-प्रमाणम् एव स्थास्यति ।  
**यतिराजः** — यद् आदिशति देवः ; भगवान् [[यामुनोऽप्येवमनुशास्तु|यामुनोऽप्य् एवम् अनुशास्तु]] ।  
**राजा** — [[मत्सुहृदेषोऽपि|मत्-सुहृद् एषोऽपि]] [[तथाऽनुजानात्येव|तथा अनुजानात्य् एव]] । (*पश्चाद् अवलोक्य*)  

---
[[P28]]
> [[रविबिम्बमम्बरसालात्|रविबिम्बम् अम्बरसालात्]] ।  
>    पतति जलधौ मनुष्यैः प्राञ्जलिभिः प्रार्थ्यमानम् इव ॥ २८ ॥  

**यतिराजः** — (*दृष्ट्वा सत्वरम् उत्थाय*) [[आसीदत्यनुष्ठानवेळा|आसीदत्य् अनुष्ठान-वेला]] (*इति निष्क्रान्तः*)  
**सुनीतिः** — क्षणं स्थित्वा, राजहृदयं विज्ञाय गच्छामि ।  
**राजा** — (*दीर्घं निश्वस्य*) [[बलान्निगृह्यमाणमपि|बलान् निगृह्यमाणम् अपि]] चेतः प्रेयसीम् अनुधावति, [[परिवादाच्च|परिवादाच् च]] भीतोऽस्मि ; [[तत्किङ्करोमि ?|तद् किं करोमि ?]]  

> [[नष्टरुचिरच्य|नष्ट-रुचिर् एष]] रागी नलिनी-विरहेण विह्वलो भास्वान् ।  
>    पतति [[पश्चिमसन्ध्याप्रवाळशय्यायाम्|पश्चिम-सन्ध्या-प्रवाल-शय्यायाम्]] ॥ २९ ॥  

[[मत्तापस्य|मम तापस्य]] तु प्रतीकारं न पश्यामि । (*इति निष्क्रान्तः*)  

**सुनीतिः** — एवम् अप्य् अस्य मिथ्यादृष्टिम् अजहतो [[राज्ञस्सूर्योदयेऽप्यन्धकारो|राज्ञः सूर्योदयेऽप्य् अन्धकारो]] न नश्यति ।  
(*इति निष्क्रान्ता*)  

#### इति द्वितीयोऽङ्कः  

---
[[P29]]
## तृतीयोऽङ्कः  

(*ततः प्रविशति चामरहस्ता सद्विद्या, गीता च*)  

**गीता** — भद्रे ! [[गजकुलादापतन्ती|राजकुलाद् आपतन्ती]] [[राजकुलवृत्तान्तं|राजकुल-वृत्तान्तं]] ब्रूहि ।  

**सद्विद्या** — भद्रे ! राज-पार्श्ववर्तिनी सर्वम् अहं जानामि । [[पून्युमदहंमहितो|पुनः सुमति-महितो]] राजा एवं चिन्तितवान् ; यथा किल, — "रामानुजस्य मति-नीति-प्रतिभा-सत्त्व-[[समुत्साहसम्पदः समीक्ष्य, तमेव महामन्त्रिपेद निवेदयामि।|समुत्साह-सम्पदः समीक्ष्य, तम् एव महामन्त्रि-पदे निवेदयामि ।]] मायावादस्तु [[प्रमाणपुरुषपादितं|प्रमाण-पुरुष-प्रतिपादितं]] [[मदैश्वर्यमशेषं|मद्-ऐश्वर्यम् अशेषं]] मिथ्येति ब्रुवन् अशेपं नाशयति [^29_1] इति प्रतिभाति । तेन तद् विज्ञाय [[जायागादेन|जाया-वादेन]] [[भास्करयादवसहितेन|भास्कर-यादव-सहितेन]] राजकुले निरुद्ध-प्रवेशो रामानुजः सामर्थ्याभ्यां शिष्याभ्यां सह कृत-प्रतिज्ञः काञ्चीपुरीं गतवान् । सेनापतिः [[सहृदश्च|सुहृदश्च]] तेन राजकुलाद् निरस्तो गत-सामर्थ्य एव न ज्ञायते क्व वर्तते" इति ।  

**गीता** — (*सभयम्*) हन्त ! [[मन्त्रिणोऽधुना|मन्त्रिणोऽधुना]] किं भविष्यति ?  

**सद्विद्या** — देवी सम्प्रति कथं तिष्ठति ?  

**गीता** — प्राणान् धारयन्ती तिष्ठति । देवस्य च नाद्यापि [[शमंलाभनेहो|शम-लाभ-स्नेहो]] विरमति । [[न ह्यसदृशपत्नीकरणादप्यधिकं|न ह्य् असदृश-पत्नी-करणाद् अप्य् अधिकं]] दुःखं नारीणाम् । तथापि, सर्वम् अहा सपरिवारा राज्याभ्युदयाय [[सम्मन्विलासमभिलषन्ती|साम्राज्य-विलासम् अभिलषन्ती]] सुनीति-सहिता देवी नारायणम् आराधयति ।  

**सद्विद्या** — (*साशंसम्*) [[सव्यास्मसङ्कल्पलामोऽस्तु|सर्वथा अस्मत्-सङ्कल्प-लाभोऽस्तु ।]] [[रामानुजक्रनोपाया|रामानुज-कृतोपायाः]] अपि सम्भूय मन्त्रिणः सर्वे सर्वदा राजानं सेवन्ते । तद् अहम् अपि गच्छामि । मायाशीलोऽपि महामन्त्री सर्वास्वपि विद्यासु माम् एव सबहुमानं पश्यति ।  

**गीता** — (*सखेदम्*) एवम् अप्रियकारिण्य् अपि राज्ञि निकामं रागिणी देवी नितान्तं परितप्यते । [[तं परितापनह|तं परितापम् अहम्]] एवम् इति निर्वक्तुं न शक्नोमि । किन्तु —  

[^29_1]: अशेपं नाशयति — पा.

---
[[P30]]
> [[सन्तापस्फुटितोज्झितस्तनतटैस्संह्लादितं|सन्ताप-स्फुटितोज्झित-स्तन-तटैस् संह्लादितं]] मौक्तिकैः  
>    भस्मीभूत-नवप्रकाश-शयनं [[व्याकुलेरङ्गकैः।|व्याकुलैर् अङ्गकैः ।]]  
> निश्वास-ग्लपित-प्रसून-कलिका-निर्विण्ण-भृङ्गी-कुलं  
>    तस्यास् तापम् अनक्षरं कथयते तन्व्या लता-मण्डपम् ॥ १ ॥  

**सद्विद्या** — (*सखेदम्*) [[मदभिप्रायास्तस्यास्तापो|मदभिप्रायः, तस्यास् तापो]] [[मद्भजैरैव|मद्-भुजैर् एव]] निर्वापणीयः । तथापि, परतन्त्राऽहं किं करोमि ?  

**गीता** — तर्हि गम्यताम् ; अहम् अपि [[तत्तापचिकित्सार्थै|तत्-ताप-चिकित्सार्थं]] [[कमलिनी - पलाश - कर्पूर - हरिचन्दन - किसलयादिकमादातुं|कमलिनी-पलाश-कर्पूर-हरिचन्दन-किसलयादिकम् आदातुं]] गच्छामि ।  
(*इति निष्क्रान्ते*)  

#### इति प्रवेशकः ।  

(*ततः प्रविशति [[यामुनकरावलम्बी|यामुन-करावलम्बी]] [[यादवभास्कराभ्यां|यादव-भास्कराभ्यां]] अनुगम्यमानो [[मायावाददर्शितमार्गो|मायावाद-दर्शित-मार्गो]] वेदमौलिः*)  

**मायावादः** — इत इतो देवः ! पाद-पद्माभ्यां [[पद्मरागसोपानपदवीं|पद्मराग-सोपान-पदवीं]] [[परिष्कणेतु।|परिष्कुरुतु ।]]  
**भास्करः** — (*सरभसम् उपगम्य, कराभ्याम् उपमार्जन्*) इदं भद्रासनम् ।  
**यादवः** — देव ! विजयस्व ! भद्रम् अस्तु भुवनस्य ! भद्रासनम् आरुह्यताम् ।  
**राजा** — (*यामुन-मुखम् अवलोकयति*)  
**यामुनः** — देव ! तथा क्रियतां [[लोकाभ्युदयाय|लोकाभ्युदयाय]] ।  
**राजा** — (*उपविश्य, समन्ताद् अवलोकन्*) सर्वेऽपि यथा-स्थानम् उपविशन्तु ।  
**मन्त्रिणः** — यद् आज्ञापयति देवः । (*इति सर्वे यथा-स्थानम् उपविशन्ति*)  
**राजा** — (*यामुन-मुखम् अवलोक्य, कराग्रेण दर्शयन्*) इदम् आसनं विविक्तम् अध्यास्यताम् ।  
**यामुनः** — (*सविनयम् उपविशति*)  
**भास्करः** — (*स्वगतम्*) सबहुमानं [[प्रणयसवर्षाणी|प्रणय-वर्षिणी]] देवस्य दृष्टिर् मय्य् एव निपतति ।  
**यादवः** — (*स्वगतम्*) धन्योऽस्मि देव-प्रसादेन [^30_1] ; यद् असौ माम् एव सस्मितम् अवलोकयति ।  

[^30_1]: स्वामिप्रसादेन — पा.



[[P31]]
### तृतीयोऽङ्कः  

**मायावादः** — (*स्वगतम्*) द्वयोरपि दाक्षिण्य-मात्रम् एव । देवस्य प्रणय-बहुमान-विश्रम्भास् तु मय्य् एव ।  

**राजा** — (*समन्ताद् अवलोक्य*)  
> संन्यस्तभारः सचिवेषु को वा महीपतिर् [[मन्मवमहत्तरेषु|मद्विध-महत्तरेषु]] ।  
>    निरस्त-निःशेष-रिपु-प्रसङ्गं सुखेन भुङ्क्ते विषयं स्वकीयम् ॥ २ ॥  

(*यामुन-मुखम् अवलोक्य*) कथ्यताम् आर्य ! कश्चिद् अस्ति चेद् एवंविधो राजा ?  
**यामुनः** — देव ! न शक्यते नास्तीति [[निर्वेक्तुम्|निर्वक्तुम् ।]] किन्तु, देवं प्रति न कश्चित् । तथाहि —  

> राजन् ! सप्त महन्ति सन्ति [[भुवनान्यन्येष्वेव|भुवनान्य् अन्येष्व् एव]] किञ्चिन् मही  
>    सम्राजोऽपि तद्-एकदेश-पतयः पूर्वे च पूर्वादयः ।  
> तादृक्-लोक-परःसहस्र-भरित-ब्रह्माण्ड-[[कोश्या|कोट्या]] धृतम्  
>    मूर्ध्ना शासनम् एव यस्य स भवान् वर्ण्येत किं [[तैरममः|तैर् अमरैः]] ॥ ३ ॥  

किञ्च,  
> प्रत्येकं नियत-स्वकीय-विषयाः प्रत्यक्ष-मुख्या नृपाः  
>    त्वन्-मित्राणि निशान-तर्क-दलित-प्रत्यर्थि-धी-सम्पदः ।  
> मर्त्यानन्द-शतोत्तरोत्तर-[[मर्त्यानन्दशतोत्तरोत्तर'घनानन्दामृतैकार्णवं|महानन्दामृतार्णवं]] [^31_1]  
>    त्वं च ब्रह्म महाविभूत्य्-अनुभवं स्तुष्टोऽसि पुष्टोऽसि च ॥ ४ ॥  

**मायावादः** — (*सासूयं पश्यन्, आत्मगतम्*) जाल्मोऽयम् [[अलीकागेपेण|अलीकारोपेण]] महाराजम् आत्मसात्कर्तुं प्रभवति । निखिल-प्रपञ्च-निबन्धरूप-परब्रह्माभिमुखीकृतस्य वेदमौलेः तद्-इतर-सकल-प्रपञ्च-साधकं प्रत्यक्षादिकं प्रतिपक्ष-कोटि-निविष्टम् [[इत्यदपि|इत्य् अपि]] न जानाति ।  

**यादवः** — महाराजं प्रति सर्वम् अपि युज्यते ।  
**राजा** — (*मायावाद-मुखं सस्मितम् [[अवलोकयात|अवलोकयति]]*)  

[^31_1]: महानन्दामृतार्णवम् — पा.

---
[[P32]]
**मायावादः** — देव ! [[चाटुक्तयो|चाटूक्तयो]] न तत्त्व पदवीम् उपजिघ्रन्ति ।  
**भास्करः** — तत् त्वम् अपि कदाचित् [[कचिदुपजिघ्रति|क्वचिद् उपजिघ्रसि]] ?  
**राजा** — सर्वम् अप्य् अस्तु । यामुनोक्तिर् मे तत्त्वम् एव प्रतिभाति ।  
**मायावादः** — तत् कविरचना-कौशलम् एव, [[यद्विद्यमानमपि|यद् अविद्यमानम् अपि]] विद्यमानवत् प्रतिभाति । [^32_1]  
**यामुनः** — न वयम् अलीक-वाचाटा वन्दिनः ! अस्मद्-उक्तिस् तत्त्वोक्तिर् अपि, [[उलोकतया|उल्लोकतया]] चाटूक्तिवत् मन्दमतीनां परिस्फुरति । महापुरुष-मुखात् प्रमाणवन्त्य् एव वचांसि निस्सरन्ति ।  
**मायावादः** — (*सासूयं पश्यन्*) किं भवान् प्रमाण-वार्ताम् अपि जानाति ?  
**यादवः** — (*विहस्य सोल्लुण्ठम्*) भवान् एव प्रमाण-तत्त्वं जानाति ; [[येतेन सहस्रमेय- प्रपञ्चमध्यपळपसि|येन एतत् सहस्र-प्रपञ्चम् अपलपसि ।]]  
**मायावादः** — (*सरोषम् अवलोक्य, साट्टहासम्*) [[प्रपञ्चमप्यलपसि|प्रपञ्चम् अपलपसि]] — इति, किं [[कन्यागर्भ मुद्रावयसि|कन्यागर्भं मुद्रायसि]] ! [^32_2] (*समन्ताद् अवलोक्य*) यदि धीमन्तः, सर्वे भवन्तः शृण्वन्तु —  
> [[मानासिद्धयतु|मानात् सिद्ध्यतु]] सर्वम् एव भुवनं मानं तु सिद्ध्येत् कुतः ?  
>    किं स्वेनैव [[तथाऽस्त्यु|तथास्तु]] तर्हि भुवनं मानेऽपि माने यदि ।  
> हन्त ! [[स्याद्विश्वातिशयरमनो|स्याद् विश्व-अतिशय-रहितो]] मेयं च न स्याद् इति  
>    क्वासौ तिष्ठतु विश्वम् अत्र सकलं सत्यं ब्रुवाणो जडः ॥ ५ ॥  

**यादवः** — (*विहस्य*) कुतोऽनवस्था ; तवापि हि स्वतःसिद्धैव संवित् ।  
**यामुनः** — तथा खलु तत् । तत्त्वं च तस्याः, [^32_3] स्वतस्त्वात् , अर्थक्रिया-निर्वहणाद् वा सिद्ध्यति ।  
**राजा** — भवतु ; जानीमो मति-वैभवम् एषाम् (*इति [[इतिव्याजान्तरेण|व्याजान्तरेण]] चामरहस्तया क्षान्त्या सह [[सँल्लपन्नश्रवणमभिनयति|सल्लपन्न् अश्रवणम् अभिनयति]]*)  

[^32_1]: तद्विरचनाकोशभव — पा.  
[^32_2]: विश्रमय — पा.  
[^32_3]: तस्याः एवमेव प्रमाणं प्रामाण्यं स्वतस्त्वात् — पा.  

---
[[P33]]
**भास्करः** — (*मायावादं प्रति सोल्लुण्ठम्*) सर्व-लोक-शास्त्र-साधारणीम् अपि प्रमाण-प्रमेय-पदवीं [[मपलपन्ते|अपलपन्]] चिराय गोपितम् अपि सर्वज्ञत्वम् उन्मीलयति ।  

**यादवः** — भोः [[सर्वापलापिन्|सर्व-अपलापिन्]] ! प्रमाण-व्यवस्थां आहत्य यत् किञ्चित् साधयन्, त्वम् अपि यस्य कस्यचित् [[कस्यचित्किञ्चिद्वास्मि|किञ्चिद् वा वदसि ।]] (*सर्वे हसन्ति*)  

**मायावादः** — (*सक्रोधं [[भ्रुकुटीमुद्धलयन|भ्रुकुटीम् उद्धूलयन्]] भास्करम् अवलोक्य*) भो ! जाल्म ! जल्पतु नाम यादवो यत् किञ्चित् । किम् आथ रे कितव ! सर्वोपनिषद्-भ्यासेन सकल-वैदिक-शिरोन्नतस्य मे सर्वज्ञ-शब्देन पाषण्डत्वम् उद्भावयसि !  

**भास्करः** — (*विहस्य*) किं सर्वज्ञत्वम् अपि ते दोषाय ! [[तर्ह्यन्यथाऽस्तु|तर्ह्य् अन्यथा अस्तु]] ।  

**मायावादः** — भो भो ! भास्कर ! प्राज्ञं मन्यमानस्य ते कथयामि ; [[परमार्थसत्ताऽऽ- भावेऽपि|परमार्थ-सत्ताभावेऽपि]] [^33_1] [[व्यावहारिकसत्ताऽपि|व्यावहारिक-सत्तापि]] मे सर्व-व्यवस्था सिद्ध्यत्य् एव ।  

**यादवः** — (*विहस्य*) किं तावता सिद्ध्यति ? सौगतेनापि तद् एव, [[संवृत्तिसत्यमिति|संवृति-सत्यम् इति]] नामान्तरेण, अङ्गीक्रियते ।  
> मिथ्येति विदितैर् अर्थैः [[किं चिक्तुम् अर्हति|किं चिकीर्षितुम् अर्हति]] [^33_2] ।  
>    स्वप्न-लब्ध-सुवर्णेन किं कार्यं कर्ण-भूषणम् ॥ ६ ॥  
न ह्य् असत्यम्, अर्थक्रियाकारि भवति ।  

**मायावादः** — (*सक्रोधसंरम्भं समन्ताद् अवलोक्य*) आः [[कप्रम|कष्टम्]] ! [[एकवराहं|एक-वराहं]] प्रति [[अनेकासरमेयास्समुत्पतन्ति,|अनेके सरमेयाः समुत्पतन्ति,]] तद् इदम् अत्र शरणम् । (*इति कूर्मासनं परामृशति*)  

**भास्करः** — (*सत्वरं [[त्रिदण्डमादत्ते|त्रिदण्डम् आदत्ते]]*)  
**यादवः** — (*[[काषायाम्बरञ्च|काषायाम्बरं]] च कमण्डलुं गृह्णाति*)  
**यामुनः** — (*[[सभयरोपम्|सभय-रोषम्]],* दृशा राजानं दर्शयन्, निर्भर्त्सयति)  
**सर्वे** — (*[[सभयमुपशाम्यन्ति|सभयम् उपशाम्यन्ति]]*)  

[^33_1]: प्रमेव्यवस्थाम् — पा.  
[^33_2]: विदितो लोको न किञ्चित्साधयिष्यति — पा.  

---
[[P34]]
**मायावादः** — (*स्वगतम्*) [[श्रुतिनिर्विशेषा|श्रुति-निर्विशेषा]] अप्य् एते मय्येव [[युगपदकाण्डे|युगपद् अकाण्डे]] वैरम् आचरन्ति ; भवतु ; सद्य एव [[राजकुलान्निरस्यामि|राजकुलाद् निरस्यामि ।]]  

**गीता** — (*विचिन्त्य सखेदं, स्वगतम्*) सर्वेऽप्य् एते [[नीतिविदोऽपि|नीति-विदोऽपि]] नित्ये वस्तुनि मुह्यन्ति ; मिथो वैरम् अप्य् आचरन्ति ; [[यामुनस्तु|यामुनस् तु]] नीति-निपुणोऽपि, नितान्तं निस्पृहतया, नात्यन्तम् उद्योगम् आचरति । (*विचार्य सनिर्वेदम्*)  

> राज्ञो मन्त्रिकुलस्य तस्य च मिथो [[यत्नैकताना|यत्नैकताना]] मतिः  
>    तद् राष्ट्रं सुखम् एव तिष्ठति मिथस् तेषां विरोधे सति ।  
> [[नश्येदेतदशेषमप्यहिभयं|नश्येद् एतद् अशेषम् अपि,]] अहि-भयं तद् वर्ततेऽस्मासु तत्  
>    किं भावीति न वेद्म [[नीतिनिपुणो|नीति-निपुणो]] मन्त्री न कश्चित् परः ॥ ७ ॥ [^34_1]  

भवतु ; पश्यामि । (*इति सर्वान् अवलोकयति*)  

**सर्वे** — (*[[यामुनवर्जमधोमुखा|यामुन-वर्जम् अधोमुखा]]* भवन्ति)  

**राजा** — (*स्मितं कृत्वा, मायावादम् अवलोक्य*) [[महामन्त्रेश्वर|महा-मन्त्रेश्वर]] ! [[किमर्थमासनमन्वे- षितम् ?|किमर्थम् आसनम् अन्वेषितम् ?]]  

**मायावादः** — देव ! [[सुखावास्थानाय|सुखावस्थानाय ।]]  

**राजा** — युज्यते । (*भास्कर-मुखं पश्यति*)  

**भास्करः** — देव ! [[यतिलिङ्गानि|यति-लिङ्गानि]] नातिदूरे स्थातुम् अर्हन्ति ।  

**राजा** — (*विहस्य, यादवम् अवलोकयति*)  

**यादवः** — देव ! सर्वं ते विदितम् एव । [[करप्रक्षालनाय|कर-प्रक्षालनाय]] कमण्डलुर् आनीतः ।  

**राजा** — (*विहस्य, यामुन-मुखं पश्यति*)  

**यामुनः** — देव ! प्रसीद ; [[सापराधेषु|सापराधेषु]] खलु क्षमा जीवति !  

**राजा** — (*[[विमृशंस्तिष्ठति|विमृशंस् तिष्ठति]]*)  

[^34_1]: पश्यति महाधीमन, क्रिमिह त्रिदण्डमानीयतम् — पा.  

---
[[P35]]
### तृतीयोऽङ्कः  

(*नेपथ्ये*)  
जय जय, महाराज ! [[जगत्प्रतिहतशासनो|जगद्-अप्रतिहत-शासनो]] विजयस्व ।  

> कीर्तिं ते भृगु-नารद-प्रभृतयो गायन्ति [[मञ्जुकण- द्रीणा|मञ्जु-क्वणद्-वीणा]]-रञ्जित-गीतयः  
>    श्रुति-सुखं विद्याधरैः सेविताः ।  
> [[मन्दारद्रुमवाटिकासुभगयोर्मन्दाकिनीकूलयोः|मन्दार-द्रुम-वाटिका-सुभगयोर् मन्दाकिनी-कूलयोः]] [^35_1]  
>    मध्ये [[मन्दरगन्धमादनतटारण्येषु|मन्दर-गन्धमादन-तटारण्येषु]] पुण्याधिकाः ॥ ८ ॥  

अपिच,  

> [[पञ्चाशीत्पदवीं|पञ्चाशत्-पदवीं]] प्रविश्य विहरत्य् अम्लान-धीरः यत् [^35_2]  
>    पश्यत्य् आत्मनि च प्रतीचि [[परमं ज्योतिर्जगत्कारणम्।|परं ज्योतिर् जगत्-कारणम् ।]]  
> तत्-साम्यं च निरञ्जनो भजति यन् मर्त्यो [[महानन्दभाक्|महानन्दभाक्]] [^35_3]  
>    तत्-सर्वं कथयन्ति देव ! कवयस् त्वत्-पाद-सेवा-फलम् ॥ ९ ॥  

**राजा** — (*निशम्य, सपरितोषम्*) [[कावेत्रौ|कावे तौ]] [[गायनः ?|गायनौ]] मधुर-कण्ठौ मम हृदयम् अनुस्पृशन्तौ परमार्थं गायतः ? (*विचिन्त्य*) [^35_4] मदीय-धर्म-तत्त्व-सङ्ग्रहम् इव इदानीम् अनुस्मारितोऽस्मि ।  

**मायावादः** — (*विचिन्त्य*) महाराज ! सर्वं मिथ्येति जानन्न् अपि, [[पृथग्जनैरप्यनादरणीये|पृथग्-जनैर् अप्य् अनादरणीये]] [[वैतालिकवचसि|वैतालिक-वचसि]] यथार्थ-बुद्धिः किं मुह्यसि ?  

**राजा** — महामात्य, किं न जानासि नूतनं सर्वं [[कौतुकमुत्पादयत्येव !|कौतुकम् उत्पादयत्य् एव !]]  

**मायावादः** — (*विचिन्त्य सासूयम्*) देव ! कौतुकं चेत्, [[कञ्चुकिनाज्ञापय|कञ्चुकिनाज्ञापय ।]]  

**राजा** — (*कञ्चुकिनं पश्यति*)  

**कञ्चुकी** — यथा आज्ञापयति देवः । (*इति निष्क्रम्य वैतालिकाभ्यां सह प्रविशति*)  

**वैतालिकौ** — (*[[पुरोऽवलोकय|पुरोऽवलोक्य]] सानन्दम्*)  

[^35_1]: सुरमयो — पा.  
[^35_2]: महारण्यानि — पा.  
[^35_3]: महानन्दवान् — पा.  
[^35_4]: मदीय-धर्म-तत्त्व-सङ्ग्रहम् इवेदानीम् अनुस्मारितोऽस्मि — पा.



[[P40]]
**यामुनः** — (*सानन्दम्*) महान् अयम् अभ्युदयः ! (*विचिन्त्य*)  
> ब्रह्माण्डेषु परिस्फुटत्सु युगपद्-ब्रह्मायुर्-अन्ते पुनः  
>    सर्वेषु प्रतिमञ्चरत्सु चिदचित्-तत्त्वेषु नृत्यन् नृपः ।  
> यस् त्वां रक्षितवान् [[यथापुरलमुद्रणानूर्वीमयं|यथापुरम् उदरान्तर् ऊर्वीम् अयम्]]  
>    स त्वां सम्प्रति [[पीड्यमानमनरैः|पीड्यमानम् इतरैः]] विष्णुः कथं [[म्रुप्यति|मृष्यति]] ? ॥ १५ ॥ [^40_1]  

**मायावादः** — (*भास्कर-यादवाभ्यां सह ससम्भ्रमम् अभ्युत्थाय, ससँरम्भम्*) देव ! [[वैतालिकलीकवचनेन|वैतालिक-अलीक-वचनेन]] [[सम्यग्विप्रलब्धोऽसि|सम्यग् विप्रलब्धोऽसि ।]]  
> विदग्ध-वेश्या-शैलूष-पाषण्ड-विट-वन्दिभिः ।  
>    विप्रलब्धा विनश्यन्ति राजान इति नः श्रुतम् ॥ १६ ॥  

इदानीं वा विरम्यतां, यावन् न विषम् उन्मस्तकीभवति ।  

**भास्करः** — (*[[यादवमङ्गल्या|यादवम् अङ्गुल्या]]* निर्दिशन्) अयम् अहं च [[द्रावावां|द्वौ आवां]] भवतो बहिरङ्गम् एव ; [[किमन्तरङ्गभूतोऽप्ययं|किम् अन्तरङ्ग-भूतोऽप्य् अयं]] बहिरङ्गतां नीयते देवेन ?  

**यादवः** — (*भास्करं प्रति जनान्तिकम्*) भवत्व् अस्य दुरात्मनो गर्व-क्षतिः ।  

**मन्त्री** — (*सक्रोधं यामुनं पश्यन्*) भो ! [[रावणसन्यामिन्|रावण-सन्न्यासिन्]] ! [[मन्मन्त्रमायासृगतृष्णि-|मन्-मन्त्र-माया-मृगतृष्णिका-]] काम्भसि निमग्नोऽयं स्वामी, राम इव कां गतिं यास्यति ?  

**प्रियरङ्गः** — राम इव [[रामानुजबलेन|रामानुज-बलेन]] स्वामी न काञ्चन दुर्गतिं यास्यति ; किन्तु, सर्वत्र विजयी भविष्यत्य् एव । त्वं तु [[महानुभावमाश्रिक्षपन्|महानुभावम् अधिक्षिपन्]] [[मवीं|सर्वां]] [^40_2] दुर्गतिं गमिष्यसि । (*विहस्य*)  
> ब्रह्मसूत्र-परित्यागी मत्तो नान्य इति ब्रुवन् ।  
>    त्वं तु रावण-सन्न्यासी [[मायैकशरणो|मायैकशरणो]] भवन् ॥ १७ ॥  

**मन्त्री** — (*सरोषम्*) साधु, [[वैतालिकवटो|वैतालिक-वटो]] ! सम्यक् पटीयानसि । त्वम् एव किं परमहंसस्य मे यज्ञोपवीत-त्यागम् अवगच्छसि ?  

[^40_1]: त्वां — पा.  
[^40_2]: भव — पा.  

---
[[P41]]
### तृतीयोऽङ्कः  

**प्रियरङ्गः** — न हि न हि ; सर्वेऽपि जानन्ति । यज्ञोपवीत-त्यागी काको वा, हंसो वा [^41_1] भवान् ; नाहम् इदानीम् एतत् कथयामि ।  

**मायावादः** — (*विचिन्त्य*) हुम् । किं [[शारीरकसूत्रपरित्यागमपि|शारीरक-सूत्र-परित्यागम् अपि]] ? [[यथाज्ञान|यथाजात]] ! श्रीवेदमौलि-[[अद्वैतसाम्राज्यानुभाव्यता|अद्वैत-साम्राज्यानुभाव्यता]] मया कथं तत्-परित्यागः कृतः ? [[तद्गच्छ|तद् गच्छ]] ; गायतो बालकस्य ते किं [[ब्रह्मविद्याप्रसङ्गेन|ब्रह्म-विद्या-प्रसङ्गेन]] ?  

**प्रियरङ्गः** — यथाजातो भवन्न् अहं न जानामि ; अन्यथाजातत्वं ब्रूहि ; किं [[सङ्गीतविद्या|सङ्गीत-विद्या]] बाल्यं च ब्रह्मविद्यां विरुणद्धि ? (*विहस्य*) प्रह्लाद-नारदौ परित्यजसि किं [[ब्रह्मविद्गोष्ठ्याम्|ब्रह्मविद्-गोष्ठ्याम्]] ?  
> शुक-नारद-वृत्तान्तः किं ते [[बधिरवल्की|बधिर-वार्ता]] ।  
>    तौ हि [[ब्रह्मविदाचार्या|ब्रह्मविद्-आचार्याः]] तत्र किं प्रतिपद्यसे ॥ १८ ॥  

रे ! वृथा पण्डितमन्य ! पश्य —  
> [[एतमात्मानमानन्दमयं|एतम् आत्मानम् आनन्दमयं]] [[लोकान्विमान्|लोकान् इमान्]] पुमान् ।  
>    उपसङ्क्रम्य [[कामान्नी|कामान्नी]] [[कामरूप्यनुपचरन्|कामरूप्य् अनुसञ्चरन्]] ॥ १९ ॥ [^41_2]  

एतत्-साम तथा गायन्न् आस्ते [[इत्यामन्प्रिया|इत्याम्नाय-प्रिया]] ।  
   नाधीता न श्रुता किं वा मायावाद ! त्वया श्रुतिः ॥ २० ॥  

सम्प्रति तत् तिष्ठतु ; [[गगनकुसुम कल्पमद्वैतमिति|गगनकुसुम-कल्पम् अद्वैतम् इति]] किञ्चिद् अङ्गीकृत्य, तद् एव सत्यम्, तत्-परिपन्थि-रूपं [[ब्रह्मसूत्रलापं|ब्रह्मसूत्र-कलापं]], तद्-अर्थ-भूतं ब्रह्मणः [[सकलचिदचित्प्रपञ्चकारणत्वं|सकल-चिदचित्-प्रपञ्च-कारणत्वं]], [[तदनुगुणानन्तकल्याणगुणमोक्षदानादिकं|तदनुगुणानन्त-कल्याण-गुण-मोक्ष-दानादिकं]] च मिथ्येति ब्रुवता भवता तत्-परित्यागः कथं न कृतः ? तथापि, [[ब्रह्मसूत्रस्वीकारस्तु|ब्रह्मसूत्र-स्वीकारस् तु]] वैदिक-जन-वञ्चनाय ; तत्त्व-निरूपणे [[वेदमौलेर्द्वैतविषयानुभवोऽपि|वेदमौलेर् द्वैत-विषयानुभवोऽपि]] प्रतारणम् अन्तरेण न किञ्चित् सिद्ध्यति । (*मन्दमन्दम् उपसृत्य*) [[सन्न्यासिनिहसार्वभौम|सन्न्यासि-सिंह-सार्वभौम]] ! त्वम् एव मे मस्तके हस्तं निधाय सत्यं ब्रूहि । स्वानुभव-सिद्धं स्वयं [[ज्योतिर्द्वैतमात्म-|ज्योतिरद्वैतम् आत्म-]]  

[^41_1]: हंसो वा परमो वा — पा.  
[^41_2]: सत्यवादिन — पा.  

---
[[P42]]
सिद्धौ [[किमन्यदाकाङ्क्षितः|किम् अन्यद् आकाङ्क्षितम्]] ? तद्-आकाङ्क्षायां तु दृश्यतया ब्रह्म मिथ्यैव स्यात् । (*विहस्य*)  
> [[तच्च ब्रह्म|तच् च ब्रह्म]] न संवेद्यं संवेद्यम् अनृतं जडम् ।  
>    इति स्वकृत-सीमायां त्वम् एव परिमुह्यसि ॥ २१ ॥  

किञ्च तत्त्वम् उच्यताम् कीदृशी ते [[म्युक्ति|मुक्तिः]] ?  

**मायावादः** — कस्मिन् किं स्यात् ?  

**प्रियरङ्गः** —  
> न साध्या ब्रह्म चेन्मुक्तिः, तदन्या चेन् मृषैव सा ।  
>    मुक्तिः शून्यस्य वेदान्त-सम्पते [[कपेः स्रजः|कपेः स्रजः]] ॥ २२ ॥  

**मायावादः** — (*सलज्जम् अधोमुखस् तिष्ठति*)  
**राजा** — (*सहर्षम्*) सत्यम् आह प्रियरङ्गः ।  
**मायावादः** — (*स्वगतम्*) सर्वात्मना अहम् अनेन दुरात्मना वञ्चितोऽस्मि ।  
**रङ्गप्रियः** — (*सहर्षम्, भुजम् आस्फोठ्य गर्जन् वल्गति*)  
**भास्कर-यादवौ** — (*हर्ष-विस्मयागतं हासम् अन्तर्-निगृह्य*) भो वैतालिक-वटो ! महाप्रगल्भोऽसि । तथापि महामात्यं परिभवन् [[कदाचिद्रिद्रमसि|कदाचिद् रिष्यसि ।]]  

> तृणीकृत-बृहस्पतिस् त्रिभुवनैक-वैतण्डिकः  
>    [[गणयन्त्यं|गणयत्य् अयं]] प्रणतोऽपि [[मेक्रानिव।|मेषानिव ।]]  
> [[मदद्विरदमस्तकस्थलविपाटनक्रीडन-|मद-द्विरद-मस्तक-स्थल-विपाटन-क्रीडन-]]  
>    [[प्रहृत्त्यदुरुकेसरप्रसरभासुरः|प्रहृष्टोरु-केसर-प्रसर-भासुरः]] केसरी ॥ २३ ॥  

**प्रियरङ्गः** — [[मुद्रितमुखास्तिष्ठन्|मुद्रितमुखस् तिष्ठन्]] कथङ्कारं गणयतु ?  
**राजा** — [[भद्रौ|भद्रौ]] ! [[महायत्यतिक्रमो|महान् यत्यतिक्रमो]] [^42_1] न कार्यः ।  
**प्रियरङ्गः** — देव ! भिक्षुकैर् अस्माभिर् [[अलपायत्यतिक्रमोऽपि|अल्पोऽपि यत्यतिक्रमो]] न क्रियते ।  

[^42_1]: साद्वैता — पा.  

---
[[P43]]
### तृतीयोऽङ्कः  

**मायावादः** — (*सामर्षम्*) राजन् ! [[वैतालिकाभ्याम्लीकोक्तिविप्रलब्धः|वैतालिकाभ्याम् अलीकोक्ति-विप्रलब्धः]], किम् अस्मान् भिक्षून् परिभावयसि ?  

**प्रियरङ्गः** — [[सर्वप्रपञ्चालीकवादिन्|सर्व-प्रपञ्च-अलीक-वादिन्]] ! किं ते सत्यम् अपि किञ्चिद् वचनम् अस्ति ?  

**मायावादः** — (*स्वगतम्*) [[सकलराजकुलगोष्ठीसञ्चारचतुरयोरनयोः|सकल-राजकुल-गोष्ठी-सञ्चार-चतुरयोर् अनयोः]] उपच्छन्दनम् अन्तरेण न किञ्चिद् उत्तरं पश्यामि । (*प्रकाशम्*) वत्सौ ! युवयोः पाटवातिशयेन प्रीतोऽस्मि । युवां बालकौ वैतालिकौ सर्वैर् उपलालनीयाव् एव । [[युष्मद्गुरुन्तु|युष्मद्-गुरुं तु]] रामानुजस्योत्तरं अहं दास्यामि ।  

**प्रियरङ्गः** — (*सामर्षम्*) मयि स्थितेऽपि [[किमाचार्यानाक्षिपसि|किम् आचार्यान् आक्षिपसि]] ? न हि कण्टकः [[पादुकानिभिन्दन्|पादुकान् विभिन्दन्]] पादतलम् उल्लिखति ।  

**रङ्गप्रियः** — (*स्मितं कृत्वा*) वयस्य ! किम् अनेन परिश्रान्तेन । न हि कश्चिद् [[आतपगन्धं|आतप-गन्धं]] [[पुष्पमवतंसयति|पुष्पम् अवतंसयति]] [^43_1] ।  

(*नेपथ्ये*)  
> [[सुस्यानयुक्तमुनिकाञ्जिलजी अलोकः|सुस्नात-मुक्त-मुनि-काषाय-चोल-कल्पः]]  
>    [[शान्तानतस्वरमिक्षुभरीक्षणीयः|शान्तातपः सरसि भिक्षुभिर् ईक्षणीयः]] ।  
> प्रक्षीण-धूम-पटलः परिणाम-रम्यो  
>    भद्राय ते भवतु [[वासरपश्चिमभागः|वासर-पश्चिम-भागः]] ॥ २४ ॥  

**राजा** — (*सबहुमानम् अमात्यान् पश्यन्*) प्रत्यासीदति [[भवतामनुष्ठानवेलेति|भवताम् अनुष्ठान-वेलेति]] वैतालिक-गीतिर् अस्मान् अनुसारयति ; तन् महामात्यं पुरस्कृत्य गन्तव्यम् । किञ्च, वन्दिनः स्तुवन्तु निन्दन्तु वा ; राजकुल-वासिभिः विशेषतो वीतरागैर् भवद्-दर्शनं तद्-वचनं प्रमाणीकरणीयम् ।  

**मन्त्री** — महाराजेनापि तथैव मन्तव्यम् । (*इति भास्कर-यादवाभ्यां सह मन्त्री निष्क्रान्तः*)  

[^43_1]: सकलप्रपञ्च — पा.  

---
[[P44]]
**राजा** — (*[[यामुनमुत्तिष्ठन्तं|यामुनम् उत्तिष्ठन्तं]] पश्यन् सबहुमानम्*) भगवन् ! क्षणं क्षम्यताम् । [[काञ्चीपूर्णवचनं|काञ्चीपूर्ण-वचनं]] ते निगडीभवति ! (*विचार्य, [[वैतालिकवचनानन्तरमात्मान- मन्यथाभूतं|वैतालिक-वचनानन्तरम् आत्मानम् अन्यथा-भूतं]] पश्यामि ।*)  

**यामुनः** — (*विहस्य*) कथम् इव भवान् अन्यथा भवति ? [[राहुगृहीतः|राहु-गृहीतः]] शशी किं तथैव तिष्ठति ?  

**राजा** — (*साश्चर्यम्*)  
> पङ्काद् आशु समुद्धृत्य प्रक्षाल्य [[विमलांशुकैः|विमलाम्बुभिः]] ।  
>    प्रमृष्टम् एव पश्यामि रत्नं माम् अद्य निर्मलम् ॥ २५ ॥  

**यामुनः** — (*वैतालिकौ हस्ते गृहीत्वा*) वत्सौ ! युवाभ्याम् आवेदितः खलु [[रामानुजमति- नीतिविभावविस्तारः|रामानुज-मति-नीति-विभव-विस्तारः]] ?  

**राजा** — कः सन्देहः ? प्रतिबिम्बम् एव हि प्रमाणं बिम्ब-सौन्दर्यस्य ? भगवन् ! [[कावेतौ|कावे तौ]] [[रामलक्ष्मणाविव|राम-लक्ष्मणाव् इव]] [[विद्याकौशलेन|विद्या-कौशलेन]] गुरुं प्रकाशयतः ?  

**यामुनः** — वत्सौ ! प्रणमतं ब्रह्मविदं राजानम् ।  

**रङ्गप्रियः** — [[वाधूलोऽहं|वाधूलोऽहं]] [[दाशरथिरभिवादये|दाशरथिर् अभिवादये]] ।  

**प्रियरङ्गः** — [[वात्स्योऽहं|वात्स्योऽहं]] सुदर्शनो [[वरदविष्णुरभिवादये|वरदविष्णुर् अभिवादये]] ।  

**राजा** — (*[[सप्रणयकौतुकम्|सप्रणय-कौतुकम्]]*) किं ताव् एतौ, याभ्यां विना [[याभ्यां विना 'तु यतीन्द्रसन्न्यासः|न तु यतीन्द्र-सन्न्यास्यः]] [^44_1] — इति किंवदन्ती ?  

**यामुनः** — अथकिम् ।  

**राजा** — वत्सौ ! [[यतिराजप्रसादभूमी|यतिराज-प्रसाद-भूमी]] भूयास्तम् । (*विचिन्त्य*) सामर्ष इव मन्त्री गत इति पर्याकुलोऽस्मि ।  

**यामुनः** — देव ! न तथा भेतव्यम् ।  
> किं सर्पो गरुडस्य [[पक्षपवनक्रीडाभिघाताक्षमः|पक्षपवन-क्रीडाभिघाताक्षमः]] [^44_2] ?  
>    किं [[कण्ठीरवकण्ठगिर्जितमपि|कण्ठीरव-कण्ठ-गर्जितम् अपि]] श्रोतुं समर्थः करी ? [^44_3]  

[^44_1]: न — पा.  
[^44_2]: पक्षपवनक्रीडामिघात — पा.  
[^44_3]: कीडाभिघाताक्षमः — पा.  



[[P45]]
### तृतीयोऽङ्कः  

> यद्य् अप्य् एवम् अयं यतीश्वर-कशा-घातेन मन्दीभवद्-  
>    गर्वो दुर्विषहेण याति [[दिलयं|विलयं]] क्वापि विलासिनः ॥ २६ ॥ [^45_1]  

**राजा** — (*[[सधर्षम|सहर्षम्]]*) सम्प्रति समाश्वस्तोऽस्मि ।  
**यामुनः** — देव ! वैतालिकयोः प्रसादः कार्यः ।  
**राजा** — (*विचिन्त्य*) स्वात्मदानं विना नान्यद् अनयोः सदृशं पश्यामि ।  
**वैतालिकौ** — (*सहर्षम्*) [[मृत्यजनस्येयमेव|भृत्य-जनस्य अयम् एव]] खलु स्वामी । (*समन्ताद् अवलोक्य*) पश्य —  

> [['प्राच्यालेम्यतुलां|प्रायः पत्रतुलां]] प्रयाति भुवनं स्प्रष्टुं तमः-कन्दलैः  
>    दृश्यन्ते [[प्रतिकर्मभिश्च|प्रतिकर्मभिस् च]] सुदृशो [[देहान्तगन्धा|देहाङ्ग-गन्धा]] इव ।  
> [[गृहदीपकश्च|गृह-दीपाश्च]] विमला [[धीवन्महायोगिनाम्|धिय इव महायोगिनाम्]]  
>    [[मन्योपास्तिमियं|सन्ध्योपास्तिम् इयं]] तनोति [[मुकुलव्याजाञ्जलिः|मुकुल-व्याजाञ्जलिः]] पद्मिनी ॥ २७ ॥  

**राजा** — (*समन्ताद् अन्धकारं पश्यन्, साश्चर्यम्*)  
> येन स्पष्टम् [[स्पष्टमदृष्टिगोचरतया|अदृष्टि-गोचरतया]] सत्ता-अतिरिक्तं जगत्  
>    मिथ्येति प्रतिभाति मिलितम् इतो [[भेदप्रपञ्चोद्रमः|भेद-प्रपञ्च-उद्गमः]] ।  
> [[आनन्दन् मुखमन्धकारमुदयीमज्ञानपारं परं|आनन्द-मुखम् अन्धकारम् उदयम् अज्ञान-पारं परं]] [^45_2]  
>    अद्वैतस्य पिता, गुरुः, किम् अथवा, किं वा तद् एव स्वयम् ॥ २८ ॥  

तस्माद् अस्माकम् अपि [[नियमकालोऽतिक्रामति|नियम-कालोऽतिक्रामति]] ।  
(*इति निष्क्रान्तास् सर्वे*)  

#### इति श्री घटिकाशत-श्रीमद्वरदाचार्य-विरचिते वेदान्त-विलासापरनाम्नि "यतिराजविजयानाटके" वैतालिकप्रवेशो नाम तृतीयोऽङ्कः ।  

[^45_1]: यद्यप्येवम् — पा.  
[^45_2]: इह या म.  

---
[[P46]]
## चतुर्थोऽङ्कः  

(*ततः प्रविशति जनकः*)  

**जनकः** — भो भोः ! भवन्तः शृण्वन्तु ।  
> प्रद्युम्नेन जितो गुहः, प्रतिहतो रामेण लम्बोदरो  
>    हा रुद्रो [[हरिहुङ्कृतो|हरि-हुङ्कृतो]] यद्-भटा [^46_1] गर्जन्ति जित्वा गणान् ।  
> बाणं लून-भुजं [[हगाय स हरिलेड्याऽनिरुद्धोऽप्यनन्|जगाद स हरिर् लीलया अनिरुद्धोऽपि यत्]] [^46_2] -  
>    भिक्षाम् ईश्वर एष इत्य् अमरवाग् आयुष्मती पातु वः ॥ १ ॥  

अहो ! विशृङ्खलः खलु विष्णोः [[शुभाश्रयलक्षण-मुमुक्षूपास्य-दिव्यमङ्गल-|शुभाश्रय-लक्षण-मुमुक्षूपास्य-दिव्य-मङ्गल-]] विग्रहस्यानुभवः ।  

> संविन्मयं [[सकलतत्त्वविभूषणालं|सकल-तत्त्व-विभूषणाढ्यं]]  
>    रूपं स्मरन् परमसाम्यम् उपैति विष्णोः ।  
> [[अज्ञानदोषविरहादखिलैश्च|अज्ञान-दोष-विरहाद् अखिलैस् च]] भोगैः  
>    [[ज्ञानादिमङ्गलगुणैश्च|ज्ञानादि-मङ्गल-गुणैस् च]] भवत्य् अभेदी ॥ २ ॥  

(*पुरोऽवलोक्य*)  
> [[सन्यासिनी समायात कषा|सन्न्यासिनी समायाति का एषा]] काषायधारिणी ।  
>    [[विरक्तिरथ|विरक्तिर् अथ]] निर्द्वन्द्वा किं वा शान्तिः [[शरीरिणी|शरीरिणी]] ॥ ३ ॥  

(*निरूप्य*) आः ज्ञातं, विष्णुभक्ता भगवती गीतैव ।  

(*ततः प्रविशति गीता*)  

**गीता** — अहो ! मुमुक्षून् प्रति भगवद्-औदार्यम् ! [[कर्मज्ञानादियोगैराश्रितानेतान्|कर्म-ज्ञानादि-योगैर् आश्रितान् एतान्]] [[यदात्मसमान|यद् आत्मसमान्]] पश्यति ।  

**जनकः** — तावद् एनाम् उपसङ्गच्छामि । (*[[ब्रह्मवादिनीमुपसृत्य|ब्रह्मवादिनीम् उपसृत्य]]*) भगवति ! नमस्ते ।  

[^46_1]: यद्भुवा — पा.  
[^46_2]: यदु — पा.  

---
[[P47]]
**गीता** — वासुदेव-प्रसाद-पात्रं भूयाः ! वत्स ! [[खाण्डिक्ययाग मुक्तौ|खाण्डिक्य-जनक-मुक्तौ]] किम् उक्तं त्वया, [[परजीवयोरभेदलक्षणं|पर-जीवयोर् अभेद-लक्षणं]] स्वरूपैक्यम् ?  

**जनकः** — न हि न हि ; [[स्वभावैक्यम् ।|स्वभावैक्यम् ।]] (*सविस्मयम् । इत्यादि पुनः तद् एव पठति*)  

**गीता** — तर्हि त्वयि [[स्वकीयववुरि|स्वकीय-वपुषि]] [[मायावादप्रभृतीनां|मायावाद-प्रभृतीनां]] "उन्मुखेन शिरःकण्डूयनम्" एव पर्यवस्येत् ।  

**जनकः** — कः सन्देहः ? न हि कश्चिद् अस्मिन् राजकुले भवतीम् उल्लङ्घयति । (*विलोक्य*) [[किन्निमित्तमस्य ;|किं निमित्तम् अस्य ;]] अथवा, सम्भवत्य् एव कदाचित् [[त्रिजककलत्र-|निज-कलत्र-]] प्रीतिः ।  

**गीता** — (*विहस्य*) [[मिथ्यादृष्टिविमोहितस्य|मिथ्यादृष्टि-विमोहितस्य]] न कदाचिद् अपि तत् सम्भवि । तथापि, [[यतिराजशिष्याभ्यां|यतिराज-शिष्याभ्यां]] [[गृहीतवैतालिकवेषाभ्यां|गृहीत-वैतालिक-वेषाभ्यां]] प्रविश्य प्रकाशित-बहु-नीति-विप्लवे मन्त्रिणि मायावादे विरक्त-हृदयः, तत्-पदे [[निरवद्यनिखिलनीतिविभवं|निरवद्य-निखिल-नीति-विभवं]] रामानुजं निवेश्य, [[तदनुरोधेन|तद्-अनुरोधेन]] देवो देव्या सुमतौ किञ्चित् साभिलाष इव तिष्ठति । तद्-अनुराग-वर्धनाय भगवतीं [[लक्ष्मीमाराधयितुं|लक्ष्मीम् आराधयितुं]] फल-कुसुमादि-सम्पादनाय व्यापृताऽस्मि ।  

**जनकः** —  
> [[दयापन्नसार्वभौम सुर मेधासाकुलैः युन्नतैः|दयावन्-सार्वभौम-सुर-मेधा-सङ्कुलैः उन्नतैः]] ।  
>    [[मृगार्द्रान्तिकैरैलङ्कृतमुखाभाजा स्थिता वक्षसि ।|मृग-आर्द्रान्तिकैर् अलङ्कृत-मुखाभासा स्थिता वक्षसि ॥]]  
> स्वच्छ-छायावति कौस्तुभे कृत-पदा पत्न्यन्तराशङ्कया ।  
>    क्रीडा-पङ्कज-ताडिता [[प्रियनमा|प्रियतमा]] देवी प्रसन्नाऽस्तु ते ॥ ४ ॥  

तर्ह्य् अहम् अपि ते सहकारी भवामि (*इति तया सह निष्क्रान्तः*)  

#### इति विष्कम्भः ।  

---
[[P48]]
(*ततः प्रविशति [[रामानुजदत्तहस्तो|रामानुज-दत्त-हस्तो]] राजा यामुनश्च*)  

**राजा** — (*पुरोऽवलोक्य सानन्दम्*)  
> पौरन्दरीं तिलकयन् ककुभं कराग्रैः  
>    [[चन्द्रस्य एष|चन्द्र एष]] [[हरिचन्दनपङ्कताम्रैः|हरिचन्दन-पङ्क-ताम्रैः]] ।  
> [[आस्वादयत्यधरबिम्बमिमां|आस्वादयत्य् अधर-बिम्बम् इमां]] सरागां  
>    [[आलोकितः|आलोकितः]] [[प्रणयपेशलमङ्गनाभिः|प्रणय-पेशलम् अङ्गनाभिः]] ॥ ५ ॥  

(*पार्श्वम् अवलोक्य, सस्मितम्*) [[सन्यासिनीधृतसकलसांसारिकवृत्तान्तयोर्युवयो-|सन्न्यासि-निधृत-सकल-सांसारिक-वृत्तान्तयोर् युवयोः]] [^48_1] एतद् आकर्णनम् अपि [[कर्णयोरुच्छ्रवाय|कर्णयोर् उच्छ्रवाय]] ।  

**गीता** — (*कर्णौ पिधाय*) न हि न हि,  
> [[भवन्मुखसमुद्भूतं|भवन्-मुख-समुद्भूतं]] सर्वं [[संसारभेषजम्|संसार-भेषजम्]] ।  
>    [[मातुःस्तनविनिष्छ्युतं|मातुः स्तन-विनिःस्रुतं]] पयो भवति किं विषम् ॥ ६ ॥  

**यामुनः** —  
> गृहिणोऽपि [[तवादेशकारिणो|तव आदेशकारिणो]] विषया अपि ।  
>    [[स्वकलत्रोपभोगाद्याः|स्वकलत्रोपभोगाद्याः]] कल्पन्ते [[मुक्तिहेतवः|मुक्ति-हेतवः]] ॥ ७ ॥  

देव ! दीयताम् इतो दृष्टिः ।  

> [[आमीलद्द्विरवेध्य|आमीलद्-द्विरेफे]] [[पत्रनिचयैस्तन्निरुद्धां|पत्र-निचयैस् तन्-निरुद्धां]] प्रियां  
>    [[आधावन्मधुपानकेलिविवशामाक्रष्टुमिच्छन्|आधावन् मधुपान-केलि-विवशाम् आक्रष्टुम् इच्छन्]] बहिः ।  
> पक्षाभ्यां परिताडयन् [[पदविखैः|पद-नखैः]] [[पर्यायातः|पर्यायतः]] पाटयन्  
>    तुण्डाग्रेण च खण्डयन् मधुकरः पङ्केरुहं क्रोशति ॥ ८ ॥  

**राजा** — [[प्रणयरसपरभूमिः|प्रणय-पर-भूमिः]] [^48_2] खलु दाम्पत्यम् । (*पुरोऽवलोक्य सानुरागम्*)  
> आनीलां [[करपल्लवैरपनयन्|कर-पल्लवैर् अपनयन्]] गाढं [[तमःकन्दलीम्|तमः-कञ्चुलीम्]] [^48_3]  
>    आशां सम्प्रती [[वासवीमनुभवन्नक्षीणरागः|वासवीम् अनुभवन्न् अक्षीण-रागः]] शशी ।  

[^48_1]: सन्यासिनिधृत — पा.  
[^48_2]: प्रणयपरभूमिः — पा.  
[^48_3]: कञ्चुलीम् — पा.  

---
[[P49]]
> [[अस्याश्च स्तनसङ्गिनीमिव|अस्यास् च स्तन-सङ्गिनीम् इव]] वहन्न् अङ्गेन कस्तूरिकां  
>    [[आश्लिष्यत्यमयादरेण|आश्लिष्यत्य् अमूम् आदरेण]] [^49_1] रजनीम् अर्धोन्मिषत्-तारकाम् ॥ ९ ॥  

**यामुनः** — (*राजानं चक्षुषा निर्दिशन्, जनान्तिकम्*) अयम् इदानीम् इन्द्रियैः दूरम् उन्माद्यति ।  

**रामानुजः** — एवम् अप्य् अस्य भवतु [[रागोत्पीडः|रागोत्पीडः]] । स कदाचित् स्थाने पतिष्यति । देवी सुमतिस् च [[किवदुत्सुका|किञ्चिद् उत्सुका]] तिष्ठति ।  

**यामुनः** — कथम् एतत् सम्भवति ? यद् एष [[सकललोकविप्रलम्भचतुरया|सकल-लोक-विप्रलम्भ-चतुरया]] [^49_2] [[मायाविलासिन्या|माया-विलासिन्या]] वशीकृतः, तया मुक्तोऽपि न तां मुञ्चति । तज् जानती सुमतिस् च मानवती तं न गणयति ।  

**यतिराजः** — तत् तथैव ; तथापि, [[मद्दर्शितसूतमागानुसारिणी|मद्-दर्शित-सूत-मार्गानुसारिणी]] सुनीतिः, [^49_3] [[व्याजकलुषितौ|व्याज-कलुषितौ]] तौ संयोजितुं प्रभवति ।  

**यामुनः** — तथा सति [[सम्भवेदेव|सम्भवेद् एव]] ।  

**राजा** — किं भवन्तौ मन्त्रयतः ?  

**यामुनः** — [[स्वस्यैव ललिते सति|स्वस्यैव मुखालङ्करणे सति]] [^49_4] [[मन्त्रिण्वेव|मन्त्रिष्व् एव]] [^49_5] कार्यभारः पर्यवस्यति ।  

**राजा** — (*[[स्मयते|स्मितं करोति]]*) [^49_6]  

(*ततः प्रविशति सुनीतिः*)  

**सुनीतिः** — देवः, सम्प्रती [[स्वचरितनाटकावलोकनसमये|स्वचरित-नाटकावलोकन-समये]] [[मिथ्यादृष्टिभूमिकां|मिथ्यादृष्टि-भूमिकां]] परिगृह्य प्रवृत्ते वैदेशिके भरते, [[द्रष्टुदुष्टम हास्यचेष्टायां|द्रष्टुः दुष्ट-महा-हास्य-चेष्टायां]] मिथ्यादृष्टौ, किञ्चिद् विरक्त-  

[^49_1]: हूटयन् — पा.  
[^49_2]: सकललोकविप्रलम्भचतुरया मिथ्यादृष्ट्या मोहतः — पा.  
[^49_3]: सुनीतिस्तु तेन राज्ञा संयोजयितुम — पा.  
[^49_4]: स्वस्यैवमुखालने — पा.  
[^49_5]: कार्यचिन्ता — पा.  
[^49_6]: स्मितं करोति — पा.  



[[P50]]

यतिराजविजयम्-नाटकम्

हृदयस् तिष्ठति। यद् अयम् एवावसरो देवेन देवीं योजयितुम्। (पुरो ऽवलोक्य।)  
जयतु समित्रामात्यो देवः।

**राजा** — (सादरं पश्यति)

**यामु** — भद्रे! किंचिद् आकुलैव लक्ष्यसे।

**सुनी** — (स्मितं कृत्वा) यतिराजे महा-मन्त्रिणि किम् आकुला भवामि?

**राजा** — (विहस्य) सोल्लुण्ठम् इव प्रतिभाति।

**यामु** — तत् तु देवो जानाति।

**यति** — (सस्मितम्) सुनीतिं प्रति किंचिद् रहस्यम् इव देवस्य; तद् आवां बहिरङ्गम् एव।

**राजा** — किं चक्षुषी बहिरङ्गम्?

**सुनी** — चक्षुषो ऽपि राज्ञां सुनीतिर् अन्तरङ्गम् एव।

**यति** — (स्वगतम्) इयम् एकान्ते देवम् अनुकूलयितुम् आप्तैव। तद् अस्माभिर् अवकाशो देयः। (प्रकाशम्) यावन् नियम-शेषं निर्वर्त्य समागच्छामः; तावद् इयं देवं विनोदयतु। (जनान्तिकं) भद्रे! सिद्धम् अनुवदामि।

> युक्तायुक्त-निरूपणं सदृशयोः संयोजनं क्रुद्धयोः  
> क्रोधस्योपरमं विधातुमपि ते लीलैव [[यद्द्रामिणि!|यद् भामिणि!]] ।  
> तत् संयोजयितुं यतस्व गणिका-संसर्ग-[[जातेर्ष्या|जातेर्ष्यया]]  
> देव्या देवम् उदार-शील-गुणया नान्या गतिस् त्वं विना ॥ १० ॥  

(इति यामुनेन सह निष्क्रान्तः)

**राजा** — (सुनीतिं हस्ते गृहीत्वा) प्रियसखि! सत्यम् एव ब्रूहि। त्वत्-प्रिय-सखी किम् अस्मान् गणयति; कदाचिद् अङ्गीकरिष्यति वा?

**सुनी** — तद् एव [[एव|देवो]] निरूपयतु; स्व-दोषः किं [[प्रत्यहतीति|प्रत्येतीति]]। (विचिन्त्य)

---

[[P51]]

चतुर्थॊऽङ्कः

> देवी तिष्ठतु सा मम प्रिय-सखी देव! त्वया चिन्त्यतां  
> मिथ्या-दृष्टि-विलास-मोहित-मतिः किं किं न कुर्याद् इति ।  
> तत्त्वं द्रष्टुम् अपि प्रगल्भ-गणिका-धूर्ते न सम्मन्यते  
> देवी किं त्व् अनुनीति-कल्पलतिका देवस्य हस्ते स्थिता ॥ ११ ॥  

**राजा** — देवीं कथम् इदानीम् अपि पश्यन् नानुयामि (सखेदम्)

> मलय-पवनो मर्म-च्छेदी मधुव्रत-निःस्वनः  
> श्रवण-परुषो वर्षत्य् अग्निं स्फुलिङ्ग-मयं शशी ।  
> भवति च मनः-शल्यं माकन्द-भूरुह-मञ्जरी  
> सुमति-विरहे सर्वो लोको भवत्य् अयम् अन्यथा ॥ १२ ॥  

**सुनी** — सुमति-संयोगे पुनर् अपि सर्वं यथावस्थितं भवत्य् एव।

**राजा** — (विचिन्त्य)

> आजिघ्रन् मुख-पुण्डरीकम् अमलाम् आसज्य गण्ड-स्थलीम्  
> आचुम्बन् अनुभवायन्न् अनुभवन् अन्तर्-विशन्तीम् इव ।  
> आश्लिष्यन् दृढम् अपि [[चिन्नैव|चिन्न् एव]] दृशा पश्यन् मुहुः प्रेयसीम्  
> आत्मानं चरितार्थयामि सखि! ताम् आनेष्यसि त्वं यदि ॥ १३ ॥  

**सुनी** — देव! किम् एवम् आज्ञा-प्रतीक्षे दास-जने स्वातन्त्र्यम् आरोपयसि? सम्यग् आनीताम् एव देवीं द्रक्ष्यसि ।

**राजा** — (सलज्जम्) दुर्मन्त्रि-वचनात् ईदृश-प्रेम-शालिनीं त्वाम् अपि दूरीकुर्वतो मे लालित्यम् अपि दोषाय ।

**सुनी** — (सभयम्) देव! मैवं अनुतप्तुम् अर्हसि। सर्वस्यापि प्रभवति खलु स्वामी। संप्रति देवप्रसादेन कृतार्था ऽहं देवीम् अपि कृतार्थयामि। (इति निष्क्रान्ता)

**राजा** — (देवीं विचिन्तयन्)

> सासूये शफरी-विवृत्तिषु दृशौ [[शाङ्गं|शार्ङ्गं]] न शङ्कास्पदं  
> भ्रू-वल्ली ललितस्य कैशिक-तुला वैदेशिकं शैवलम् ।  

---

[[P52]]

यतिराजविजयम्-नाटकम्

> को मेरुः कुच-मण्डलस्य भुजयोः को ऽप्य् अन्तरे वल्लरी  
> शङ्के चन्द्र-कथा ऽपि साहस-पदं तस्याः स्मृतं चेन् मुखम् ॥ १४ ॥  

(परितो ऽवलोक्य, ) हा चित्रम् एतत् ।

> सस्मित-मुखारविन्दा सर्वकष-नयन-विभ्रम-विशेषाः ।  
> [[घनकुचविनम्रमध्याः|घनकुचविनम्रमध्याः]][^52_1] ककुभः पश्यामि[^52_2] चिन्तयन् देवीम् ॥ १५ ॥  

[^52_1]: कुचयुगलभारनम्राः - पा०
[^52_2]: दरसे - ग०

(श्रुतिम् अभिनीय) किम् एतत् कल-शिञ्जितको ऽपि शब्दः कर्ण-विवरम् आह्लादयति? (विमृश्य सहर्षम्) मुखर-मञ्जीरा देवी समागता स्यात्।  
(ततः प्रविशति सुनीतिम् अंसे गृहीत्वा [[गीनयाऽनुगम्यमाना|गीतया ऽनुगम्यमाना]] सुमतिः)

**सुम** — हळा! अञ्ज उंत्तंस (इत्य् अर्ध-उक्ते)

**गीता** — (सभयम्) देवि! विरम, विरम। सुमतिर् अपि किं भरत-शापं विस्मरसि ।

**सुम** — (सभयम्) अम्ब! चिन्ताकुला नात्मानम् अपि जानामि। सखि! आर्यपुत्रस्य कथम् आत्मानं दर्शयामि, यः पुनर् एवम् अति-कश्मले रथ्याम्भसि आत्मानं पतितवान् ।

**गीता** — भद्रे! तस्य तादृश-वार्धक्य-संयोगो निरूप्यमाणः, प्रवादम् अन्तरेण परमात्म-विदो न संभवति; संभवे ऽपि नास्य प्रायश्चित्तं पश्यामि। किन्तु, विष्णु-भक्ति-रूपयैव प्रायश्चित्तवान् भवति।

**सुनी** — देवि! भगवत्या वचनम् अनुपालयस्व (इति पादयोः पतति)

**सुम** — (अधोमुखा बाष्पं मुञ्चति)

**सुनी** — (सपरितोषम्) सो ऽयम् अभिषेको महा-राज-मनोरथ-साम्राज्यस्य।

**गीता** — (पाणिभ्याम् अश्रु प्रमार्जयन्ती सपुलकोद्भेदम्) शीतल-स्पर्शो ऽयम् अन्तराह्लादम् आवेदयति।

---

[[P53]]

चतुर्थॊऽङ्कः

**सुनी** — इत इतो देवी!

**सुम** — सखि! किम् एतद् इति न जानामि।

> पादौ जडौ भवति लोचनम् अश्रु-पूर्णं  
> [[कम्पोत्तरं भवति|कम्पोत्तरं स्तन-तटं]][^53_1] घन-वेपथु-कम्पम् ।  
> कामश् च चेतसि करोति विरोधम् अन्यः  
> शक्नोमि गन्तुम् अधुना न समुद्यतो ऽपि ॥ १६ ॥  

[^53_1]: कम्पोत्तरस्तनतटं - अ०

**सुनी** — (स्मितं कृत्वा) सात्त्विको ऽयं विकारो देवीं जडयति ।

**सुम** — (विमृश्य सरोपं पश्यन्ती) प्रियसखि! मुञ्च माम्। [[अलमुपालम्भेन|अलम् उपालम्भेन]][^53_2]; त्वम् अपि [[मानिन्थ्यासि|मानिन्य् असि]]।

[^53_2]: अनलमुपालम्भेन - पा०

> मानं जीवितम् आमनन्ति सुदृशां तद्-भङ्गम् अप्य् आचरन्  
> दृष्टः खण्डन-हेतुभिः स दयितो दृष्टश् च नादर्शिनी ।  
> किं जीवन् सुमतिः कृतं तव गिरा सर्वं [[महस्यान्यथा|मया स्यान्यथा]]  
> निन्द्या मादृश-[[सनि|जनी]] धूर्त-गणिका-[[मार्माल्य|निर्माल्य]]-भोगाद् अहम् ॥ १७ ॥  

**उभे** — (सभयम्) देवि! प्रसन्ना ऽपि क्षुद्रनदीव किं कलुषा भवसि?

> शून्या त्वं लिखितेव तिष्ठसि वपुः शोभावशेषाकृतं  
> [[श्वासैर्निर्मलपितं|श्वासैर् म्लापितं]] मुखं तव शरन्-मीनोपमं लोचनम् ।  
> सर्वं वेत्सि विमुञ्च [[माननि रुगं|मानिनि रुषं]] चन्द्रो ऽपि अयम् [[मादृशा|मादृशः]]  
> दृष्टः [[सशयभागनः|संशय-भाजनः]] स दयितो ऽप्य् आत्मा च रक्ष्यस् त्वया ॥ १८ ॥  

**सुम** — यद्य् अपि सर्वम् इदं जानामि, तथापि [[अस्मद्भावसुलभो|स्त्री-भाव-सुलभो]] मानो मे निगळी-

---

[[P54]]

यतिराजविजयम्-नाटकम्

भवति।

**सुनी** — [[तथाऽप्यस्य|तथा ऽप्य् अस्य]][^54_1] कदाचिद् अन्तो भवत्य् एव । यतिराजेन सह मन्त्रितम् एव च देवेन — “सर्वम् इदं राज्यं देव्या एव; सुमति-वल्लभत्वान् ममापि” इति। किञ्च, मिथ्यादृष्टि-स्नेहम् अपि मिथ्यैव देवस्य इति, तद्-परिजन-वचनम् अपि किं न श्रद्दधासि?

[^54_1]: तथाऽपि - पा०

**सुम** — (स्मितं कृत्वा) सर्वं राज्यं दयित एव स्त्रीणाम्। (विचिन्त्य) प्रिय-सखि! तस्मिन्न् अनुस्मृते नाहम् आत्मनो ऽपि प्रभवामि। यत् संप्रति,

> तत्-कण्ठ-ग्रहणाय धावति पुरो दोर्-वल्लरी मां विना  
> वक्षोजौ मम वल्गतः पुलकितौ तद्-वक्षसि क्रीडितुम् ।  
> चक्षुस् तन्-मुखम् ईक्षितुं [[जिगमिषत्यामेच्छ्या|जिगमिषत्येवेच्छया]] तद्गतं  
> [[न प्रत्येति|न प्रत्येति]][^54_2] पुनर् मनः कथय मे कार्यं न जानाम्य् अहम् ॥ १९ ॥  

[^54_2]: नाप्येति - पा०

**राजा** — (चन्द्रं विलोक्य विहस्य च)

> कामो मे रिपुरेव चन्द्र-मरुतौ! कामं स मां बाधताम्  
> [[युक्तं मां युयोः|युक्तं वां युवयोः]] [[किमात्मसुहृदं|किम् आत्म-सुहृदं]] दग्धुं [[जगच्छोतयोः|जगत्प्राणयोः]] ।  
> प्राप्तं वह्नि-सखस्य तद् [[तद्व्रतु|युक्तं]] वा चन्द्र! त्वया शाम्यतां  
> [[नो चेन्मत्सुहृदातिवाहिकसभामध्ये|नो चेन् मत्-सुहृद्-आतिवाहिक-सभा-मध्ये]][^54_3] कथं स्थास्यसि ॥ २० ॥  

[^54_3]: नोचेत्त्वं सुहृदा-बाह्निक - पा०

(इति मूर्च्छति)

**सुनी** — (पुरो ऽवलोक्य, सभयम्) प्रिय-सखि! सुमतिर् अपि किं न पश्यसि; तद्-विरहातिशयेन देवः किंचिद् अप्य् अजानन्न् अचेतन इव किं विवशस् तिष्ठति। तद् एनं आश्वासयावस् तावत्। (इति सर्वा राजानम् उपसर्पन्ति)

**सुनी** — (सभयं) हा कामुक! कृतार्थो ऽसि [[शतुहननेन|शत्रु-हननेन]]।






[[P60]]

पञ्चमोऽङ्कः

(ततः प्रविशति सुदर्शनः)

**सुद्** — (विमृश्य) यतिराज-प्रेषितेन मया [[पथिकमुखान्|पथिकवेषेण]]-मायावाद-वृत्तान्तो विदितः। यथा किल—मायावादः शंकरं पुरस्कृत्य केरळैस् संभूय सङ्कट-स्थाने दुर्गामार्गाढ्य-तत्-प्रसाद-लब्ध-विविध-माया-युक्ति-शक्ति-विभवो रामानुज-विजयाय मेघनाद इव प्रस्थितः। तद् अस्यार्थम् उद्यताव् अपि वृद्धौ ध्यान-नियोग-वादी निष्प्रपञ्चीकरण-नियोग-वादी च शंकर-द्वेष-निवृत्तौ। वाक्यार्थ-ज्ञान-वादिनौ च शंकर-शिष्यौ जीव-बहुत्वैकत्वे प्रति परस्परं कलहायमानौ क्व गताव् इति न [[ज्ञायत|ज्ञायते]] इति। तद् इदं वृत्तान्तं गुरवे निवेदयामि।

(इति निष्क्रान्तः विष्कम्भः)

(ततः प्रविशति संक्रुद्धः संन्यासी शुक्लपटश् च)

**संन्या** — भो भो दुरात्मन्! शंकर-श्रीपाद-शिष्यो ऽपि किम् एतां यज्ञोपवीत-वत् कण्ठ-ग्राहिणीं भेद-वासना-पिशाचीं च न मुञ्चसि?

**शुक्ल** — (सरोषम्) अनात्मज्ञ! प्रच्छन्न-बौद्ध-संन्यासिन्! मर्मज्ञं मामपि किं [[प्रकोष-|प्रकोप-]]यसि? नमस्करण-न्यायेन अवैदिकं ते दर्शनम्। निर्वाण-निष्ठं प्रतिनियत-[[बन्धमोक्षादिदिभिं|बन्ध-मोक्षादिभिः]] [[भेद-वाक्यैर्|वेद-वाक्यैर्]] अलङ्कर्तुं काश-कुशम् अवलम्ब्य जीव-भेदं परिकल्पयामि। तद् अपि न मृष्यसि?

**संन्या** — (सक्रोधं दन्तान् संपीज्य) कथं मृष्यामि दुस्तर्क-वादिनस् ते पाण्डित्यम् [[तर्हि|तावत्]] ब्रूहि ब्रह्मण्य् एकपत्नी-व्रते धारयन्त्य् अविद्या, कति कति वा जीव-चण्डालान् आलिङ्गति?

---

[[P61]]

पञ्चमोऽङ्कः

**शुक्ल** — त्वम् एव तावद् ब्रूहि, अज्ञान-रूपेयम् अविद्या-चण्डाली ज्ञान-रूपं ब्रह्म कथंकारं शिरसि गृहीत्वा ताडयति?

**संन्या** — (सक्रोध-संभ्रमं, शिखायां ब्रह्म-सूत्रे च गृहीत्वा) द्वैत-पाताल-पतित-धूर्त-प्रलापनिस् ते दन्त-खण्डनं करोमि। (इति [[दण्डकम्|दण्डमूलम्]][^61_1] उद्यच्छति)

[^61_1]: दण्डमूलम् - पा०

**शुक्ल** — (सक्रोधं पश्यन्) कथम् एनं सर्वाश्रम-[[परिय्रष्टं|परिव्रष्टं]] गृह्णामि;

> न शिखा नोपवीतं च न स्पृहा चान्य वाससि ।  
> गळ एव ग्रहीतव्यं पतितं पातयाम्य् अहम् ॥ १ ॥  

(इति गळे हठाद् गृह्णन्, पुरो ऽवलोक्य, सभयम्) कथम् इहैव राजा समागच्छति। तद् इतः गच्छामि। (इति तम् आक्रोशन्तम् एव अनुकर्षन् निष्क्रान्तः)

(ततः प्रविशति राजा देवी च)

**राजा** — (समन्ताद् अवलोक्य सकौतुकम्) [[देवि!|देवि, पश्य पश्य]][^61_2] दीयताम् इतो दृष्टिः।

[^61_2]: देवि, पश्य पश्य - गा०

> सदयं स्पृशन् करैर् रागी कण्टकित-गात्र-लतिकायाः ।  
> पातुम् एवेच्छति भास्वान् पद्मं मुखम् इव विकासि पद्मिन्याः ॥ २ ॥  

**राजा** — (सामिलाषं देवी-मुखं पश्यति)

(नेपथ्ये)

रे रे राजकुल-वासिनः परिस्पन्दाः!

> सन्त्य् एवान्ये ऽपि लोके सकल-बहुमत-द्वैत-विद्या-वलेपाः ।  
> किं तैर् उद्वेग-वार्ता-द्विरद-मद-[[मदमून्माद-विवस्तचित्तैः|मदुन्माद-विवश-चित्तैः]] ।  
> मातृ-प्राभाकरादि-प्रतिभट-समय-प्राण-सर्वस्व-हारी  
> संप्राप्तः [[शंकरोऽयं क्व नु खलु वसति वृत रामानुजो वः|शङ्करो ऽहं, क्व खलु स वसति वत रामानुजो वः]][^61_3] ॥ ३ ॥  

[^61_3]: शङ्करोऽहं, क्व खलु स वसति - पा०

**देवी** — (तच्छ्रुत्वा सभयोत्कम्पम्) को ऽसौ महाराक्षसः! (इति समाकुला राजानम् आलिङ्गति)

---

[[P62]]

यतिराजविजयम्-नाटकम्

**राजा** — मानिनि! मयि स्थिते किं भयेन? (ततः प्रविशति सशिष्यो रामानुजः, सुनीतिर् यामुनश् च)

**रामा** — (सावष्टम्भम्) महाराज! सुमत्या सह विहरन् विजयस्व। तिष्ठामि खलु, ते [[वीरस्य धीरत्वनुपलालयितुम्|वीरस्य लालित्यम् उपलालयितुम्]][^62_1]।

[^62_1]: वीरस्य लालित्यमुपलालयितुम् - पा०

(पुनर् नेपथ्ये)

> वल्गत्-खड्ग-निपात-निष्ठुर-महात्काराभिघात-लुटद्  
> द्वैत-मन्त्रि-सिरा-मुख-स्रवद्-असृग्-धारा-कमलाराधिनाम् ।  
> कालीं केरळ-केलि-कल्पलतिकां कालानलोद्गारिणीम्  
> प्राप्तः [[श्रीणयितुं|प्रीणयितुं]] प्रवादक-शिरोमुण्डोपहारैर् अहम् ॥ ४ ॥  

**रामा** — (विहस्य, ) [[महाभैरवमन्त्रिसिद्धो|महाभैरवमन्त्रसंवृद्धो]][^62_2] मायावादः, शंकर-सहितः केरळ-देशाद् आगत्य, गर्जति।

[^62_2]: मन्त्रसंवृद्धः - पा०

(ततः प्रविशति शंकर-भुजावलम्बी संक्रुद्धो मायावादः)

**शङ्क** — (सरोषं पश्यन्) को ऽयं रामानुजो नाम?

**सद्-दू** — यच्-शिष्यो ऽहम् अस्मि।

**शङ्क** — तम् एव वेदितुम् इच्छामि।

**सद्-दू** — वाद-प्रतिभुवि मयि स्थिते किम् असद्-गुरुम् अन्वेषयसि? न हि कण्टकः पादुकम् [[मभिन्दन्|अभिन्दन्]] पाद-तलम् उल्लिखति?

**शङ्क** — (सावज्ञम् अन्यतो ऽवलोकयति)

**सद्-दू** — (सक्रोधम्) जाल्म! किं माम् अवजानासि। अरे!

> सप्त-द्वीप-त्वदीय-खल-जन-गति-च्छादनेच्छासमुद्यन्-  
> माया-सिद्धान्त-कथा-शत-लवन-कला-कर्तरी-वृत्तिर् एषः ।  
> सम्यग्-व्यूहः सद्दृहः सदसि यतिपतेः तन्तुपालस् त्वया किं?  
> दृप्यद्-दुर्वादि-वर्ग-क्षपण-मन्त्र-विधौ दीक्षितो नेक्षितो ऽहम् ॥ ५ ॥  

---

[[P63]]

पञ्चमोऽङ्कः

**शङ्क** — (सामर्षं तिर्यग् विलोकयन्) कथं न पश्यामि? अस्ति खलु मे [[शंकरस्येव|शिशुपालस्येव]][^63_1] दुष्ट-निरीक्षणे तेजोमयं तार्तीयीकं चक्षुः?

[^63_1]: शिशुपालस्येव - पा०

**सद्-दू** — (विहस्य) तद् अपि ते चैद्यस्येव विरंस्यति।

**शङ्क** — तम् एव वेदितुम् इच्छन्न् अपि न तं पश्यामि।

**माया** — वत्स! गृहीतो ऽपि गर्वं किं न पश्यसि? अहम् एव विवेचयामि। दुरुहो ऽयम्, अस्माभिर् वेदमौळि-प्रकाशात् त्रस्त इदानीं सद्-द्रुहो भवति। सुमति-सखी सुनीतिर् एषा, या दुर्नीतिर् इति दुहित्रा मे निराकृता। अयम् एव स यामुनः, यो ऽयं मित्र-रूपो शत्रुः, अन्धकूपे जीवन्तं महा-राजं गजम् इव [[पातितवान्।|पातयति।]][^63_2] वत्स! परिशेषाद् अयम् एव स इति निश्चीयताम्।

[^63_2]: पातयति - पा०

**शङ्क** — (निर्वर्ण्य, स्वगतम्)

> अतिमानुषो ऽयम् अस्य प्रथयत्य् आकार एव महिमानम् ।  
> सलिलम् इव मेरु-सिन्धोर् निर्मलम् अन्तर्गतं महारत्नम् ॥ ६ ॥  

तद् इदम् अत्यद्भुतं ज्योतिः परैर् अनभिभवनीयम् एव। (प्रकाशम्) (सरोषम् चक्षुषी परिवृत्य) अहो! अतिचिर-प्रार्थितो महा-नागो गरुडस्य चक्षुर्-गोचरी-भवति।

**मद्-दू** — [[एवमेव|सुतर्कः]][^63_3]

[^63_3]: सुतर्कः - पा०

**माया** — (सरोषम् एनं पश्यति)

**शङ्करः** — अयम् इदानीम्,

> कल्पान्त-कन्दळित-सागर-वीचि-माला-संरम्भ-डम्बर-विडम्बिभिर् अस्मदीयैः ।  
> संक्षोभितस् सपदि यास्यति युक्ति-जालैः वातूल-धूत-नव-तूल-[[गनामवस्थाम्|गताम् अवस्थाम्]][^63_4] ॥ ७ ॥  

[^63_4]: वा लवेगहततुलगताम् - पा०

---

[[P64]]

यतिराजविजयम्-नाटकम्

**माया** — (सरोष-धैर्यम्) महा-मन्द! मदीयं पदम् अधिष्ठाय महा-राजस्य मृदु-हृदयं मोहयन्, संशमके मयि सन्नद्धे स्थिते ऽपि मति-नीति-कौशलं किं न दर्शयसि?

> परस्पर-महानक-खड्ग-संघट्ट-जृम्भितैः ।  
> स्फुलिङ्गैरस् तु खद्योतैर् विद्योतितम् इदं नभः ॥ ८ ॥  

**सद्-दू** — (सरोषम्) कामं संशसको भव। रामानुज-शिष्यः किम् अहम् अपार्थो ऽस्मि?

**यामुनः** — किं न्याय-तर्क-निपुणैः वृथा वाद-केलिः?

> अन्यान् प्रतीपयति हन्त! यतीन्द्र एषः ।  
> कण्ठीरवः पतति किं करि-यूध-योधी  
> संघे ऽपि सम्मुख-निपातिनि सैरिभाणाम् ॥ ९ ॥  

**शङ्क** — (सरोष-संरम्भम्) भो! किम् उक्तवान् असि? किम् अतः परतो ऽपि कश्चिद् अस्ति विपश्चित् तर्क-नीति-निपुणः?

> अश्रूयन्त न किं त्वया मम मुहुः पुङ्खानुपुङ्खोत्पत-  
> त्तर्क-तर्किविहार-[[भैरवरवाश्रुण्डा|भैरवरवोच्चण्डा]][^64_1] वितण्डा-जवाः ।  
> यत्-संरम्भ-निरीक्षण-क्षण-गलत्-संरन्ध-कर्णार्जुन-  
> स्पर्धा-दुर्धर-युद्ध-दुर्मद-भुज-प्रेक्षादरो नारदः ॥ १० ॥  

[^64_1]: भैरवरवोच्चण्डा - गा०

**यति** — (यामुन-मुखं पश्यन्, स्मितं करोति)

**यामु** — सर्वः स्वात्मानं श्लाघत एव।

**यति** — भगवन्! मैवं शंकरम् अवधारय। स्वात्म-निरपेक्षम् एव समयान्तर-कलहेषु अयम् अभिपतति।

**[[सदू —|सुतर्कः —]]**[^64_2] (विहस्य) तर्हि स्वव्याघातं न जानात्य् एव।

[^64_2]: सुतर्कः - पा०

**रामा** — तथा सति स्वात्मानं अरक्षन् पर-घाती [[वीर इव|वीरो ऽपि]][^64_3] नश्यति।

[^64_3]: वीरोऽपि - पा०



[[P65]]

पञ्चमोऽङ्कः

**[[सुतर्कः|सुतर्कः —]]**[^65_1] सर्वं मिथ्येति वदतः, प्रथमं स्ववचनम् एव मिथ्या स्याद् इति, परपक्षो ऽनूद्य एव विजयी-भवति।

[^65_1]: सुतर्कः - पा०

**सुनी** — व्रीहिकोशः स्वात्मानम् अदग्ध्वा किं गृहं दहति?

**माया** — (विहस्य) सर्वं खण्डयतः स्ववचनं खण्डनीयम् इति तत् परेण खण्डन-युक्तिभिर् एव खण्ड्यमानं सुतराम् अभिमतम् एव।

**सुनी** — तर्हि, विजय-फले वादे, पराजयो ऽपि फलं भक्ष्येव।

**[[सदू —|सुतर्कः —]]**[^65_6] (साट्टहासम्) युद्ध्यतो वीरस्य स्वहस्ताद् आच्छिद्य शस्त्रं तेनैव परेण स्व-शिर-च्छेदः किम् अभिमतो भवति?

[^65_6]: सुतर्कः - पा०

**शङ्क** — (विहस्य) न किंचिद् एतत्।

**राजा** — (देवीं पश्यन्) तन्तुपालः सेनापतिः सम्यग् उत्तरं दिशति।

**देवी** — आज्ञा-भङ्गो नरेन्द्राणां [[विदुषामुक्तिकूषणम्|विदुषाम् उक्ति-दूषणम्]][^65_2] ।  
पृथक्-शय्या च नारीणाम् अशस्त्र-वध उच्यते ॥ ११ ॥  

[^65_2]: अवज्ञा विदुषां तथा - पा०

**माया** — (ससंरम्भम्) भो भो [[महावावद्वेकभामानिन् !|महावादुकाभिमानिन्!]][^65_3] मयि पुरःस्थिते किं कुतर्क-विस्फुलिङ्गान् विकिरसि?

[^65_3]: महावादुकाभिमानिन् - पा०

> पादाघात-किरीट-[[धर्षण|कर्षण]][^65_4]-महा-मुष्टि-प्रहार-व्यथा-  
> [[मुद्यन्नायमुखच्युतेन|मुह्यन् वक्त्र-च्युतेन]][^65_5] रुधिरोद्वारेण शाम्यन्नपि ।  
> क्रोधाग्निर् मम दुर्मदस् तव यशः-सर्पींषि पीत्वा जग-  
> [[त्युत्सर्पन्ति|जगत्सूत्सर्पति]] यतीन्द्र-निर्भर-कथा-दर्पो ऽयम् उत्सर्पति ॥ १२ ॥  

[^65_4]: किरीटकर्षण - पा०
[^65_5]: वाक्तायः - पा०

**शङ्क** — (विहस्य) अस्तु नाम, अद्वैत-वादिनं प्रति न किंचिद् एतत्।

**[[सदू —|सुतर्कः —]]**[^65_6] रामेण रावण इव रामानुजेन जीवन्-मुक्तो ऽसि।

---

[[P66]]

यतिराजविजयम्-नाटकम्

**यति** — (ससंरम्भम्) [[वृथा वाचाटोऽकाद्वैतिन् !|वृथाकथनपौण्ड्रकाद्वैतिन्!]][^66_1] किं मां सुदर्शनं न जानासीति संनह्यति?

[^66_1]: वृथाकथनपौण्ड्रकाद्वैतिन् - पा०

**सदू** — भगवन्न् अलम् अति-संरम्भेण। [[महोरगे निपतन् गरुडः|वरहट्ट-मध्ये कथं नाम कुठार-व्यापारः]][^66_2] निपतन् गरुडः किं मण्डूके [[निपति|निपतति]]?

[^66_2]: वरहट्टमध्ये कथं नाम कुठारव्यापारः - गा०

(ससंरम्भं) परिवृत्य,

> [[यद्येको|यद्येको]][^66_3] भुवि सर्व-धुर्य-मत-द्वैतण्डिकस् त्वद्-विरां  
> गर्वं [[खण्डयितुं|खण्डयिता]][^66_4] यतीश्वर-चमू-नासीर-धूली-लवः ।  
> सक्रुद्धो ऽहम् अवस्थितो ऽस्मि शतशस् तर्कासि-धारा-हति-  
> क्रीडा-खण्डित-चण्ड-[[हैतुककथा|चण्डवादुककथा]][^66_5]-कण्डूल-जिह्वालतस् ॥ १३ ॥  

[^66_3]: त्रैको - पा०
[^66_4]: खण्डयिता - पा०
[^66_5]: चण्डवादुककथा - पा०

**शङ्क** — साधु, वटो! साधु। लघुरपि विस्फुलिङ्ग इव दीप्तो ऽसि।  
त्वया सह त्वदाचार्यं मदुक्तिः खण्डयिष्यति ।  
कञ्चुके पातितः खड्गः न स्पृशेत् किं कलेवरम् ॥  

تथापि, मत्त-गजम् एव लक्ष्यी-कुर्वन् मृगपतिः [[महिषे|मार्जारे]][^66_6] किं निपतति? (समन्ताद् अवलोक्य,)  
मदुक्ति-बाण-निर्भिन्नं दृष्ट्वा रामानुजं नराः ।  
द्विनेत्रम् अपि मां प्राहुः त्रिनेत्रं भुवि शङ्करम् ॥  

[^66_6]: मार्जारे - पा०

**सदू** — (साट्टहासम्) संरम्भाकुलितेन भवता विपरीतम् अभिधीयते।  

> [[स्वेाक्तिसुस्थिरबाणोऽपि त्रिणेलो|स्वोक्ति-सुस्थिर-बाणो ऽपि त्रिणेत्रो]][^66_7] युधि शङ्करः ।  
> रामानुजेन बलिना जितो दृष्टो हि नान्यथा ॥  

[^66_7]: सपक्षेणैव बाणेन शायितो युधि शङ्करः - पा०

---

[[P67]]

पञ्चमोऽङ्कः

**शङ्क** — दुर्विद्वग्ध! कचाट! वटो! किं विकत्थसे। (सक्रोध-संरम्भम्) सर्वे ऽपि मां पश्यन्तु।

> ब्रह्मणः [[कति|कति नाम]][^67_1] वा न सन्ति जगती-निर्माण-नैपुणी-  
> पारीणाः परमाणवो ऽपि कति वा लोकत्रयारम्भकाः ।  
> तत्तत्-तत्त्व-शिखण्डिषा परिपतन्-मदुक्ति-[[कालानलै|कालानलै-]][^67_2]  
> ज्वाला-तत्क्षण-भक्षितस्य जगतो भस्मापि न स्मर्यते ॥ १४ ॥  

[^67_1]: कति नाम सन्ति - पा०
[^67_2]: मधुविध्वानलज्वला - पा०

**सुनी** — (कर्णौ पिधाय) दुस्सहान्य् अमूनि वाक्यानि, स्फुलिङ्गम् अभिवर्षन्ति।

**रामा** — (विहस्य) वाङ्-मात्रेणापि वराकस् तुष्यतु।

**सदू** — (सक्रोधं पश्यन्) मयि स्थिते ऽपि महापुरुष-सन्निधौ किं प्रलपसि?

**माया** — (ससंरम्भम्)

> ब्रह्मास्त्रम् एकम् आदाय समितौ विहरन्नहम् ।  
> खण्डयामि जगत् सर्वं पाण्डित्यं मम दृश्यताम् ॥  
> यस्मिन् ध्वस्तम् एतत् त्रिभुवनम् अखिलं यच्च पश्यत्य् अविद्या-  
> मुग्धं स्वाध्यस्तम् एतद् दिवि निज-वपुर्-वीक्षणे मुच्यते यत् ।  
> ज्ञानं ज्ञेयादि-हीनं भवति यद् अपदं संविदां निर्विशेषं  
> सत्यं तद् ब्रह्म मिथ्या, तद्-इतरद्-अखिलं को ऽन्यथा वक्तुम् ईशः ॥ १५ ॥  

(इति भुजम् आस्फोटयति)

**यति** — (सस्मितं सदू-मुखं पश्यन्)

**सदू** — (ससंरम्भं भुजम् आस्फोटयन्,) अहम् ईशो ऽस्मि। आकार-भेद-सम्पादकम् एतद्-अखिलं निर्विशेष-वस्तु-वादिनस् ते न सम्भवति।

**सुम** — (सहर्षम्)

> सम्यग् एकोत्तरेणैव परार्थान् अच्छिनत् सुधीः ।  
> प्रत्येकं शाल-भेदाय रामस् तद् दधे शरान् ॥ १६ ॥  

---

[[P68]]

यतिराजविजयम्-नाटकम्

**माया** — (विहस्य) किम् अत्रानुपपन्नम्। अस्ति खल्व् अस्माकम् अविद्या-कामधेनुः।

**सदू** — (विहस्य) कष्टं भोः,

> आरोपयितुम् एवास्य धर्मान् बत निराकरोः ।  
> ब्रह्मणि ज्ञान-शक्त्यादि-गुणान् स्वाभाविकान् अपि ॥ १७ ॥  

किञ्च,

> नाध्यासः स्वप्रकाशे तिमिरमिव रवौ ज्ञान-बाध्या च माया  
> न ब्रह्म-ज्ञान-रूपं स्थगयति न ततो बन्ध-मोक्षौ च तस्य ।  
> न ज्ञानं ज्ञेय-हीनं न सद्-अमति-पदं निर्विशेषं न किञ्चित्  
> सत्यं [[स्यान्मानसिद्धं|संज्ञामात्रसिद्धम्]][^68_1] जगद् अपि न यदि स्वोक्ति-बाधादयस् स्युः ॥ १८ ॥  

[^68_1]: संज्ञामात्रसिद्धम् - गा०

किञ्च,

> प्रत्यक्ष-प्रभृति-प्रमाण-विदितं सत्यं च भिन्नं जगत्  
> बाधस्तस्य न केनचित् स्व-विहतैर् ब्रह्मात्मकं तद् जगत् ।  
> द्वैताद्वैत-गिरो विभिन्न-विषया बाधाय नालं मिथः  
> पश्वालम्भ-निषेध-वाक्यवद् अतो विश्वापलापः कुतः ॥ १९ ॥  

**रा** — (सुनीति-मुखं पश्यति)।

**सुनी** — सत्सु पदेषु सम्यग् [[सम्यगुन्तोतो दोषः|उन्नीतो दोषः]][^68_2]।

[^68_2]: अपार्थ - पा०

**सुम** — (विहस्य) मायावाद-[[सातपद्दीनमपि|साम्राज्य-पीठम् अपि]] [[समासमेतेन|समाप्तम् एतेन]] देवस्य।

**माया** — ([[जनान्तिकम्|अपवार्य]][^68_3]) अयि वत्स, दुरात्मा सम्यग् उत्तरं [[ददाति|दिशति]][^68_4], न हि विधि-बाधो निषेधेन?

[^68_3]: अपवार्य - पा०
[^68_4]: दिशति -- गा०

**शङ्क** — (सविषादम्) किं कुर्मः; संप्रति धार्ष्ट्यम् एव नस् शरणम् अस्तु, जातयः प्रयुज्यन्ताम्।

---

[[P69]]

पञ्चमोऽङ्कः

**तन्तुपालः** — (निरूप्य) भवद्-अभिमतं जानामि। माधव-समये किं जाति-च्छद्म-जल्पः परिस्फुरति? निपुण-मति-निरूपणीयम् एतत् तिष्ठतु।

> इदम् इत्थम् इति ज्ञेयं निर्विशेषम् इति ब्रुवन् ।  
> माता बन्ध्या ममेत्युक्ता हन्त लज्जेत किं भवान् ॥ २० ॥  

(नेपथ्ये)

रे रे! कः पुनर् एवम् अस्मत्-सुहृदम् आस्कन्दति, सानुबन्धम् एव वेदमौळि बन्दीग्राहं ग्रहीतुम् आगतो ऽस्मि।

**शङ्क** — (श्रुत्वा, सहर्षं निष्क्रम्य, पुनः प्रविशति)

**माया** — किम् एतत्?

**शङ्क** — मिथ्यादृष्टि-प्रोत्साहितो योगाचारः अस्मत्-प्रिय-चिकीर्षया राज-द्वारं निरुणाद्धि।

**सुम** — (भयाकुला भर्तारम् आलिङ्गति)

**राजा** — (सधैर्यम्) अयि प्रिये! किम् आकुलासि?

> विरमतु तव भीतिर् वेपमाना ऽसि किं त्वं?  
> [[विमतवदनवाभिः|विमत-वदन-दाग्निः]] वेदमौळिः किलाहम् ।  
> सुमतिर् असि, सुनीतिस् त्वत्-सखी, तत्-समेता  
> विहर, सति यतीन्द्रे विद्यते किं भयं ते? ॥ २१ ॥  

(प्रविश्य प्रतीहारी)

**प्रती** — (साञ्जलिबन्धम्) देव! परकाल-शराङ्कुशादयः साभिसरा द्वारि तिष्ठन्ति।

**यति** — पराङ्कुशः प्रविशतु परकालादिभिः; परे निरस्यन्ताम्।

**प्रती** — यद् आज्ञापयन्ति गुरवः। (इति निष्क्रान्ता)

(ततः प्रविशति पराङ्कुशः। सर्वे यथोचितम् उपविशन्ति।)

**यति** — (सहर्षम्)

> शठकोप-मुनिस् स एष साक्षात् पुरुषं पश्यति पुण्डरीक-नेत्रम् ।  
> अनपेक्षित-वर्ण-भेदम् अस्मात् अवतेरुस् स्वयम् आगम-साराः ॥ २२ ॥  



[[P70]]

यतिराजविजयम्-नाटकम्

**पराङ्कुशः** — देव! सपरिवारो विजयस्व।

**राजा** — (सादरं पश्यति)

**परा** — (परिवृत्य सामर्षम्, मायावादं प्रति राजानम् अङ्गुल्या निर्दिशन्)

> दृश्यं निन्दति दर्शयन्न् अपि परं ज्योतिर् जगत्-कारणम्  
> मोक्षोपायम् उदीरयन्न् अपि मृषा संसार-मोक्षाव् इति ।  
> ब्रूते भेद-परायणो ऽपि तमपि द्वेष्टि त्वदायत्तधीः  
> (विहस्य) किम् अतः परं कौटिल्यं दौष्कुल्यम्;  
> मायावाद! वदत्य् अलीकम् इति च [[प्रत्यायितोऽयं|प्रख्यापितो ऽयम्]][^70_1] त्वया ॥ २३ ॥  

[^70_1]: प्रख्यापितोऽयम् - पा०

तद् एवं लवणाकर इव कर्पूरं सर्व-जगत्-प्रमाण-भूतं राजानम् अध्याकुर्वन् किं फलं प्राप्नोषि?

**सुतर्कः** — (सोल्लुण्ठम्) सामन्त-भद्र-पीठं प्राप्तम्।

**सुनी** — तथागतो ऽयं सर्वार्थसिद्ध एव।

**माया** — (विमृश्य, सक्रोधा) किम् अहम् सुगत एष?

**सुनी** — (विहस्य) दुर्गतश् च।

**सुत** — सर्वज्ञस् त्वम् एव तन् निरूपय।

**शङ्क** — भगवन्! विरम्यताम्। अतिप्रसङ्गस् तिष्ठतु।

**सुनी** — (विहस्य) एवम् अनामन्त्रयन् शङ्करः कथं सर्वज्ञः स्यात्।

**यामु** — कामम् अन्यथा करोतु।

> मन्त्रिषु न्यस्त-भारो ऽयं न तद्-दोषेण दुष्यति ।  
> स्फातिकः किं प्रदुष्येत वर्ण-भेदैर् उपाधिजैः ॥ २४ ॥  

**यति** — भगवन् पराङ्कुश! निरङ्कुश-वृत्तयो ऽमी निरस्यन्ताम्।

**परा** — कः पुनर् एतयोर् दण्डः?

---

[[P71]]

पञ्चमोऽङ्कः

**यति** — [[शिखोपवीतच्छेदो|शिखोपवीतत्यागो]][^71_1] हि दण्डो दुष्ट-द्विजन्मनाम्।  
[[स तु प्रागेव देवेन|कृतः प्रागेव]][^71_2] द्वयोर् वित्त-मुषोर् अभूत्॥  

[^71_1]: शिखोपवीतत्यागो हि - पा०
[^71_2]: कृतः प्रागेव - पा०

पश्चाद् अपि एवंविधान् यतीन् इन्द्रस् शालावकेभ्यः प्रयच्छति।

**शङ्क** — भगवन् पराङ्कुश! महाद्वैत-पातिन् विष्णु-भक्तो ऽसि; सो ऽहं भावनातिशयेन जीवन्-मुक्तो मुकुन्द एव; मयि न पापं कर्तुम् अर्हसि।

**सदू** — (विहस्य)

> सो ऽहम्-भावनया सुरासुर-शिरः-कोटीर-कोटी-लस-  
> रत्नालोक-विलोकनीय-चरण-द्वन्द्वो मुकुन्दो भवान् ।  
> केनादर्शि,  

**सुनी** — किम् आत्मनैव ददृशे,

**सदू** — तद् ब्रूहि सत्यं स्वराट्  
किं मुष्टेः किमु दुह्यति (विहस्य)  
स्फुटम् अहो को ऽप्य् एष केलिक्रमः ॥  

**परा** — (सरोषम्) स्वस्वामि-तादात्म्य-भावना-पातकिन्! किं पौण्ड्रक-वृत्तान्तं न शृणोषि?

> वासुदेवो ऽहम् एवेति पौण्ड्रक-वत् त्वम् अपि ब्रुवन् ।  
> सुदर्शनेन दुर्दर्शः क्रियसे जितकाशिना ॥ २५ ॥  

(नेपथ्ये)

मयि तिष्ठति को वा विज्ञानवादिनम् अधिक्षिपति?  
चिन्मात्रम् आवयोस् तत्त्वं मिथ्यैवाऽऽविद्यकं जगत् ।  
तत् तु मित्रस्य मे नित्यं चिन्मात्रं क्षणिकं मम ॥  

---

[[P72]]

यतिराजविजयम्-नाटकम्

यद्वा, निर्विशेषाभिमानी नित्यत्वादि-धर्मं कथं ब्रूयात्?

(पुनर् नेपथ्ये)

> यद् वैभाषिक-भाषितं यद् अपि वा सौत्रान्तिकैस् सूत्रितं  
> योगाचार-विचारणा च सरणिः सिद्धान्त-सौधस्य नः ।  
> तद् अज्ञानं च मृषैव विश्ववद् इति व्यक्तं ब्रुवन् निर्भयो  
> मत्-पार्श्वे भव नान्न्याथा तव गतिर् [[र्विश्वापलापार्थिनः|र्विश्वापलापार्थिनः]][^72_1] ॥ २६ ॥  

[^72_1]: दृश्यापलापार्थिनः - गा०

**सुत** — (श्रुत्वा सक्रोधा) किं युवां योगाचार-माध्यमिकौ? रक्षतम् आत्मानं द्वयोर् अयम् एको रामशरः।  

> स्वस्वामि-विरोधस् तस्या चेत् सर्वं शून्यं मृषेति वाक् ।  
> सर्वं जीवित-सत्या चेत् मृषा-सर्पे ऽस्ति किं विषम् ॥  

**सुनी** — (साकूतं मायावाद-मुखम् अवलोक्य) वृश्चिक-घातेन विष-धरो ऽपि हतः।

**माया** — (सलज्जम् [[मवाङ्मुखस्तिष्ठति|अधोमुखस् तिष्ठति]][^72_2])

[^72_2]: अधोमुखः - पा०

**परा** — (सरोषम्) किं युवां बौद्धस्य सुहृदौ। (इति दण्डं गृह्णाति)

(उभौ — सभयं निष्क्रान्तौ)

**सुम** — अद्याहम् आश्वास्ता ऽस्मि, यद् आभ्यां सह महा-राक्षसी मिथ्यादृष्टिर् अपयातीति।

**सुत** — अत्र लब्धासिके सति रामानुजे, माया-विलासिनी कथम् आस्तिका न स्यात्?

**सुनी** — न हि रजनी-विरामे तिमिर-वलिस् तिष्ठति।

**राजा** — नष्टे ऽपि सर्पे सर्प-भयम् अनुवर्तत एव।

**यति** — (यामुनं पश्यन्) आर्य! किंचिद् विशेषस् तिष्ठत्य् एव।

(ततः प्रविशति यादवो [[दण्डकमण्डलुधारी|कमण्डलुबाहः]][^72_3] पुस्तक-वाचक-शिष्यश् च)

[^72_3]: कमण्डलुबाहः पुस्तक - गा०

---

[[P73]]

पञ्चमोऽङ्कः

**याद्** —

> तर्क-न्याय-तरङ्गळित-जगद्-दुर्वादि-गर्वानलः  
> सर्वाम्नाय-तदङ्ग-मङ्गल-महामाणिक्य-दीपाङ्कुरः ।  
> मादृक्षो यदि कश्चिदस्ति सचिवः श्रीवेदमौळेर् अयम्  
> प्रत्युद्गच्छतु तन्-मदं शमयितुं प्राप्तो यतिर् यादवः ॥ २७ ॥  

(सर्वे सादरं पश्यन्ति)

**याद्** — वत्स, वादिसिंह! पठ्यतां वेदान्त-विषय-संग्रह-श्लोकः।

**शिष्यः** —  
> ब्रह्मैकं तत्त्वम् एतद् बहुविध-चिद्-अचिच्-चित्त-नियन्तृ-प्रभेदात्  
> तत्तच्-शक्ति-स्वरूपं परिणमति यथा वारि-फेनादि-रूपम् ।  
> [[सत्त्वं|तत्त्वं]][^73_1] सर्वानुवृत्तं मणिषु परिमल-न्यायतो ऽचित्-पदार्थे  
> चैतन्यं स्वप्रकाशं श्रुतिरिह विषये स्थापिता यादवेन ॥  

[^73_1]: तत्त्वम् - पा०

**याद्** — अस्यायम् अर्थः—सच्चिदानन्दमयं ब्रह्मैव तत्त्वम्; तच्च तत्तच्-शक्ति-मय-भोक्तृ-भोग्य-नियन्तृ-रूपेण परिणमति; यथा फेन-बुद्बुद-तरङ्ग-रूपेण वारि; कारण-भूतं ब्रह्म, गुणः चैतन्यं रत्न-गन्ध-न्यायेन क्वचिद् अचिद्-वस्तुनि विद्यमानम् अपि न प्रकाशते; कारणात्मना सर्वम् अभिन्नम्, कार्यात्मना च सर्वं भिन्नम्, यथा घट-शरावादि। भेदाभेद-श्रुतयश् च अस्मिन्न् अर्थे व्यवस्थाप्यन्ते।

**सदू** — (विहस्य साट्टहासम्) किम् एवं महा-राज-विषयं, मन्त्रीश्वर! विप्लवयसि।  
निर्विकार-श्रुतेर् ब्रह्म सविकारं न मृष्यति ।  
जीव-नित्यत्व-वादो ऽपि तन्-मत्यैव प्रकुप्यति ॥  

एवम् अन्यान् अप्य् अर्थान् उन्मूलयन् महा-राज-समीपे न स्थातुम् अर्हसि।

**याद्** — (सुनीति-मुखं परामृशन् अधोमुखस् तिष्ठति)

**परा** — देव! राज-द्रोहे महति कः दण्डः?

**राजा** — (स्मितं कृत्वा) यति-दण्डं यतिराज एव जानाति।

**यति** — (यामुनं पश्यन्)

---

[[P74]]

यतिराजविजयम्-नाटकम्

**यामु** — शम-दमाद्यात्म-गुणोपेतस्य् अपि दुष्टस्य परिव्राजो देशाद् विवासम् अन्तरेण नान्यो दण्डः।

**याद्** — (सप्रश्रयम्) देव-पाद-सेवा-परित्यागात् प्राण-परित्याग एव सुलभ इव प्रतिभाति।

**राजा** — तर्हि रामानुजस् ते शरणम् अस्तु।

**याद्** — (यतिराजस्य पादयोः पतति)

**यति** — (समन्ताद् अवलोक्य)

> सदोषो वा ऽप्य् अदोषो वा मामेष शरणं गतः ।  
> भवद्भिर् भव्य-हृदयैर् अयम् अद्भिर् अनुगृह्यताम् ॥ २८ ॥  

**राजा** — (सहर्षम्) न केवलम् एष एव; कृत-सकल-किल्बिषो ऽपि यो भवद्-अभिमान-विषयः, सो ऽसद्-विषय-वासिभिस् सर्वैः शिरसा माल्य-वद् धार्यताम्।

**यामु** — तथैवास्तु। (आकाशे पुष्पवृष्टिः, दुन्दुभि-ध्वनश् च)

**यति** — महान् अयं प्रसादो देवस्य।

**परा** — भो मस्करिन्! भगवद्-रामानुज-परिग्रहेणैव परां कोटिम् आरूढो ऽसि, तद् गम्यतां नियम-निर्वर्तनाय।

**याद्** — (शिष्येण सह निष्क्रान्तः)

(ततः प्रविशति भास्करः, शिष्याश् च)

**भास्कर** — (सहर्षम्) मायावादे निरस्ते, ममैतद् राज-कुलम्; रामानुजस् तु मत्समान-धर्मा मयि नात्यन्तम् अपराध्नोति।

**सुनी** — (पुरो ऽवलोक्य)

> यज्ञोपवीती काषायी त्रिदण्डाजिनवान् शिखी ।  
> सशिष्यासनमुत्पाद्यैः शिष्यैर् अभ्येति मस्करी ॥ २९ ॥  

**राजा** — (विमृश्य) देवि! किम् एनं प्रत्यभिजानासि?



[[P75]]

पञ्चमोऽङ्कः

**सुम** — (विलोक्य) कतिपय-दिवसान्तरित-दर्शनो [[मध्यममात्य|मध्यमामात्य]] एषः। (विहस्य)  
हला! सुनीते किम् एतद् ब्रवीमि। [[अयमनेनेन|अयम् अनेन]] वेषेण खलु मिथ्यादृष्टेर् दौत्यम् अनुष्ठितवान्।

**भास्कर** — जयतु देवः; किं [[मामेवमवजानासि ?|माम् एवम् अवजानासि?]] किंचिद् [[किंचिद्दर्स्मिन्|अस्मिन्]] जने क्रियतां प्रसादः।  
द्वे चक्षुषी, द्वे च पदे; एवम् एव मन्त्रिणौ च द्वाव् अपेक्षणीयौ; तद् अहम् अपि रामानुजस्य द्वितीयो भवामि ॥  

**सुनी** — भास्करम् अपि तमः प्रविशति।  

> [[प्रमाणेष्विव|प्रमाणेष्व् एव]][^75_1] वेदान्तः प्रमेयेषु परः पुमान् ।  
> प्रमातृषु यतीन्द्रो ऽयं न द्वितीयम् अपेक्षते ॥ ३० ॥  

[^75_1]: प्रमाणेष्वेव - पा०

**सेना** — को दोषः, अनेन जानीमस् ते नीति-पेशलताम्; कथं त्वया विचिन्तितो महा-राज-विषयः।

**भास्कर** —

> ब्रह्मैकं सद्-उपाधि-भेद-भिदुरं जीवत्वम् अभ्येति तत्  
> जीवत्वे च विपतयो ऽनुपहितं ब्रह्मैव शान्तं शिवम् ।  
> ब्रह्मैव खलु मुक्तिर् एतद् अखिलोपाधिक्षये देहिनां  
> कर्म-ज्ञान-समुच्चयाद् अयम् इति लक्ष्यन्तराख्य-स्थितिः ॥ ३१ ॥  

**सुम** — (सुनीति-मुखं पश्यन्ती मुखम् अन्यतः करोति)

**सदू** — (विमृश्य, सक्रोधम्)  

> बहुधा [[जीवरूपेण|जीवभेदेन]][^75_2] दुष्यतीति परः पुमान् ।  
> जल्पन्ती तव जिह्वेयं शतधा किं न शीर्यते? ॥ ३२ ॥  

[^75_2]: जीवभेदेन - पा०

**परा** — अरे! भगवद्-द्रोह-वादिनस् ते जिह्वा-च्छेदो न दोषाय। (इति पार्श्वम् अवलोकयति)

(प्रविश्य दिव्यपुरुषः)

**दिव्यपुरुषः** — को ऽसौ दुरात्मा भगवद्-द्रोहम् आचरति। (इति कृपाणम् आकर्षति)

---

[[P76]]

यतिराजविजयम्-नाटकम्

**भास्कर** — (विलोक्य) हा कष्टम्! (इति निष्क्रामति)

**दिव्यपुरुष** — (कृपाणं धून्वन्न् अनुधावति)

**परा** — भद्र, निवर्तस्व; अलम् एतावता निर्भर्त्सनेन।

**दिव्यपुरुष** — तथा। (इति प्रतिनिवृत्य, निष्क्रान्तः)

**सुनी** — (विहस्य) देवि! प्रमाणम् अनङ्गी-कुर्वतां कृपाण एवोत्तरम्।

**सुम** — एवम् अजानती कथं सुनीतिर् असि।

**यति** — (विलोक्य)  

> मस्करीव नभः-स्थायी बिभ्राणो रक्तम् अंशुकम् ।  
> तेजसा हीयमानो ऽयं [[तिरोधत्ते|तिरोभवति]][^76_1] हि भास्करः ॥ ३३ ॥  

[^76_1]: तिरोभवति - गा०

**राजा** — (सुमतिं हस्ते गृहीत्वा)  

> निधाय सर्वकष-नीति-मार्गे रामानुजे मन्त्रिणि राज्य-भारम् ।  
> सुनीतमत्या सुमत्या त्वया ऽहं क्रीडामि कृत्स्नैर् विषयैः प्रहृष्यन् ॥ ३४ ॥  

(इति हर्षं नाटयन्तो निष्क्रान्तास् सर्वे)

इति श्री घटिकाशत - श्रीमद्-वरदाचार्य-विरचिते वेदान्त-विलासापरनाम्नि यतिराज-विजये पञ्चमो ऽङ्कः।

---

[[P77]]

अथ षष्ठोऽङ्कः

(ततः प्रविशति यतिराजः, शिष्यश् च)

**यति** — (विचिन्त्य) वत्स! सर्वे ऽन्ये तिष्ठन्तु।  

> [[निरालम्बन' म्येतदेवं|निरालम्बनम् एवैतत्]][^77_1] साधयतो मतम् ।  
> शङ्करस्य तु लीलेयं गगने चित्र-लेखनम् ॥ १ ॥  

[^77_1]: निरालम्बनमेवैतत् - पा०

(प्रविश्य शङ्करः)

**शङ्क** — साधु यतिराज, सम्यग् दृष्टवान् असि।  

> [[मद्गोपाटदर्शनाय|बुद्धेः पाट-प्रदर्शनाय]][^77_2] विदधे तत्त्व-स्थितेर् अन्यथा  
> मिथ्या-मेयम् अमेयम् एव सद् इति प्रस्थानम् अन्यन् मया ।  
> (विहस्य)  
> पश्यंस् तत्त्वम् इदं च [[मुञ्चति|मुह्यति जनः]][^77_3] बत प्राज्ञो ऽसि किन्त्व् अद्भुतं  
> नान्यो वेत्ति नभः-स्थले [[विलिखतः|विलिखतश्]] चित्राणि मे कौशलम् ॥ २ ॥  

[^77_2]: बुद्धेः पाटप्रदर्शनाय - पा०
[^77_3]: मुह्यति जनः - पा०

**यति** — सम्यग् आह भवान्।  

> द्रष्टा [[यदाऽवमन्येत|यदा चेन्मन्येत]][^77_4] [[गगने पङ्कजोद्भवम्|पाषाणे पङ्कजोद्भवम्]][^77_5] ।  
> तदा दर्शयितुर् नष्टं कुहना-शिल्प-कौशलम् ॥ ३ ॥  

[^77_4]: द्रष्टा यदा चेन्मन्येत - पा०
[^77_5]: पाषाणे पङ्कजोद्भवम् - पा०

**शङ्क** — अहं तु पर्यङ्क-विद्याम् उपासितुम् अन्तःपुरं गच्छामि।

(इति निष्क्रान्तः)

---

[[P78]]

यतिराजविजयम्-नाटकम्

**यति** — (विहस्य) [[लोकस्स्वेतन|लोकस् स्वेन न]] जानाति। केवलं गतानुगतिक एवान्धकूपे निपतति।

**सुतर्कः** — (विमृश्य)  

> हा कष्टं किम् अनेन चेष्टितम् अभूद् अस्मद्-दृशाम् अग्रणीः  
> किं वा बुद्ध-सुबुद्धिर् अपि वृथाआचारो विचारोज्झितः ।  
> सर्वज्ञो ऽपि शताध्वरो ऽपि कुहना-शास्त्रान्धकूपे [[नरान्|जनान्]][^78_1]  
> अन्धान् एवम् अहो! निपात्य नरकावर्ते न वर्तेत कः? ॥ ४ ॥  

[^78_1]: जनान् - पा०

**यति** — कस् तन् न जानाति। सर्वो ऽपि स्वधी-सामर्थ्यम् एव दर्शयति। एवम् अनात्मज्ञैर् अन्यैश् च मन्त्रिभिर् एक-शरीरयोर् अपि महा-राज-वेद-विचारयोर् अन्योन्य-विरोध उत्पादितः; तत्-प्रशमनाय वेद-विचारम् आनेतुं पञ्चमो वेदः पुराण-सहितः प्रहितः; तन् मया महा-राज-समीपे स्थातव्यम्; तद् भवता यामुनादीन् पुरस्कृत्य माधवोत्सवः कार्यः॥ (इति निष्क्रान्ताौ)

(इति विष्कम्भः)

(ततः प्रविशति सुनीति-सहितो राजा, परिजन-परिच्छन्ना देवी, यतिराजश् च)

**यति** — (शुभ-निमित्तं वीक्ष्य, दक्षिणतो दर्शयन्, सहर्षम्)  

> शुकासित-भरद्वाज-हारीतास् तत्-पथे स्थिताः ।  
> कृष्ण-पक्षाः [[कृतालापा|कृतोद्योगाः]][^78_3] द्विजा मे दर्शन-प्रियाः ॥ ५ ॥  

[^78_3]: कृतोद्योगाः - पा०

**राजा** — (विमृश्य, स्मितं कृत्वा) महर्षि-प्रियम् एव यतिराज-दर्शनम्।

**सुनी** — सम्यग् उक्तं देवेन।  

> वेदेष्व् अर्थ-निधानानि दृश्यन्ते न हि सन्त्यपि ।  
> तन् न यत्नेन दृश्येत [[तत्त|तत् तु]] तस्यैव दर्शनम् ॥ ६ ॥  

---

[[P79]]

षष्ठोऽङ्कः

**यति** — (सपरितोषम्) सर्वम् इदं महा-राज-प्रसाद एव; शुभ-निमित्त-पक्षिसंचार-वचनम् एव इदं परिणमयति। (सबहुमानं) राजन्! [[इदमासनमध्यास्यताम्|इदं सिंहासनम् अध्यास्यताम्]][^79_2]।

[^79_2]: सिंहासनम् - पा०

**राजा** — (उपविशति)

**सुनी** — आर्य! भवता ऽपि यथासनम् उपविश्यताम्। (इति चामर-हस्ता राज-पार्श्वे तिष्ठति)

**राजा** — (पार्श्वतो ऽवलोक्य, स्मितं कृत्वा) सुनीतिर् एव राज्ञां महा-राज-शब्दं स्थापयति।

**यति** — सम्यग् उक्तं देवेन।  

> काले वर्षति वासवः, कलि-कथा न का ऽपि, वर्णाश्रमाः  
> वेलां देव न लङ्घयन्ति, न मिथो वैरं क्वचित् [[प्राणिषु|प्राणिनाम्]][^79_3] ।  
> सूते सर्व-फलं मही, सुकृतिनस् सर्वे ऽपि संविन्मये  
> न्यस्यन्त्य् आत्म-भरं मुर-द्विषि, महानीतिज्ञ-राज्ञि त्वयि ॥ ७ ॥  

[^79_3]: प्राणिनाम् - पा०

**राजा** — त्वयि मन्त्रिणि किं न सम्पद्यते ललितस्य।

**सुनी** — [[सूत्रनुमुक्तं|सुष्ठूक्तं]] देवेन।  

> स्व-स्वार्थ-क्षतिर् इह न क्वचिच् छ्रुतीनां  
> प्रत्यक्ष-प्रभृतिर् अपि [[प्रमाणवर्गः|इह]][^79_4] ।  
> स्वार्थेषु प्रभवति निस्सपत्न-चारी  
> राजंस् ते वहति धुरं यतीश्वरे ऽस्मिन् ॥ ८ ॥  

[^79_4]: इह - पा०

(प्रविश्य कञ्चुकी)

**कञ्चु** — देव, पञ्चमं वेदं पुरस्कृत्य वेद-विचारो द्वारि तिष्ठति।

**राजा** — (अश्रावणं नाटयति)
