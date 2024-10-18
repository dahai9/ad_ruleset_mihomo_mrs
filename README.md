# ruleset 规则集文件说明
本项目主要将[ios_rule_script/Clash广告部分](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash)转化为mrs以减小内存开销 

由于数据结构限制，domain-keyword无法完全转化，为达到最好效果建议如示例添加


## 1. 文件类型
① Clash ruleset 规则集文件，格式为 `.mrs`（`format: mrs`）  
## 2. 数据源
`rule-set,Advertising,🛑 广告拦截` 源采用 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash/Advertising)  

`rule-set,AdGuardSDNSFilter,🛑 广告拦截` 源采用 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash/AdGuardSDNSFilter)

`rule-set,EasyPrivacy,🛑 广告拦截` 源采用 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash/EasyPrivacy)

https://github.com/dahai9/ad_ruleset_mihomo_mrs/releases/download/clash-ruleset/Advertising.mrs
https://github.com/dahai9/ad_ruleset_mihomo_mrs/releases/download/clash-ruleset/EasyPrivacy.mrs
https://github.com/dahai9/ad_ruleset_mihomo_mrs/releases/download/clash-ruleset/AdGuardSDNSFilter.mrs
## 3. 文件使用
<details>
<summary>① Clash 内核</summary>

- 注：以下只是节选，请酌情套用

```
proxy-groups:

  •••
  
  - {name: 🛑 广告拦截, type: select, proxies: [REJECT]}

rule-providers:
  Advertising_c:
    type: http
    behavior: classical
    format: yaml
    path: ./rules/Advertising.yaml
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Advertising/Advertising.yaml"
    interval: 86400

  Advertising:
    type: http
    behavior: domain
    format: mrs
    path: ./rules/Advertising.mrs
    url: "https://github.com/dahai9/ad_ruleset_mihomo_mrs/releases/download/clash-ruleset/Advertising.mrs"
    interval: 86400

  EasyPrivacy:
    type: http
    behavior: domain
    format: mrs
    path: ./rules/EasyPrivacy.mrs
    url: "https://github.com/dahai9/ad_ruleset_mihomo_mrs/releases/download/clash-ruleset/EasyPrivacy.mrs"
    interval: 86400

  AdGuardSDNSFilter:
    type: http
    behavior: domain
    format: mrs
    path: ./rules/AdGuardSDNSFilter.mrs
    url: "https://github.com/dahai9/ad_ruleset_mihomo_mrs/releases/download/clash-ruleset/AdGuardSDNSFilter.mrs"
    interval: 86400

rules:
  - RULE-SET,Advertising_c,🛑 广告拦截
  - RULE-SET,Advertising,🛑 广告拦截
  - RULE-SET,AdGuardSDNSFilter,🛑 广告拦截
  - RULE-SET,EasyPrivacy,🛑 广告拦截


```
</details>

