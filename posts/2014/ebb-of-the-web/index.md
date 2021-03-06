The ebb of the web
==================
posted: 2014-04-15

Tech pundits like to lament that the web has [no viable
future][no-viable], while web idealists hold that in fact the web is
totally fine, with a "too big to fail" [sort of attitude][recline].

At the root of this disagreement are poorly defined terms. The web can
mean many different things to different people. Though it started from a
pretty abstract notion of a series of interlinked documents, it has now
evolved to refer to a very specific technology stack of hyperlinked HTML
documents styled with CSS, enhanced with JavaScript, all served on top
of HTTP. In light of an increasing movement away from desktop-style
computing, we've seen a big shift away from the web in mobile platforms. 

Let's take apart this gob of web technology in light of the increasingly
complex landscape of computing and try to make sense of what the web is
and where it's going.

![A framework for webiness](webiness.png)

[no-viable]: http://cdixon.org/2014/04/07/the-decline-of-the-mobile-web/
[recline]: http://schepers.cc/the-recline-of-the-mobile-web

<!--more-->

## Webiness: how far down the rabbit hole?

I want to introduce the concept of webiness, a framework for evaluating
how deeply an application embraces "the web":

Games are typical examples of apps that are **pure native** and not
webby at all (barring high score servers, etc). Because many are
playable offline, with no added benefit of having an internet
connection, there is obviously no room for web. They are built entirely
on native APIs, benefiting from being as close to the hardware as
possible for performance reasons.

Another class of native apps are Twitter, Facebook and the like, which
essentially act as **specialized browsers**. They largely use HTTP to
access RESTful endpoints that serve up JSON, which is rendered by the
native clients. Because a specialized browser is designed for a specific
use case in mind (eg. interacting with Twitter), it can be streamlined
for that purpose and doesn't need to deal with processing the web's
presentation layer (HTML, CSS, JavaScript). Therefore it presents a
more focused experience and benefits from being faster at start-up and
during interaction, offline support, and a generally better experience.

**Embedded browsers** (also called hybrid apps) embed a webview into the
user interface of the page to use the web's presentation layer for part
of the user interface. How much of the user interface is created using
web technologies varies widely. This approach is beneficial because it
allows web developers to be featured in app stores, and also gives them
access to native APIs that are not available on the open web.

Lastly, **browser-based** pages and apps are ones where even the code
itself is fetched over HTTP. The app is written in a cross-browser way
to ensure that regardless of which browser loads the page, the user is
presented with a reasonable experience. The idea of this is to be able
to write once, deploy everywhere. Like the other types of apps on our
spectrum, these also use HTTP to interact with the server. All of the
content is rendered using HTML/CSS/JavaScript. Additionally, the HTML is
often hyperlinked.


## The web as greatest common divisor

In mathematics, the greatest common divisor (GCD) between multiple
digits is the largest positive integer that divides the numbers without
a remainder. Observe that the GCD of a set of numbers (S) is by
definition less than or equal to each number. Furthermore, if the
numbers in S are not multiples of one another, the inequality
becomes strict. So `foreach n in S, gcd(S) < n`.

In the webbiest case above, where we write once for all browsers, the
web user interface becomes the GCD for all existing interfaces. It is
guaranteed to be slower, less featureful, etc, than each individual
native platform, but when the web was conceived, the benefits outweighed
the costs. As the web evolved in the 90s, native platforms evolved
alongside it. Computing at the time was very desktop-centric, requiring
a physical keyboard, mouse, and relatively large display at, let's say
1024x768 pixels. At best, variance was between operating systems. The
computer geeks were on the Linux fringe. The art and music geeks used
Macs. But the hardware was pretty much the same.

Because of this uniformity, it was easy to standardize on a set of input
and outputs that would work reasonably well across a bunch of existing
computer configurations and operating systems. Computer hardware was all
very similar, just off by some factor. And the GCD of this orderly set
was pretty large: `gcd(200, 300, 400) = 100`.


## We're not in Kansas anymore

Contrast this uniformity to today, when our mots du jour are "mobile
first", or even "mobile only". But even these notions are becoming
passé, as our day-to-day tech encounters start including wearable
sensors for health, chips embedded in your appliances, shoes, and
computers on your face. Even with the most conservative notion of what
mobile means - small screens and touch input - we've really thrown a
wrench into the big-screen, mouse-and-keyboard web. Scott Jenson is
absolutely right in remarking in an [Edge conf panel][edge], that the
web hasn't even recovered from the fact that screens have gotten
smaller. With today's extended notion of computing, the GCD of all
of the devices and use cases the web is trying to support becomes very
small: `gcd(100, 200, 300, 50, 99, 198, 33) = 1`.

At the same Edge conf panel on the future of the web, somebody
asked the question of how the web would work on hardware without a
display. Answers from the panel were incoherent, but it's unclear how
this would be built into today's frankenweb, which is already a snowball
of many, often redundant technologies. And this is largely because of the
notion of **THE WEB** as a single platform. This is both its greatest
strength, and ultimately its tragic flaw, as the legacy of the early 90s
causes the singular web to cave in on itself, as we are experiencing
today.

We can no longer have a one-web-for-all approach. We need to focus on
having many different webs, each specializing on a particular subset of
our universe of devices. Taking our set above, we can split it in two
subsets, `S1 = {100, 200, 300, 50}`, and `S2 = {99, 198, 33}`.  Imagine
S1 are the desktop-like devices, and S2 are the phone-like devices. Now,
we have pretty okay GCDs: `gcd(S1) = 50`, and `gcd(S2) = 33`. Our worst
case GCD is now 33, which is a lot better than 1!

[edge]: https://www.youtube.com/watch?v=6u03xYkwMVI


## The web is dead, long live the web!

I'm pretty sure that HTTP is here to stay. Our desire for content is
universal, and that content needs to live somewhere. Regardless of how
that content is presented to us, it is likely to be served to us through
the cloud, over HTTP in the forseeable future.

What is indisputably being downplayed in the vibrant and variant near
future of computing, is the web's presentation layer - HTML, JavaScript
and CSS. These comprise the lingua franca of the web, and have no real
competition. However, this browser-served presentation layer of the web
will become less relevant as fewer things are done through the browser,
especially on mobile platforms.

To me, the critical thing is that content be addressable by URL, and
cross-linkable in some reasonable way. This is conventionally achieved
with HTML's `<a>` elements, but can also be done with JavaScript (eg. a
button that runs `javascript:window.location.href = myUrl;`, or a
`<form>` that creates a POST request to some other resource. This can
even be done without HTML at all. As long as we continue using HTTP, we
are guaranteed to have content that is available at a given URL. And as
long as we can guarantee that there's some handler for that content, the
spirit of the web lives on.


## Specialized browsers are a good solution

RSS readers are good examples of specialized browsers focused on
presenting a good reading experience to the user. They are a single
entry point for all of the interesting things on the internet for the
user to read.

The Twitter app on your mobile device is an example of a specialized
browser designed for reading and sending tweets. This specialized
browser relies on the web's ability to link to various kinds of content
addressable by URLs. Tweets typically include an article or an image
which are served up using HTTP, and sometimes require HTML to render.
Twitter is all about hyperlinked content, without ever using an `<a>`
tag.

Apple also has several projects that are specialized browsers in spirit,
though they rarely link out to the wild west of the world wide
web. Generally, these specialized browsers focus on giving a great
experience for the user aiming to do something specific. Similar in
function to an RSS reader, Newsstand is an entry point to the magazines
and newspapers you read. Passbook is a specialized browser for tracking
event tickets, boarding passes and coupons. From a developer
perspective, both of these browsers require you to setup a server and
write some iOS code. (Unfortunately you're then stuck in Apple's
ecosystem forever.)

By identifying common patterns of functionality, Apple is able to
successfully introduce a specialized browser notion that spans across
multiple services, unifying it with a consistent user experience. This
begins to address the concern that there are [too many apps for
everything][apps-must-die]. Of course you don't want separate apps for
NYTimes, WSJ, USA Today, LA Times, etc. And of course you don't want
separate apps for each event booking service, airline and coupon
company.

The problem is endemic to the web community. The standards process
behemoth is slow, heavy and change-averse. Its focus is on a monolothic
web, **THE WEB**. Imagine if we focused on use cases in the same way
that Apple does, and created specialized sub-webs for various related
things. The next big thing is wearable health. Imagine a sub-web for
that, where we get to define the way all of these devices can talk to
one another. There would be a browser for that sub-web, providing a good
experience to see historical data, analyze trends, and plot data over
time. This is not the stuff of a web browser, but a completely different
beast.

Android's intent filters are a step in the direction of a specialized
browser. Intent filters let apps register to handle specific URL
patterns. If the URL pattern is opened by the user, she is presented
with a dialog of all of the possible handlers for that resource, which
may include Chrome, other web browsers, and specialized browsers that
subscribe to that URL. Once you're in an Android app, however, you're
stuck. Unless the app provides the ability to share content, there's no
way to send your state to someone else. In contrast, with a web browser,
you just take the URL and send it to your friend and if they have access
to that content, they get to see it.

[apps-must-die]: http://designmind.frogdesign.com/blog/mobile-apps-must-die.html


## The web, the good parts

When tech pundits hail the ebb of the web, they mean that mobile native
apps are eating away at the presentation layer on the mobile web and
beyond. After some contemplation, I have made peace with this
possible future. HTML is not the best possible way of creating content,
nor is CSS a reasonable way of laying out content. JavaScript may be
commonly used, but that does not make it a very good language. The
presentation layer is optimized for content consumption using pointers
and keyboard input, or if you're really adventurous, a smaller touch
screen.

Apps are another story. Frameworks like iOS and Android provide a much
more modern, cogent way of developing apps for mobile platforms. But
unfortunately they aren't linkable or portable across platforms. As I
mentioned earlier, there's no need for `<a>` elements, or anything from
the presentation layer to preserve benefits of linkability. But what
does the web look like once we've gutted the presentation layer?  Here
are some characteristics that we should preserve:

- The ability to take any content that is currently being shown and
  serialize it into a URL.
- The ability to open a URL with the right specialized browser of the
  user's choosing.
- If no specialized browser is installed, some way of presenting the
  user with a list of good browsers.

By dropping the notion of **THE WEB** (singular), and ushering an era of
specialized browsers, we can split our universe of devices into subsets
and increase the baseline greatest common denominator. Trying to extend
the web to work for every possible case will lead to even more feature
creep in a web platform that is already keeling over.

The web community should take a look at verticals and spec and build
specialized browsers for them. How would a web for boarding passes,
concert tickets and coupons look like? How about a web for personal
health tracking data? A web for content that should be consumed on an
audio-only device?

This has been my slightly edited brain dump on the future of the web.
Thanks for reading, I eagerly await your thoughts :)
