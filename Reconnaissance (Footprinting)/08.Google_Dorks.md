
# 🔍 Google Dorks Cheat Sheet  
**Google Hacking Made Easy**  
📎 [pentest-tools.com - Google Hacking](https://pentest-tools.com/information-gathering/google-hacking#)

---

## 📁 Search for Documents on Popular Cloud Platforms

Use the following dorks to search public files on cloud services:

```
site:drive.google.com <searchterm>
site:dl.dropbox.com <searchterm>
site:s3.amazonaws.com <searchterm>
site:onedrive.live.com <searchterm>
site:cryptome.org <searchterm>
```

---

## 🔐 Find Admin Credentials in Public Files

Look for text files containing sensitive credentials:

```
intext:company_keyword 
  (ext:txt | ext:sql | ext:cnf | ext:config | ext:log) 
  AND (intext:"admin" | intext:"root" | intext:"administrator") 
  AND (intext:"password")
```

---

## 🌐 Discover Subdomains Indexed by Other Services

Check public domain registries:

```
site:bgp.he.net inurl:ndd
site:dnslookup.fr inurl:ndd
```

---

## 🏢 Internal Organization Info

Useful for corporate recon:

```
site:cadres.apec.fr direction <CompanyName>
```

---

## 💼 Financial Reports (Often in PDF)

```
"périmètre de consolisation" 
| "rapport de référence" 
| "rapport annuel" 
filetype:pdf
```

---

## ⚠️ Don't Miss Deeper Subdomains

If you’re using:

```
site:*.example.com
```

Also check:

```
site:*.*.example.com
site:*.*.*.example.com
```

---

## 😂 Funny or Interesting Google Dorks (e.g., Public Trello Boards)

```
site:trello.com inurl:/b/
site:trello.com password admin OR username
```

---

## 🕵️ Recon for Sensitive Data (Code, Notes, Paste Sites)

Search on public dev and note-sharing sites:

```
site:ideone.com 
| site:codebeautify.org 
| site:codeshare.io 
| site:codepen.io 
| site:repl.it 
| site:justpaste.it 
| site:pastebin.com 
| site:jsfiddle.net 
| site:trello.com 
"$TARGET"
```

---

## 📊 Piwik Anonymous Access

```
inurl:token_auth inurl:anonymous
```

---

# 🛠️ Automated Google Dork Tools

## 1. GoogD0rker  
🔗 [GoogD0rker GitHub](https://github.com/ZephrFish/GoogD0rker)  
Command:
```bash
./googD0rker-txt.py -d example.com
```

---

## 2. Goohak  
🔗 [Goohak GitHub](https://github.com/1N3/Goohak)  
Command:
```bash
./goohak domain.com
```

---

## 3. Pagodo  
🔗 Tool to gather dorks and find vulnerable pages

**Step 1 – Scrape dorks from GHDB:**
```bash
python3 ghdb_scraper.py -j -s
```

**Step 2 – Use scraped dorks on a target domain:**
```bash
python3 pagodo.py -d example.com -g dorks.txt -l 50 -s -e 35.0 -j 1.1
```
