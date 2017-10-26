# SSL Security

Updating to SSL is important:

- It makes a website look more professional.
- Ensure that the website comes from the authorized author adding an extra step of validation.
- Control: Some WIFI providers will try to inject their ads into your site. HTTPS protects you and your users. This will also stop man-in-the-middle attacks.
- SEO: Google gives an SEO bonus to sites with HTTPS support.
- Analytics: You will only see inbound referrers from sites using HTTPS if your own site use HTTPS.
- Performance: Modern browsers support HTTP 2.0, only for sites with HTTPS enabled. For some sites HTTP 2 can give significant performance improvements.

GitHub Pages [does not support SSL (secure socket layer) for custom domains.](https://github.com/isaacs/github/issues/156) This means that, if you'd like to host a GitHub Pages website using SSL, you'll need to switch to something else.

## Table of Contents

- [Requirements](#requirements)
- [Possibilities](#possibilities)
  - [Move to GitLab Pages](#move-to-gitlab-pages)
  - [Move to Cloudflare](#move-to-cloudflare)
  - [Use Netlify.](#use-netlify)
- [Process](#process)
- [Questions](#questions)
  - [Is SSL Security the same as using HTTP and switching to HTTPS?](#is-ssl-security-the-same-as-using-http-and-switching-to-https)
  - [Does this matter for static sites?](#does-this-matter-for-static-sites)
  - [Are DNS and Nameservers the same?](#are-dns-and-nameservers-the-same)

## Requirements

- https://website.com should work.
- Going to http:// should redirect to https:// for all links.
- There should be a green lock in the browser bar.
- Free (no monetary cost)
- Easy (no maintenance cost)
- Maintain hosting remains on GitHub

## Possibilities

Here are the different possibilities I have tried. In the end, I went with Netlify.

### Move to GitLab Pages

[Source](https://docs.gitlab.com/ee/pages/README.html#secure-your-custom-domain-website-with-tls)

This is a lot of overhead, and you'll lose GitHub integration and the community there. This should be the last possible step, for the sake of keeping overhead and maintenance low.

### Move to Cloudflare

Guides:
- [Cloudflare](https://blog.cloudflare.com/secure-and-fast-github-pages-with-cloudflare/)
- [Random guide](https://www.goyllo.com/github/pages/free-cloudflare-ssl-for-custom-domain/)

This isn't great, because it still doesn't work for the main domain on GitHub [1](https://www.quora.com/What-is-the-difference-between-Lets-Encrypt-and-Universal-SSL). However, it would use [Let's Encrypt](https://letsencrypt.org/getting-started/), which I've heard good things about. This probably isn't a good enough reason to switch.

Cloudflare is apparently also super annoying for people running TOR, but I'm not sure why. [2](https://github.com/opensourcedesign/opensourcedesign.github.io/issues/31).

Open questions:
- Which browsers does Cloudflare provide SSL for?
- Should I use LetsEncrypt instead? Why? 
- How is this different from using a paid service?
- Does moving to Cloudflare remove the benefit of being hosted on GitHub?

### Use Netlify.

Seems to be the best option. It is currently being used by [@mogden](https://twitter.com/stevekinney/status/797626436127522816), and doesn't take any extra steps but changing over DNS and adding to Netlify. This will also allow you to continue to publish to GitHub just fine - just add a Gemfile.

I've also used it for multiple sites, at this point.

## Process

- [ ] Set up Netlify. Make an account.
- [ ] Add your site to Netlify from your GitHub Repository. Use the right build commands, such as `jekyll build`, and folder, such as `_site`.
- [ ] Add Gemfile to your site. It should have these contents, if Jekyll:

```
source 'https://rubygems.org'
gem 'jekyll'
gem 'github-pages', group: :jekyll_plugins
```

- [ ] Look at the deployed test site, and fix any Mixed Content or CORS issues that HTTPS throws up.
- [ ] Add a CNAME that points to your root domain: for instance, `nomadasfuck.com`.
- [ ] Change DNS servers (but not nameservers). Instructions: https://www.netlify.com/docs/custom-domains/
- [ ] Enable security on Netlify. Force a redirect to https.

## Questions

### Is SSL Security the same as using HTTP and switching to HTTPS?

Yes.

> HTTPS (also called HTTP over TLS,[1][2] HTTP over SSL,[3] and HTTP Secure[4][5]) is a protocol for secure communication over a computer network which is widely used on the Internet. HTTPS consists of communication over Hypertext Transfer Protocol (HTTP) within a connection encrypted by Transport Layer Security or its predecessor, Secure Sockets Layer. The main motivation for HTTPS is authentication of the visited website and protection of the privacy and integrity of the exchanged data.

[Source](https://en.wikipedia.org/wiki/HTTPS)

### Does this matter for static sites?

Yes.

- Improves Google Rankings.
- Makes your site invulnerable to man-in-the-middle attacks (think Airports, think people redirecting or changing traffic)
- Makes your site look better to others (marketing).

### Are DNS and Nameservers the same?

[No.](http://www.pcnames.com/articles/the-difference-between-dns-and-name-servers).

DNS stands for _Domain Name System_, and not _Domain Name Servers_. This can be confusing. It looks like, on Hover, if you're going to use their DNS settings, you need to have the Nameservers pointed to Hover's nameservers (but, now that I think about it, this doesn't apply to MX records.)
