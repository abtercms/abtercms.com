---
title: "AbterCMS Documentation"
---

# AbterCMS

[AbterCMS](https://abtercms.com/) is an open source, language agnostic, API-first, security-aware and scalable CMS. It aims to both provide a ready to use, easy to setup solution for simple landing pages that require an admin area for non-technical maintainers, and also to provide a good starting point for projects that want to start-off small but be prepared for rapid growth.

## Open Source

In 2019 there's very little explanation needed for why going with open source. Still, it might be worth noting that while AbterCMS is currently a one-man-show, it's creator, [Peter Aba](http://peteraba.com/) is ready to share as much responsibility for it's future as possible and dedicated to
keep all future versions free, both as in beer and as in speech. Honest feedback or help is always welcome and much appreciated.

## Language Agnostic

While Open Source is an attribute most readers will understand without further explanation, what a language agnostic CMS means might be less obvious. AbterCMS is meant to be a well-defined set of APIs, functional tests and end-user documentation, while various parts may be implemented in various languages, possibly even using different technology stacks for the different components and features.

You may be familiar with the [RealWorld example apps](https://github.com/gothinkster/realworld) project where the goal was to provide an API that resembles real world applications and let the community show case their favorite tech stack to implement those features.

Our goal here is slightly different. We want to provide useful functionality, and we're happy to let the community provide various solutions for them.

### Implementations

**So if AbterCMS is only an API, it must have some implementations, right?** Yes, currently there's only one implementation, written in PHP and built on top of the excellent [Opulence Framework](https://www.opulencephp.com/).
This implementation aims to be as simple to operate and develop for as possible, therefore it does not come with a fully-fledged frontend framework, but provides some frontend functionality via [jQuery](https://jquery.com/).

  * **Github:** [https://github.com/abtercms/abterphp](https://github.com/abtercms/abterphp)
  * **Documentation:** [https://abterphp.abtercms.com/](https://abterphp.abtercms.com/)

### Considerations

While, AbterPHP is the only implementation at the time of this writing, it's important to state that AbterPHP will not be considered stable before there's an easy and well-documented way for extending it using other tech stacks. This would have to include being able to modify the admin navigation, creating, modifying or disabling grids and forms or
enabling the frontend templating system to render custom tags. All this will have to be possible via the RESTful API.

## API-first

AbterCMS is not the only CMS in the open source ecosystem that claims to be designed API-first. But it's one of the very few that could, to some extent, add that it's actually **API-only**. As explained above, AbterCMS is really just a set of various APIs and promises that the various implementations abide to.

The API provided is meant to follow the [Zalando guidelines](https://github.com/zalando/restful-api-guidelines), because they are comprehensive and are based on widely-accepted best practices.

{{% notice info %}}
The stability of the API is a clear goal for the time AbterCMS matures, before 1.0 however it is subject to changes without prior notice.
{{% /notice %}}

## Security-aware

Admittedly, there's no such thing as completely secure, but it is also recognized that security needs to be a driving force while designing software systems. AbterCMS not only promotes best practices, it makes them easy to use and in some cases deliberately hard to dodge them. It's understandable if you're not yet convinced, but we have a lot more to say [about security]({{%relref "basics/security/_index.en.md" %}}).

## Contribute to this documentation
Feel free to update this content, just click the **Edit this page** link displayed on top right of each page, and pullrequest it

{{% notice info %}}
Your modification will be deployed automatically when merged.
{{% /notice %}}
