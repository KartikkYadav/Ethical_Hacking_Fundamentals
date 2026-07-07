# Active Subdomain Enumeration

## Active Subdomain Enumeration

**Active Subdomain Enumeration** involves directly querying external sources such as DNS servers, web services, or performing HTTP(S) probes to identify **live and resolvable subdomains** of a target. Unlike passive enumeration, this method interacts with the network and can detect subdomains that are currently active.

---

## Key Characteristics

* Sends DNS queries or HTTP requests
* May identify subdomains not found in passive sources
* Riskier (more detectable) than passive methods
* Helps validate which subdomains are **actually live**

---

## Common Techniques

* **DNS resolution** of a wordlist against the target domain
* **HTTP probing** to check if subdomains are serving content
* **Wildcard filtering** to eliminate false positives

---

## Popular Tools for Active Subdomain Enumeration

### 1. dnsx (by ProjectDiscovery)

A fast and multi-purpose DNS toolkit that resolves subdomains.

#### Installation

```bash
go install -v github.com/projectdiscovery/dnsx/cmd/dnsx@latest
```

#### Usage

```bash
cat subdomains.txt | dnsx -silent -a -resp -o alive-subdomains.txt
```

**Flags**

* `-a` → Get A records
* `-resp` → Show response
* `-silent` → Clean output
* `-o` → Output file

---

### 2. httprobe (by Tomnomnom)

Checks for HTTP/HTTPS servers on discovered subdomains.

#### Installation

```bash
go install github.com/tomnomnom/httprobe@latest
```

#### Usage

```bash
cat subdomains.txt | httprobe > live.txt
```

---

### 3. httpx (by ProjectDiscovery)

A powerful replacement for `httprobe` with more features.

#### Installation

```bash
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
```

#### Usage

```bash
cat subdomains.txt | httpx -silent -status-code -title -ip -tech-detect -o httpx-output.txt
```

**Flags**

* `-status-code` → Show HTTP status codes
* `-title` → Page titles
* `-ip` → Show IP addresses
* `-tech-detect` → Detect technologies

---

### 4. massdns (Blazing-fast DNS resolver)

Used for bulk resolution of domains.

#### Usage

```bash
./massdns -r resolvers.txt -t A -o S -w resolved.txt subdomains.txt
```

---

## Example Workflow

1. **Enumerate subdomains** (passive or wordlist-based)
2. **Resolve DNS** using `dnsx` or `massdns`

```bash
cat subs.txt | dnsx -silent -o resolved.txt
```

3. **Probe for HTTP(S) services**

```bash
cat resolved.txt | httpx -silent -o live.txt
```

---

## Output Example

```
https://api.tesla.com     [200] [Cloudflare] Tesla API
http://staging.tesla.com [403] [nginx]
https://shop.tesla.com   [200] [Shopify] Tesla Shop
```

---

## Notes

* Use **rate limits or proxy rotation** when scanning large scopes
* Combine **active and passive methods** for best results
* Always log output and manually verify false positives if needed

---

## Conclusion

Active subdomain enumeration is crucial for confirming **which assets are live and potentially attackable**. Tools like `dnsx`, `httpx`, and `massdns` can significantly **supercharge your reconnaissance phase**.
