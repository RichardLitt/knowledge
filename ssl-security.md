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

### Move to Cloudflare

This isn't great, becuase it still doesn't work for the main domain on GitHub.

Open questions:
- Which browsers does Cloudflare provide SSL for?
- Should I use LetsEncrypt instead? Why? 
- How is this different from using a paid service?
- Does moving to Cloudflare remove the benefit of being hosted on GitHub?

### Use Netlify.

Seems to be the best option.

##### Steps

Using https://www.netlify.com/docs/custom-domains.

- [x] Set up Netlify
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
