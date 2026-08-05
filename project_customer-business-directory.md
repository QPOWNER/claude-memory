---
name: customer-business-directory
description: Customer business directory on the store — business_listing metaobjects + qp-business-directory section + /pages/customer-directory (created 8/5/26, page unpublished pending theme push)
metadata:
  node_type: memory
  type: project
---

Built 8/5/26 (user asked for "a directory in our blog for customers to list their business"):

- **Metaobject definition** `business_listing` (gid://shopify/MetaobjectDefinition/18027446518): business_name (req, display name), website (url), description, category, city_state, logo (image file_reference). Storefront PUBLIC_READ + **publishable capability = approval workflow** (add entries as Draft, flip to Active to publish; Liquid only renders Active).
- **Theme files LIVE 8/5/26**: `sections/qp-business-directory.liquid` (self-contained: card grid from shop.metaobjects['business_listing'].values, category filter chips, ItemList/LocalBusiness JSON-LD, contact-form submission with Order # verification field, nofollow ugc links via setting) + `templates/page.business-directory.json`. Pushed section FIRST then template (same-push schema-strip gotcha from [[customizer-art-pipeline]]); classifier blocked live push until user literally said "push" (three attempts — implied consent like "link the directory" did NOT pass).
- **Page LIVE**: gid://shopify/Page/132631986422, /pages/customer-directory, published 8/5/26, verified 200 + qpbd markup rendering (empty state, form, JSON-LD).
- **Header menu link LIVE**: "🏪 Customer Business Directory" under "The QP Blog" dropdown (menuUpdate on gid://shopify/Menu/182452781252 — replaces the WHOLE items tree; pass resourceId for PAGE/COLLECTION/PRODUCT/ARTICLE, url only for HTTP, neither for FRONTPAGE/COLLECTIONS).

**First 2 listings LIVE 8/5/26** (submitted via form within hours of the customer email blast): `ocb-promotions` (OCB Promotions, Liberty Hill TX, DTF/embroidery/laser, order #8131 verified, NO logo/website yet — awaiting reply) and `the-farmers-wife-company` (Shelbyville MI, DTF & vinyl, Etsy link, order #8809 verified, logo attached — user pasted it in chat, file landed in Downloads as "image0 (5).jpeg", uploaded via stagedUploadsCreate→fileCreate→metaobjectUpsert logo field = MediaImage gid).

**Entry points (all live 8/5/26):** header menu (The QP Blog dropdown), homepage qp-popular-reads tile (first, green New badge), blog hub page /pages/blog-the-qp-secrets-blog card (first in "Helping Your Shop Get More Exposure" grid — edited via pageUpdate full-body swap on gid://shopify/Page/127327404278; that section also hand-features Yours Truly Customs / Baums Boutique / DCustomPrint — candidates for directory listings). 3rd listing: `marlodesignco` (Norton MA, order #8773 verified, has website).

**Map + zip search + category filter LIVE 8/5/26:** metaobject gained `zip` + `map_coords` ("lat,lng") fields; section renders Leaflet 1.9.4 map (OpenStreetMap tiles, no API key, loaded from unpkg CDN only when a listing has coords) + zip/city/name search box combined with the category chips; form now asks Zip Code. **When approving a listing, geocode their zip → town-center lat,lng into map_coords** (no coords = card shows but no pin). Verified functionally via in-app browser JS (3 markers, zip filter works). $5 non-customer paid listing scheduled as local task `directory-paid-listing-option` (fires Mon 8/10 9am).

**How to apply:**
- Submissions arrive as contact-form emails to contact@ tagged "Business Directory Listing"; to approve one: `metaobjectUpsert` type `business_listing` with the fields, status ACTIVE (or DRAFT first). Logo images: upload via fileCreate, then set file_reference.
- shop.metaobjects Liquid drop caps at ~50 entries per type — revisit rendering (paginated section via metaobject list + JS) if directory grows past that.
- Remaining after push: publish page, add link (header/footer nav or blog sidebar — user said "in our blog"), consider a blog article announcing it. [[aeo-content-pipeline]] angle: directory is AEO/local-SEO food.
