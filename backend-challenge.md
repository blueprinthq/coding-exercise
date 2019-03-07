## Context
In order to help us judge the technical capabilities of our candidates, we ask everyone to do a short coding exercise. Please spend no longer than 60 minutes on this challenge. If you don't end up with a complete solution in that time, that's fine, just submit it anyway. We don't expect this to be enough time to write "The Most Perfect Thing". The things we're assessing are:
- How you interpret requirements
- How you approach problems
- How you use source control
- How readable & maintainable your code is

You're free to use whatever language, framework, libraries, tools, editors, search engines, etc you like in order to complete the challenge.

## Your mission

A client needs to know what is happening on the social networks. All of them. Right now.

The three social networks the client is interested in are:

https://takehome.io/twitter

https://takehome.io/facebook

https://takehome.io/instagram

Because these social networks are so webscale, they don't always respond predictably. The delay in their response almost appears like someone waited for a random integer of seconds before responding!

Also, sometimes they will respond with an error. This error will not be valid JSON. Life's hard sometimes.

The client needs to be able to run your thing, then issue the command:

```
curl localhost:3000
```

And get back a JSON response of the output from the three social networks in the format:

```
{ twitter: [tweets], facebook: [statuses], instagram: [photos] }
```

Order isn't important. This should be a quick little task, but the client is paying us A Billion dollars for it so make sure your implementation is as robust as it is beautiful.

## Deliverable
- Please send us a link to the hosted repository with your code (e.g. Github, Bitbucket)
- The repo should include a README that includes the following items:
  - Description of the problem and solution
  - Reasoning behind your technical choices
  - Trade-offs you might have made, anything you left out, or what you might do differently if you were to spend additional time on the project
  - Link to other code you're particularly proud of
  - Link to your resume or public profile
