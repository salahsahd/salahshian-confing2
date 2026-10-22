# salahshian-confing2
perfect.yaml
geodata-mode: true
geo-auto-update: true
mixed-port: 7890
allow-lan: false
mode: rule
log-level: info
ipv6: false

dns:
  enable: true
  ipv6: false
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  nameserver:
    - 8.8.8.8
    - 1.1.1.1
    - https://dns.google/dns-query
  fallback:
    - 9.9.9.9
    - 208.67.222.222

proxies:
  - name: "🇺🇸 Salah Fast (VLESS)"
    type: vless
    server: 88.216.57.220
    port: 443
    uuid: 02722550-1915-4629-a653-cbe95e594f70
    network: tcp
    udp: true
    tls: true
    flow: xtls-rprx-vision
    servername: cdn12usa.goonars.com
    reality-opts:
      public-key: vFnG0SzHIv43o3L8bw4reKp3EIFuSS-BCyBqbWUsYCo
      short-id: 6591f200
    client-fingerprint: firefox

  - name: "🇺🇸 Kurdesh Fastly (VLESS)"
    type: vless
    server: 140.248.176.149
    port: 443
    uuid: cbcf2255-6d66-4039-b7d6-c10d6ffc99e7
    network: tcp
    udp: true
    tls: true
    flow: xtls-rprx-vision
    servername: ssl.fastly.com
    reality-opts:
      public-key: NozDA4apA_XQ_wzcJCZx7VXAD285J_HSs4w_GvBfJHA
      short-id: 63903c2e
    client-fingerprint: chrome

  - name: "🇩🇪 Kurdesh H2 (Hysteria2)"
    type: hysteria2
    server: 64.188.98.171
    port: 443
    password: mkL3AfdSZIpTWRB9TcWPn9vywPGN89MRHg3ToRDj
    sni: germany3.h2corp.local
    skip-cert-verify: true

  - name: "🇺🇸 Salah Trojan (Trojan)"
    type: trojan
    server: 165.215.250.14
    port: 443
    password: humanity
    sni: www.ignitelimit.com
    skip-cert-verify: true
    network: ws
    ws-opts:
      path: /assignment
      headers:
        Host: www.ignitelimit.com

  - name: "🇩🇪 H2 Aspidnet (Hysteria2)"
    type: hysteria2
    server: 162.249.125.133
    port: 443
    password: QCgqi_I4EkV8UR-OgQ_tG4EnVTEVvIyR2GgRBzrIn2s
    obfs: salamander
    obfs-password: c1b4086fea89914496c7e10967a419216566
    sni: hy2-new.aspidnet.xyz
    skip-cert-verify: true

proxy-groups:
  - name: "🚀 انتخاب خودکار (بهترین پینگ)"
    type: url-test
    url: "http://www.gstatic.com/generate_204"
    interval: 300
    tolerance: 50
    proxies:
      - "🇺🇸 Salah Fast (VLESS)"
      - "🇺🇸 Kurdesh Fastly (VLESS)"
      - "🇩🇪 Kurdesh H2 (Hysteria2)"
      - "🇺🇸 Salah Trojan (Trojan)"
      - "🇩🇪 H2 Aspidnet (Hysteria2)"

  - name: "🎯 انتخاب دستی"
    type: select
    proxies:
      - "🚀 انتخاب خودکار (بهترین پینگ)"
      - "🇺🇸 Salah Fast (VLESS)"
      - "🇺🇸 Kurdesh Fastly (VLESS)"
      - "🇩🇪 Kurdesh H2 (Hysteria2)"
      - "🇺🇸 Salah Trojan (Trojan)"
      - "🇩🇪 H2 Aspidnet (Hysteria2)"
      - "DIRECT"

rules:
  - IP-CIDR,127.0.0.0/8,DIRECT
  - IP-CIDR,192.168.0.0/16,DIRECT
  - IP-CIDR,10.0.0.0/8,DIRECT
  - GEOIP,IR,DIRECT
  - GEOSITE,IR,DIRECT
  - MATCH,🎯 انتخاب دستی
