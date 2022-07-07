---
description: >-
  There are only two steps to use Launchpad: create a session, and then ignite
  it. In this example, I am going to show you how to create your first Launchpad
  session and how to ignite it!
---

# Your First Session

## What is a Session?

You can understand that one session is one API caller in a context. A context could be a page, a modal, a function, a component, and not necessary their children.

## Understand the Session

There are four lifecycles in a Launchpad session:

* **On Start:** It executes when the session is first inserted into the code. Usually happens before a page is loading. In React, it is the start value of a state, when no any `useEffect` is executed.
* **On Mount:** It executes when the session is mounted into the client. Usually happens when a page is loaded, a component is loaded, or an application is loaded. In React, it is the first `useEffect`.
* **On Override:** Most of the APIs require information from front-end (e.g. UUID, filter settings, etc.). So, _Override_ is the behavior that the front-end are setting parameters of the session. Launchpad can then re-make the API call, update information, or do anything you need.
* **On Unmount:** It executes when the session is going to be unmounted from the client. Usually happens when the lifecycle of a page is ended. You can unregister the listeners that were registered when page was mounted, or you can do anything you need. In React, it can be understand as the return function of an empty `useEffect` function.

## Smallest Example

{% tabs %}
{% tab title="React" %}
{% hint style="info" %}
In this example, we are using JavaScript.
{% endhint %}

### Example

A session object is fairly simple –– just a JavaScript object notation.

In this example, we are not going to send an API call because that is actually optional to the session! We will mention that in the _Fundamental_ section.

```javascript
const test = () => {
    return {
        // The start value.
        onStart: () => null,
        // The callback function when the session is mounted.
        onMount: ({ setState }) => {
            setState(1);
        },
        // The callback function when the `setParam` is called.
        onOverride: ({ state, setState, newValue }) => {
            setState(state + newValue);
        },
    };
};
```

The reason we wrap it as a function and then return a JSON is that we can have local variables inside the scope of this function. So you can use some variables to store things between different stages. But please be careful on what you store because it may violate the rule of React hook.

You have done creating the session! Now, let us ignite it in React.

It is similar to other hooks –– we got your back with a hook function `useLPSession`.

```javascript
const YourFunctionalComponent = () => {
    const { data, setParam } = useLPSession(test());
    return (...);
}
```

That is it! After that, you have a state variable `data` that has the information you need, and an override function `setParam` to send information to the session. Every time you call `setParam` will update the `data` automatically based on your session settings.
{% endtab %}

{% tab title="Svelte" %}
Svelte version is still under development. Check back later!
{% endtab %}
{% endtabs %}

## Why Launchpad Session?

You may feel that the Launchpad is over-powered in this case. The same functionality can also be achieved by using `useState`. But here are some use cases that you may want to use Launchpad over vanilla hooks:

* When you have an algorithm that may need to be changed over time. You can choose to write a function and then call the function before every state set. In a collaborative scenario, it is not perfect. By using Launchpad, the only things you exposed to other folks (who use your session) are the returned data, a simple set function, and a built-in loading indicator. It is safer, cleaner, and easier.
* When things become complicated (e.g. You are going to make a fetch request with the given data and set the result onto the state). If you choose vanilla hooks, you will write a bunch of things, which make your code not intuitive and decrease the reusability between different API calls.

{% hint style="warning" %}
**Maintainability:** In general, we recommend to write the session in a file that separates from the front-end UI components for a better maintainability. However, it is just an object notation, so you can write it wherever you like!
{% endhint %}

