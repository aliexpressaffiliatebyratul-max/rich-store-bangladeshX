# RICH STORE Bangladesh — Watch Store Starter

A mobile-friendly black-and-gold watch storefront starter with 10 sample products, product details, cart, and checkout form UI.

## Important status
This is a **front-end starter**, not yet a live production checkout. It does not currently store orders, send emails, or charge payments. Never advertise the online payment option as active until the backend and payment gateway have been configured and tested. Product photos are represented by a watch icon in this starter; replace them with photos you own or are authorized to use. Product prices/specifications are sample placeholders and must be checked before publishing.

## Files
- `index.html` — storefront, product cards, cart and checkout UI
- `supabase/schema.sql` — starter database table for orders
- `supabase/functions/create-checkout/index.ts` — secure backend scaffold notes for SSLCommerz + email integration
- `SETUP-BN.md` — Android-friendly setup guide in Bengali

## Free starter deployment
You can host the static frontend on GitHub Pages or Cloudflare Pages for free. A secure live checkout needs a backend/database and merchant credentials. For Bangladesh, apply for a supported payment gateway (for example SSLCommerz) and follow its current merchant onboarding/testing instructions. Provider eligibility, fees and approval are separate from hosting.

## Before launch checklist
1. Replace all sample prices and product specifications with verified supplier details.
2. Add real product images you have rights to use.
3. Add contact/support details, delivery policy, return/refund policy and privacy policy.
4. Set up Supabase database and secure server-side checkout endpoint.
5. Apply for and configure a payment gateway. Keep secret keys on the server only, never in `index.html`.
6. Add email notifications using a provider such as Resend from the server-side function.
7. Test sandbox payments and order status verification before taking real payments.
8. Configure order status updates and fulfilment workflow.
