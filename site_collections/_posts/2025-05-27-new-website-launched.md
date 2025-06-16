---
title: New website launched!
author: Jacky Song, Henry Wilkinson, TheFckinUnicorn
description: Our community effort has launched a new, modern website! Here's how we got here.
categories:
  - news
date: 2025-06-15
layout: post
postimg: img/news/website-launch/cover.png
postimgalttext: ""
---

After years of work, we're excited to announce the arrival of a new website for Natron! This community effort has been developed from the ground up to bring a new and modern face to Natron, while simultaneously being flexible, scalable and maintainable. Along with the website, we have also introduced refreshed branding that updates Natron's icon and logotype without sacrificing everything good about the old designs. This effort has gone through its fair share of ups and downs over the years; now having been officially published, we would like to take this opportunity to share our story!

## How it all started

The project was initially conceived in 2020 as an ambitious concept shared by [Jacky Song](https://jackysci.com) in a [Natron forum thread](https://discuss.pixls.us/t/natron-ui-re-design-proposal/18313) for a total GUI redesign for Natron. This was the first time that the people who would eventually spend years working together building the new website got to know each other and discussed their shared interest in Natron's design. Although the GUI redesign concept would not last long, it kicked off a long discussion about design in the community.

Six months into this discussion, Jacky posted mock-ups of a redesign of the Natron website, which was soon followed by a website concept by [Henry](https://wilkinson.graphics/). These posts marked the true beginning of our quest. What was initially a few design concepts and a back-and-forth discussion between Jacky and Henry on the forum soon turned into a centralised project with a collaborative workflow, with further discussions continuing in the Natron Discord server. Even though the website started taking shape within the course of a year, progress was slow: Jacky and Henry were only able to work on it in their spare time.

## Mock-up, Prototype, Test!

Our goal was to create a website for Natron that was modern and professional. Henry worked hard on establishing the core look and feel of the website as well as the bespoke iconography seen on our landing page.

{% include news-img.html 
   img="website-launch/website-artboards-1.png"
   alt=""
%}

Tailwind's [Typography plugin](https://github.com/tailwindlabs/tailwindcss-typography) and the [ElementaryOS blog](https://blog.elementary.io/) proved to be valuable sources for typography inspiration. We ultimately chose [Inter](https://rsms.me/inter/), a professional and versatile typeface with an extensive set of glyphs and support for advanced OpenType features. To give the website a distinctive look-and-feel, we incorporated glowing links, high-contrast colors, and vibrant gradients, which became integral to our core design language. A dark theme was chosen, inspired by Natron's purpose-designed UI dark theme, which is common for VFX work usually accomplished in dark rooms. Content was, inspired from what worked in the old website, such as a grid layout for the homepage features list.

{% include news-img.html 
   img="website-launch/website-artboards-2.png"
   alt=""
%}

As is with most design projects, the scope narrowed over time from complex mock-ups loaded with visual elements down to increasingly streamlined designs. Focus was eventually set upon delivering content in a simple and elegant manner.

{% include image-gallery.html folder="img/news/website-launch/mockup-iterations" %}

Constant communication and collaboration in the Natron Discord server and working together on Figma boosted the team's ability to implement changes and try out new things continually. This allowed our team to rapidly develop and implement new ideas and concepts.

## A Unified Design System

As soon as the design stage shifted towards web development, emphasis was put on developing a [design system](https://www.figma.com/blog/design-systems-101-what-is-a-design-system/). All of the work so far — the look and feel, the layout, the iconography, the typography, the mock-ups and design prototypes — were unified under one design language, custom-crafted for the Natron website. This further streamlined the project, giving a [single source of truth](https://en.wikipedia.org/wiki/Single_source_of_truth) for all our UI components, creating a solid base for further development.

{% include news-img.html 
   img="website-launch/design-system-1.png"
   alt=""
%}

{% include news-img.html 
   img="website-launch/design-system-2.png"
   alt=""
%}

This also meant that a unified repository of reusable UI components were readily accessible for quick mock-ups and prototypes for future additions to the website. Standardization and a component-based workflow were central towards making the design process as efficient as possible.

## Jekyll Adventures

Now having the design system in place, the team could now move to actual development. The decision was made early on to make the website a static site powered by [Jekyll](https://jekyllrb.com/). Jekyll takes HTML snippets and markdown files, and compiles them into pages for a static website. It is natively supported on [GitHub pages](https://pages.github.com/) (where Natron's then-current website was hosted), so it was a natural decision for the team.

Within time, a minimum viable product was ready. Some nifty additional features such as an Atom Feed developed by Henry and a [Natron Brand Assets page](https://natrongithub.github.io/brand) were added. The decision to use Jekyll had paid off, despite initial hiccups. Page layouts could be made in Markdown or basic HTML, and could be compiled by Jekyll using the design system templates. This meant that future additions, tweaks and changes would not take much time or effort.

## We did it!

When the team announced that the MVP was ready to be published, Natron developers and GitHub administrators [Frédéric](https://github.com/devernay) and [Aaron](https://github.com/acolwell) helped with archiving the old website and publishing the new one. After nearly 5 years of work, our project is a success, and the new website is now live!

It would be an understatement to say that this project was a _lot of work_! We couldn't have done it without all the contributions from the Natron community. Henry contributed a lot of his design expertise, made many artboards, mock-ups and prototypes, and developed the visual look of the website. Jacky contributed immensly to Henry's design and development efforts. [TheFckinUnicorn](https://thefckinunicorn.com/) contributed many hours of feedback and content, lending the website a professional aspect, and also helped coordinate the communication and collaboration efforts on Discord. Aaron helped tremendously by coordinating the logistics of the website repository, and also streamlining the handover and publishing processes. Last but not least, Frédéric and [Ole-André](https://github.com/rodlie) were instrumental in reviewing our work from the start, and giving the rest of the team the final go-ahead for the launch.

For the team, this project was an amazing learning experience, and each one of us is exhilarated to have been a part of this project. We certainly hope that this new website helps Natron (and by extension all other free and open-source software) to embrace high-quality design standards. It's been a long journey for us, and we hope this website will serve Natron well for years to come!

Thank you,

Henry, Jacky, TheFckinUnicorn.
