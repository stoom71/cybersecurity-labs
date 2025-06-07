# 🕵️ Challenge Walkthrough: nothinginterestinghere.001

## 🧰 Tools Used

* `strings`
* `grep`
* `base64`

---

## 🔍 Step-by-Step Breakdown

### 1. Extract strings from the file

Use `strings` to pull readable ASCII text from the binary:

```bash
strings nothinginterestinghere.001
```

This dumps all human-readable sequences from the file.

---

### 2. Filter potential Base64 strings (20+ characters)

We're looking for anything that *could* be base64 encoded. To catch them:

```bash
strings nothinginterestinghere.001 | grep -E '^[A-Za-z0-9+/=]{20,}$'
```

✅ This filters lines that:

* Only contain base64 characters
* Are 20+ characters long (common base64 length for encoded data)

---

### 3. Decode the base64 string

Found this encoded string:

```text
U1ZCUkd7ZDNsMzczZF9uMDdfZjByNjA3NzNuXzI4MzAyOTM4Mn0=
```

Decode it with:

```bash
echo 'U1ZCUkd7ZDNsMzczZF9uMDdfZjByNjA3NzNuXzI4MzAyOTM4Mn0=' | base64 -d
```

---

### 🎯 Flag

```text
SVBRG{d3l373d_n07_f0r60773n_283029382}
```

---


---



