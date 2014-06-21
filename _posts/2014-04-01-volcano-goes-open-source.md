---
layout: post
title: "Volcano Goes Open Source"
description: "A gateway-agnostic billing system with a fully-featured API and front-end control panel."
category: 
tags: []
---
{% include JB/setup %}

<blockquote>
	<p>Patience, persistence and perspiration make an unbeatable combination for success.</p>
	<small>Napoleon Hill</small>
</blockquote>

Billing is a critical component for many software products. There are several solutions [to](http://www.whmcs.com) [choose](http://chargify.com) [from](http://paypal.com) yet integration and management are often a major headache. Today, I'm pleased to announce the launch of [Volcano](https://github.com/volcano/billing) - an API-driven billing solution that also includes an easy-to-use front-end control panel. Best of all, it's now [open source](https://github.com/volcano/billing)!

<a class="btn btn-primary" href="https://github.com/volcano/billing">
	View the GitHub Project
</a>

A Long and Winding Road
-----------------------
Volcano got its start in 2009. The original idea was to create an agnostic payment gateway system for my [employer's](/about.html) [Social CMS Platform](/projects.html#socialcore). The goal was to provide our customers with a new ecommerce add-on that could handle purchases through PayPal, Google Checkout, and other payment gateways. Unfortunately, the project stuttered along for a couple of years and never really got off the ground.

Fast forward to the the fall of 2012. At this point, my employer was offering traditional hosting and enterprise social media tools and building a new cloud hosting platform. Payments for the core products were running through a home-grown, Oracle-based billing system that was nearly 15 years old. This out-dated billing system was tightly-coupled to the company's hosting technologies and was nearly impossible to integrate into new product initiatives due to a lack of robust APIs. The original goal was to solve these issues by building a new billing infrastructure. However, these plans were scrapped in favor of [WHMCS](http://www.whmcs.com) leading up to the launch of our PaaS cloud platform at [SXSW](http://sxsw.com). WHMCS ended up working pretty well for the new product though it's lack of multitenancy support, incomplete APIs and other limitations left us searching for a better, long-term solution.

In the summer of 2013, a commitment was made to build a new Volcano. The brand-new version would include everything we needed to better automate enterprise purchases, improve product up sells and track churn and financial performance across _all_ of the company's products. In less than three months of development, the project quickly grew to include great APIs for developers and an easy-to-use control panel for management.

In the fall of 2013, I ended up leaving the company amidst plans to integrate Volcano into all of the products and migrate $2M+/year in transactions to the new system. As Volcano's product manager and lead developer, it was hard for me to step away from the project yet other factors necessitated a change in direction. It has certainly been a long, wild journey to get to the current incarnation of Volcano and I'm thrilled that it will now continue to evolve in the open source world!

Oh, and if you're wondering where the name "Volcano" came from - it was meant to symbolize a volcanic eruption of money. :-)


Why Volcano?
------------
Volcano was designed to be a simple yet flexible billing solution that's easy to integrate and supports a variety of use cases. Here's a quick visual overview of its features:

<div class="post-image-overview">
	<div class="thumbnail">
		<img src="{{ IMAGE_PATH }}/posts/volcano_settings.png" alt="Volcano Seller Settings" />
		<div class="caption">
			<h3>Multitenancy</h3>
			<p>Easily manage API access, payment gateways, contact information and other settings for all sellers.</p>
		</div>
	</div>

	<div class="thumbnail">
		<img src="{{ IMAGE_PATH }}/posts/volcano_products.png" alt="Volcano Seller Settings" />
		<div class="caption">
			<h3>Product Options &amp; Pricing</h3>
			<p>Easily manage multiple product lines, individual products and recurring/non-recurring fees.</p>
		</div>
	</div>

	<div class="thumbnail">
		<img src="{{ IMAGE_PATH }}/posts/volcano_customer.png" alt="Volcano Customer Management" />
		<div class="caption">
			<h3>Customer Management</h3>
			<p>Easily view and manage customer payment methods, orders, products, transactions and contact information.</p>
		</div>
	</div>

	<div class="thumbnail">
		<img src="{{ IMAGE_PATH }}/posts/volcano_statistics.png" alt="Volcano Statistics &amp; Reporting" />
		<div class="caption">
			<h3>Statistics &amp;  Reporting</h3>
			<p>Monitor growth and churn with daily and cumulative activity and conversion reports.</p>
		</div>
	</div>
</div>

<p class="text-center">
	<a class="btn btn-primary" href="https://github.com/volcano/billing">
		View the GitHub Project
	</a>
</p>

Next Steps
----------
The current iteration of Volcano is a great start. Yet there are still a few holes to be filled and plenty of improvements that can be made. Here are a few of the planned next steps:

* Improved Getting Started Wizard
* Dashboard Modules
* Orders View
* Improved Statistics & Reporting
* Seller Authentication and ACL
* Light-Weight CRM Tools

What Do You Think?
---------------------------
What challenges (or delights) have you had in the past when working with billing products? What interests you most about Volcano? Follow me [@smwxforever](http://twitter.com/smwrxforever) - I'd love to hear your [thoughts](http://twitter.com/smwrxforever) and [suggestions](https://github.com/volcano/billing/issues).
