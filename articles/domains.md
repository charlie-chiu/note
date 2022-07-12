
# TLD - Top-Level Domain

gTLD generic top-level domain  .com .net .org .gov 之類的

ccTLD country code top-level domain: `.tw` `.ca`

# Root Domain, Subdomain & subfolder

- apple.com. (root domain)
- charlie.site. (root domain)
- subdomain.apple.com/subfolder/
- label.label.label.com.tw (每一層都是個 label)

# 理論限制
- total length of a domain name: 255 (rfc1035)
- label 長度：0~63 字完， null label ( length zero ) 保留給 root
- 可用字：a-z, A-Z, 0-9 (LDH rule)
- Labels may not start or end with a hyphen.
- top-level domain names should not be all-numeric.
- 127 levels of label (基於255的總長度限制得出)

# Rule

> I believe the DNS itself can have up to 127 levels of label, each label can be up to 63 characters and the maximum length of the whole record is limited to 253 characters as you have to encode the length and a terminating 0.
domain name system - Is there a maximum subdomain depth? - Server Fault


> Any Fully Qualified Domain Name can be a host or a subdomain. - Wiki-Subdomain
From https://en.wikipedia.org/wiki/Subdomain#Overview


> In theory this subdivision can go down to 127 levels deep, and each  DNS label  can contain up to 63 characters, as long as the whole domain name does not exceed a total length of 255 characters. But in practice most domain registries limit at 253 characters.
From subdomain - Names and maximum lengths of the parts of a URL - Stack Overflow


# References

[Domain Name System - Wikipedia](https://en.wikipedia.org/wiki/Domain_Name_System#Domain_name_syntax,_internationalization)

[Domain name - Wikipedia](https://en.wikipedia.org/wiki/Domain_name)