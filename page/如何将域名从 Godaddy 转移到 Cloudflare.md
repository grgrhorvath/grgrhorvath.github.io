## 背景

Godaddy 域名续费费用较高（159 RMB/年），而 Cloudflare 的域名续费仅需 80 RMB/年，性价比更高。正好有一个域名需要续费，因此决定将其转移到 Cloudflare 后再续费。

---

## 转移步骤

### 一、添加域名到 Cloudflare

1. 登录 [Cloudflare 控制台](https://bit.ly/bewildcard)，选择“添加域”，将域名添加到 Cloudflare。
2. 添加后，Cloudflare 会自动读取现有的 DNS 配置并自动添加，按照提示继续操作。
3. 配置完成后，Cloudflare 会提示需要在 Godaddy 更换名称服务器。记录下 Cloudflare 提供的名称服务器信息，准备进行下一步操作。

---

### 二、在 Godaddy 更换名称服务器

1. 登录 [Godaddy 控制台](https://dcc.godaddy.com/)，选择需要转移的域名。
2. 设置域名服务器，将 Cloudflare 提供的名称服务器填入对应位置。
3. 保存设置后，返回 Cloudflare 查看域名状态。如果状态显示为“活动”，则名称服务器更换成功。

---

### 三、转移域名到 Cloudflare

1. 登录 Godaddy，选择需要转移的域名。
2. 点击“转移到另一个注册商”选项。
3. 按照提示操作，获取转移授权码（Auth Code），记录下来备用。
4. 登录 Cloudflare，选择“转移域名”功能，按照提示操作。
5. 在转移过程中，需要输入 Godaddy 提供的授权码，并支付域名续费费用（80 RMB/年）。
6. 提供有效的支付卡信息（建议使用支持国际支付的卡片），完成支付后域名转移将正式开始。
7. 返回 Godaddy，确认域名转出请求。
8. 当收到域名转移完成的确认邮件时，表示域名已成功转移到 Cloudflare。

---

## 小贴士

- Cloudflare 的域名续费费用远低于 Godaddy，适合长期使用。
- 转移过程中需要使用支持国际支付的卡片，推荐使用虚拟卡完成支付。

👉 [野卡 | 一分钟注册，轻松订阅海外线上服务](https://bit.ly/bewildcard)