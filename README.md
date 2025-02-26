1：家庭有部署公网服务，sb在单独的debian作为旁路网关，需要域名直接解析到局域网。
  dns-server添加"tag": "home-dns",地址为 "address": "local"，  dns-rule中匹配域名后缀 "domain_suffix"为".yourdomain.com",改为自己的域名，
  "server"为 "home-dns"，然后在singbox所在服务器，在hosts文件添加域名指向服务IP

2.外部场所，op作旁路部署sb，域名为AAAA且在cf解析，需要IPV6访问纯IPV6地址，避免域名geosite匹配为非cn到分流到proxy，且避免访问外网被解析到IPV6。
dns-rule中匹配域名后缀 "domain_suffix"这项里的server改为"dns_direct"，dns-server的 "home-dns"一组dns服务器可以删除。
