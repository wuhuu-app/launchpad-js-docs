---
description: A modern API hook management system.
layout: landing
---

# Meet the Launchpad



![](<.gitbook/assets/Launchpad JS Cover (1).png>)

{% hint style="info" %}
**WIP:** This documentation is still a Work In Progress. We are happy to hear from you about any suggestion or any issue that we have!
{% endhint %}

Launchpad helps you quickly and painlessly integrate the front-end user interface with API calls (or mock calls) throughout the entire life cycle of your application.

It is a brand new idea on modularizing the fetching session (the API call from server to client, or a pure local call that happens behind the UI codes) and being ease with any change that may happen on an API algorithm (or even the mock one).

With Launchpad, you can define an API hook by writing its schema – including how every state turns, how API request will be fired, and everything you can imagine.

The coolest thing is that UI developer can call API by simply calling the hook function, with loading state built-in and their favorite objects as parameters.

## Understanding the Architecture

Launchpad is an additional layer lying between the front-end application and API calls. A Launchpad session can take input, convert arguments into proper JSON, and then send package to the back-end. When back-end replies, Launchpad will update the exposed state variable based on how it was configured.

So in the low-level, Launchpad is simply wrapping the essential algorithm by using hooks, and exposing most-needed APIs for a session. It saves a lot of time for UI developers to write fetching algorithm and manage annoying states (e.g. loading, error, and more) in UI files.

## Getting Started

### Guides: Make your first step

Follow our handy guides to get started on the basics as quickly as possible:

{% content-ref url="guides/installation.md" %}
[installation.md](guides/installation.md)
{% endcontent-ref %}

{% content-ref url="guides/your-first-session.md" %}
[your-first-session.md](guides/your-first-session.md)
{% endcontent-ref %}

{% hint style="info" %}
**Why guides:** Follow our guide will be the best way to understand why you may need to use Launchpad. Please understand that not everyone needs it, so just use-it-when-you-need.
{% endhint %}

### Fundamentals: Dive a little deeper

Learn the fundamentals of Launchpad to get a deeper understanding of our main features:

Want to build an API call that is not just a simple call? Follow our example to make sure that you are using it right!

{% content-ref url="fundamentals/design-a-complex-session.md" %}
[design-a-complex-session.md](fundamentals/design-a-complex-session.md)
{% endcontent-ref %}

Want to integrate Launchpad with authorization? We can handle the authorization stuff for you, built-in. Check our guide on authorization flow and you are good to go!

{% content-ref url="fundamentals/authorization-flow.md" %}
[authorization-flow.md](fundamentals/authorization-flow.md)
{% endcontent-ref %}

Want to make some changes globally? See if you can do that by setting up a configuration file!

{% content-ref url="fundamentals/configuration.md" %}
[configuration.md](fundamentals/configuration.md)
{% endcontent-ref %}

## Credits

Greatly thanks to Alex (Chaolong) for giving the idea on the name of some API properties.
