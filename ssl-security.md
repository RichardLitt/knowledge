# SSL Security

I want to update [burntfen.com](http://burntfen.com) to HTTPS. This would:

 - Make it look more professional.
 - Ensure that it comes from me by adding an extra step of validation.
 - Stop man in the middle attacks.

Currently, burntfen.com is hosted on GitHub Pages. The repo is at https://github.com/RichardLitt/richardlitt.github.com. GitHub pages [does not support SSL (secure socket layer) for custom domains.](https://github.com/isaacs/github/issues/156)

I could use Cloudflare as a CDN. It offers free SSL for some browsers.

## Requirements

- Https://burnfen.com should work.
- Going to http:// should redirect to https:// for all links.
- There should be a green lock in the browser bar.
- Free (no monetary cost)
- Easy (no maintenance cost)
- Maintain hosting on GitHub

## Possibilities

### Move to GitLab Pages

[Source](https://docs.gitlab.com/ee/pages/README.html#secure-your-custom-domain-website-with-tls)

This is a lot of overhead, and you'll lose GitHub integration and the community there. This should be the last possible step, for the sake of keeping overhead and maintenance low.

### Move to Cloudflare

Guides:
- [Cloudflare](https://blog.cloudflare.com/secure-and-fast-github-pages-with-cloudflare/)
- [Random guide](https://www.goyllo.com/github/pages/free-cloudflare-ssl-for-custom-domain/)

This isn't great, becuase it still doesn't work for the main domain on GitHub [1](https://www.quora.com/What-is-the-difference-between-Lets-Encrypt-and-Universal-SSL). However, it would use [Let's Encrypt](https://letsencrypt.org/getting-started/), which I've heard good things about. This probably isn't a good enough reason to switch.

Cloudflare is apparently also super annoying for people running TOR, but I'm not sure why. [2](https://github.com/opensourcedesign/opensourcedesign.github.io/issues/31).

Open questions:
- Which browsers does Cloudflare provide SSL for?
- Should I use LetsEncrypt instead? Why? 
- How is this different from using a paid service?
- Does moving to Cloudflare remove the benefit of being hosted on GitHub?

### Use Netlify.

Seems to be the best option. It is currently being used by [@mogden](https://twitter.com/stevekinney/status/797626436127522816), and doesn't take any extra steps but changing over DNS and adding to Netlify. This will also allow you to continue to publish to GitHub just fine - just add a Gemfile.

##### Steps

Using https://www.netlify.com/docs/custom-domains.

- [x] Set up Netlify
- [x] Add Gemfile to richardlitt.github.com
- [~] Change DNS servers _Waiting for confirmation, can take up to 24 hours._
- [ ] Enable security

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

