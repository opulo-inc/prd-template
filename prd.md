# Product Requirement Document Template

This is a standard template for a Product Requirement Document, or a PRD.

The goal of a PRD is to explicitly define **what a product should be**. The reasons to make one are to ensure that:

1. the product you're making is actually wanted and will sell.
2. the entire organization is on the same page about the product.

All examples are for a **theoretical machine that makes peanut butter and jelly sandwiches**.

## Overview

Short description of what we’re building.

Example:
> This PRD proposes a desktop machine to automatically assemble peanut butter and jelly sandwiches.
>
> The overall vision for the machine is to create a device that makes the setup and consistent running of peanut butter and jelly assembly jobs easy and consistent.

## Goals

A bit more specific about what it needs to do. Not getting into hard metrics yet, just broad categories of tasks that it needs to be able to perform.

They should be as specific as possible, with zero implementation details. This should be in bullet point format.

Example:

> - A desktop-sized device that isn’t exorbitantly expensive to ship
> - Minimal and simple machine assembly setup process (if any)
> - Attractive looking, would fit in a consumer kitchen setting
> - Usable for real manufacturing work on a production line
> - Easily configurable for a wide range of jelly and peanut butter types
> - Open Source and possible to build by the hobbyist

## Non-Goals

Being very clear about what it shouldn’t be required to do. This helps prevent scope creep, and allows you to be a bit more opioniated with your design decisions and really focus on the things that matter to your users.

They should be as specific as possible, with zero implementation details. This should be in bullet point format.

Example:

> - Supporting any materials other than peanut butter and jelly (no jams,marmalades, or preserves)
> - Supporting any bread larger than a standard mass-produced loaf (~10cm by ~10cm)

## Audience

This is some short prose about who the product is for. It should go into what a user wants from the product, and how they want to interact with it. What’s important to them while using it.

Example:

> The majority of the audience for this machine consists of sandwich shop owners between the ages of 30 and 50. Around ¾ of exisiting sandwich assembly equipment sales have gone to small businesses and sandwich manufacturers, with a smaller amount going to consumers.
>
> The majority of organizations want a machine that just works. Their interaction with the machine is driven by the desire to create a delicious sandwich. They are less interested in deep understanding, tuning, or modifying their machine.
>
> There is a smaller group of enthusiasts and hobbyists that enjoy tinkering with their machine and expanding or modifying its functionality, allowing it to make more exotic sandwich types. This group's experience and perspective will differ from the majority of users.

## Existing solutions and issues

This is a section about other options, and why they’re less than ideal. Bullets of these reasons, helps to justify why we’re creating the product.

> While there exists a number of other automatic sandwich assembly machines, each lacks in a unique way:
>
> - The SammyJammer
>   - Poorly documented and very difficult to use, often resulting in uneven amounts of ingredients in the sandwich.
>   - Closed source and hard to repair
> - The Panera Bread 54NDW1CH-5000
>   - This machine is excellent, but exorbitantly expensive for anyone other than a very large chain.
>   - Requires a monthly service contract.
> - Hand Assembly
>   - Slow, and only works at very small scales.

## Assumptions

These are things about the users, what they’re dealing with, what we can assume about the experience or how we should be designing the product.

**Every one of these** should have a link to a customer interview, backing up your assumption. No guesses, no gut reactions. They should **all** come from data.

This is an inherently flawed process, as making broad, sweeping generalizations will always lack nuance. However, your audience has one thing in common: they could benefit from your product. Finding all the other broad themes from this group can help you figure out what to prioritize.

Example:

> - All users are familiar with the process of assembling a peanut butter and jelly sandwich.
> - Some users have never operated a sandwich assembly machine before.
> - Most users care about consistency and reliability more than speed.
> - Most users are using their machine to make sandwiches to sell for their business.
> - Some users care about hackability and the ability to easily modify their machine.

## Constraints

This section gets close to implementation details, but not quite. Based on the assumptions from research. Broad strokes like “written in python” or “should be a web application.” These should be bullet points.

Example:

> The machine should be a stable, reliable, and evergreen design. We need to highlight a few constraints of the product:
>
> - The bulk majority of the machine consists of FDM 3D printed parts and off-the-shelf hardware.
> - The machine’s API is a 5" touchscreen, two indicator lights, and a buzzer.
> - The machine's control board is custom, integrating custom sensors for detecting viscosity and thickness of the spreads.
> - The machine accepts standard peanut butter and jelly jars as material repositories.
> - The machine should be able to operate in a consumer kitchen setting (no high-pressure air, 240v, excessive noise/smell, etc)

## Key use cases

These are all the situations in which people are interacting with the product, and for what reason. These are really the tasks the product must complete.

Example:

> - Easily assemble from packaging
> - Facilitate easy job setup and configuration
> - Consistently and reliably assemble peanut butter and jelly sandwiches with a +-2mm spread thickness tolerance
> - Easy to use on-screen UI

For every use case listed, there should be a detailed section about how the product will accomplish this goal and fulfill this use case.

Example:
> ## Easily Assembled
> Describe the extent to which the user would need to assemble the machine, and otherwise get it up and running from the box.
> 
> ## Easy Job Setup
> Explain how bread, peanut butter, and jelly will be loaded in. Explain how the user will start a job.
>
> ....

## Research

This section outlines any research questions that helped inform how this PRD was written. Although at the end, this section **must be completed before the PRD is written**, as it fully informs what the product is.

### User Research

This section should inform the vast majority of the rest of this document. It should be in the format of a few key questions as headers that will inform how you build your product, with an answer based on your research below.

This entire section should contain links to notes from interviews you've performed with current or potential customers.

Example:

> ### How important is speed?
> 
> The speed of the machine (usually referred to in Sandwiches Per Hour, or SPH) is the core metric of a sandwich assembly machine. Our users are mostly using their machines to assemble sandwiches for their sandwich shop, so making sure the machine can keep up with demand is critical for them.
> 
> From [many]() [interviews]() [with]() [customers](), it seems we need to hit about 20 SPH to fulfill the demands of their production. After around 20 SPH, the bottleneck becomes how quickly their counter clerks can take the order and handle the customer's payment. To safely cover almost all customer use cases, we'll ensure we can make at least 25 SPH. Anything beyond that is great, but not a requirement.
>
> ### Should we support Turkey Sandwiches?
>
> .....etc......

### Technical Research

This section should inform the the rough structure of how your product will be built. Math, component spec research, and even some quick prototypes might be required to complete this section.

Example:

> ### How much faster does the machine get with CoreXY motor config?
>
> Switching to CoreXY makes the following changes to potential top acceleration:
> 
> - Less mass on the Y gantry
> - Only two motors facilitating all movement, instead of three
>
> This problem was explored using the [XY vs CoreXY Acceleration Comparison sheet](). Looking at the resultant theoretical acceleration from different motor configurations, it’s clear that CoreXY is a much better choice in terms of spreading speed. Assuming four passes on each piece of bread for spreading, we'll need a CoreXY configuration to be able to hit our 25 SPH speed metric.
