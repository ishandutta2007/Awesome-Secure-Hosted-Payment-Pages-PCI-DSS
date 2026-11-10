# Awesome-Secure-Hosted-Payment-Pages-PCI-DSS

# Awesome Secure Hosted Payment Pages (PCI-DSS)

> A curated list of top Secure Hosted Payment Page platforms — both SaaS/Hosted commercial solutions and open-source alternatives for accepting payments while minimizing PCI-DSS scope.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Chargebee Hosted Pages](#chargebee-hosted-pages)
  - [Stripe Hosted Checkout](#stripe-hosted-checkout)
  - [PayPal Hosted Checkout](#paypal-hosted-checkout)
  - [Adyen Hosted Checkout](#adyen-hosted-checkout)
  - [Square Hosted Checkout](#square-hosted-checkout)
  - [FastSpring Storefront](#fastspring-storefront)
  - [Mollie Payment Links](#mollie-payment-links)
  - [Checkout.com Hosted Payments](#checkoutcom-hosted-payments)
  - [Authorize.Net SIM Hosted Form](#authorizenet-sim-hosted-form)
- [Open-Source Software](#-open-source-software)
  - [Payfolio](#payfolio)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Secure Hosted Payment Page platforms. These are not open-source but are included as reference points for feature comparison.

### Chargebee Hosted Pages
**Type:** Full-featured billing hosted pages with PCI DSS Level 1
Chargebee's hosted capabilities provide pre-built, configurable pages for checkout, customer portal, payment method management, and pay-now invoice collection [citation:1]. For card payments, they help meet most PCI DSS compliance requirements, with Chargebee stating PCI DSS Level 1 compliance [citation:1][citation:13]. Pages can be embedded via Chargebee.js (which creates and manages the iframe) rather than placing URLs in your own iframe [citation:13]. Supported features include multiple payment gateways, localization, brand customization, automated tax calculation, and subscription management offloading [citation:1].
**Best for:** Subscription businesses already using Chargebee for billing wanting hosted checkout and portal pages that offload PCI scope alongside subscription management.

### Stripe Hosted Checkout
**Type:** Hosted payment pages with strong recovery and compliance tooling
Stripe Checkout Sessions provide hosted payment pages for one-time payments and subscriptions, with Stripe recommending them as the preferred standard flow [citation:14]. Stripe helps businesses achieve and maintain PCI compliance [citation:2]. Revenue recovery features include Smart Retries (recovering 57% of failed recurring payments on average), reminder emails, and a hosted recovery page for updating payment details [citation:2]. Supports cards, digital wallets, bank redirects, and direct debits [citation:2].
**Best for:** Teams already on Stripe wanting hosted checkout with built-in revenue recovery and global payment method support.

### PayPal Hosted Checkout
**Type:** Hosted checkout with extensive payment method coverage
PayPal's hosted checkout accepts PayPal, Venmo, Pay Later, crypto, and major credit/debit cards, available in 200+ markets and 130+ currencies [citation:15]. Pricing is 2.99% + $0.49 per transaction for PayPal Checkout (hosted), with an optional Chargeback Protection add-on at 0.40% per transaction [citation:15]. PayPal manages PCI compliance for the hosted flow, and the platform includes built-in risk management and Seller Protection on eligible transactions [citation:15].
**Best for:** Businesses wanting broad consumer payment method coverage (PayPal, Venmo, cards) with managed compliance and no monthly fees.

### Adyen Hosted Checkout
**Type:** Customizable hosted checkout with theme support
Adyen Hosted Checkout supports theme creation with brand logo, display name, and default settings, with the theme ID passed in the `/sessions` request to style the hosted page [citation:5]. The session response includes the hosted page URL, which expires after 1 hour by default [citation:5]. Adyen supports a wide range of payment methods filtered by shopper country and currency, with risk checks and tokenization for stored payment details [citation:5].
**Best for:** Adyen merchants wanting a branded, themeable hosted checkout with global payment method coverage.

### Square Hosted Checkout
**Type:** Hosted payment links for forms and e-commerce
Square Hosted Checkout is available through various integrations (WooCommerce, WPForms, Fluent Forms, etc.), where buyers are redirected to a Square-hosted page to complete payment and then returned to the originating form or order [citation:4]. Payment links support pre-populated buyer email and phone for faster checkout, with customer linking via Square Customer Directory [citation:4]. Payment reminders for unpaid orders can be automated with the hosted checkout link [citation:4].
**Best for:** Businesses using Square for payments wanting hosted checkout integrated with forms and e-commerce platforms.

### FastSpring Storefront
**Type:** Merchant of Record storefront with hosted checkout
FastSpring acts as a Merchant of Record, handling payment processing and tax compliance. Store settings control localization (base and available currencies), invoicing (quotes, net terms, reminders), support contact display, and tax codes [citation:6]. The hosted storefront handles checkout, receipts, and self-service portals on the merchant's behalf.
**Best for:** SaaS and digital product businesses wanting a Merchant of Record to fully offload tax and compliance alongside hosted checkout.

### Mollie Payment Links
**Type:** Simple hosted payment links with QR codes
Mollie Payment Links create a URL (and QR code) that directs customers to a branded checkout page from any channel [citation:7]. Links can be created via the Mollie Web app or app with currency, amount, description, optional expiry date, and redirect URL, or programmatically via the Payment Links API [citation:7]. Mollie handles the payment page and PCI compliance for the hosted flow.
**Best for:** European businesses wanting simple, shareable payment links with QR codes without a full checkout integration.

### Checkout.com Hosted Payments
**Type:** Hosted payment pages and payment links
Checkout.com offers Hosted Payments Pages where customers enter payment details on a Checkout.com-hosted page, with a token generated in the background to complete the payment request [citation:10]. Payment Links can also be sent via email, chat, or text, directing customers to the hosted page [citation:10].
**Best for:** Checkout.com merchants wanting both hosted page and payment link options for accepting payments.

### Authorize.Net SIM Hosted Form
**Type:** Legacy hosted payment form with customization
Authorize.Net's Server Integration Method (SIM) provides a hosted payment form with configurable colors, fonts, header/footer text, form fields (view/edit/required), and optional CAPTCHA security code [citation:9]. **Important:** Authorize.Net notes that AIM, SIM, and DPM are obsolete and being phased out, recommending modern connection methods instead [citation:9].
**Best for:** Existing Authorize.Net merchants with legacy SIM integrations; new implementations should evaluate modern alternatives.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Secure Hosted Payment Page tools. The open-source ecosystem for **hosted payment pages** is extremely limited, as PCI-DSS compliance for handling card data requires significant infrastructure and auditing that most open-source projects cannot sustain.

### Payfolio
**Stack:** Next.js / TypeScript / Tailwind CSS | **License:** MIT
Payfolio is a self-hosted payment web application positioned as an open-source alternative to Patreon, Ko-fi, and Buy Me a Coffee, designed for creators to accept small contributions [citation:12]. Users select a number of "coffees," enter optional name and message, specify an amount, and donate. **Critical limitation:** Payfolio integrates with **Razorpay** for payment handling, meaning the actual payment page and card data handling are offloaded to Razorpay's hosted/embedded checkout—Payfolio itself is a frontend for initiating payments, not a PCI-compliant hosted payment page [citation:12]. It does not provide a hosted payment page in the PCI-DSS sense; it is a donation frontend that relies on a third-party gateway.
**Best for:** Creators wanting a self-hosted donation page that initiates Razorpay payments, accepting that PCI compliance and card handling are delegated to Razorpay.

---

## 📊 Comparison at a Glance

| Software | License | Stack | PCI Scope Reduction | Hosted Page | Self-Hosted | Best For |
|----------|---------|-------|---------------------|-------------|-------------|----------|
| **Chargebee** | Proprietary | Cloud | ✅ PCI DSS L1 | ✅ Checkout/portal | ❌ | Subscription billing + hosted pages |
| **Stripe** | Proprietary | Cloud | ✅ | ✅ Checkout Sessions | ❌ | Hosted checkout + recovery |
| **PayPal** | Proprietary | Cloud | ✅ Managed | ✅ Hosted checkout | ❌ | Broad consumer payment methods |
| **Adyen** | Proprietary | Cloud | ✅ | ✅ Themeable | ❌ | Branded global checkout |
| **Square** | Proprietary | Cloud | ✅ | ✅ Payment links | ❌ | Forms + e-commerce integration |
| **FastSpring** | Proprietary | Cloud | ✅ MoR | ✅ Storefront | ❌ | Full tax/compliance offload |
| **Mollie** | Proprietary | Cloud | ✅ | ✅ Payment links | ❌ | Simple links + QR codes |
| **Checkout.com** | Proprietary | Cloud | ✅ | ✅ Hosted pages | ❌ | Hosted page + links |
| **Payfolio** | MIT | Next.js | ❌ (Via Razorpay) | ❌ (Frontend only) | ✅ | Creator donations via Razorpay |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Secure Hosted Payment Page tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for **PCI-DSS compliant hosted payment pages** is essentially nonexistent. Hosted payment pages exist specifically to **reduce PCI scope** by ensuring card data never touches the merchant's servers, but building and maintaining such a service requires PCI-DSS certification (SAQ D or equivalent), which is a significant compliance and infrastructure undertaking that open-source projects cannot realistically sustain. **Payfolio** is the only open-source project found, and it delegates all card handling to Razorpay [citation:12]. For any production use case requiring PCI compliance, commercial providers (Stripe, PayPal, Chargebee, Adyen) remain the only viable options. Self-hosting a payment page directly (SAQ A-EP or SAQ D) introduces a full security program requirement that most teams should avoid [citation:11].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
