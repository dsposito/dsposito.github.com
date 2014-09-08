---
layout: post
title: "Designing For Change"
description: "Designing For Change: Leveraging the adapter design pattern."
category: 
tags: []
---
{% include JB/setup %}

<blockquote>
	<p>You must welcome change as the rule but not as your ruler.</p>
	<small>Denis Waitley</small>
</blockquote>

Today's era of software is all about 3rd-party integration and the sharing of data. It's no longer *optional* for your app to be able to integrate or be integrated with other apps and services. It's a *necessity*. Whether it's a small library, an open source framework, or a robust 3rd-party service - software today is built by connecting a variety of tools and services.

When adding a major new feature to your app there's likely a plethora of existing 3rd-party solutions that you could plug in. Each one of these solutions has its own pros and cons and custom integration points.  *Wouldn't it be great if you could spend less time worrying about future changes to the custom integration process and instead easily swap in/out solutions now or in the future?* Let's take a look at several reasons this capability would be helpful and how you can implement this approach with the [adapter design pattern](http://en.wikipedia.org/wiki/Adapter_pattern).


Why Design For Change?
----------------------
Your app is going to need to change as its industry and market players evolve over time. Designing for change can save you a lot of time and headache when these changes occur in the not-too-distant future. It also leads to many other opportunities and benefits. Here are a few real-world examples:

<br />

<div class="row post-image-overview-grid">
	<div class="col-sm-6 col-md-4">
		<div class="thumbnail">
			<i class="icon-hdd"></i>
			<div class="caption">
				<h3>Backup Plan</h3>
				<p>Consider the scenario in which you have a news app that relies on sports data from ESPN. You'll find yourself scrambling to integrate a new sports news service if the current provider <a href="http://developer.espn.com/blog/read/publicretirement">suddenly decides to shut down its API</a>. Designing for change allows you to easily switch to a different provider when needed.</p>
			</div>
		</div>
	</div>
	<div class="col-sm-6 col-md-4">
		<div class="thumbnail">
			<i class="icon-sitemap"></i>
			<div class="caption">
				<h3>Multi-Option Support</h3>
				<p>If you run an online store, it'd be great if you gave your customers multiple payment options when it comes time to make a purchase. If you use the adapter pattern, your app can not only easily switch between Credit Card, PayPal and BitCoin - it could actually enable all three options at once.</p>
			</div>
		</div>
	</div>
	<div class="col-sm-6 col-md-4">
		<div class="thumbnail">
			<i class="icon-beaker"></i>
			<div class="caption">
				<h3>A/B Tests</h3>
				<p>Imagine that you're building a photo discovery app and you want to see which content source resonates the best with your users. A photo adapter can allow you to easily run content A/B tests between Flickr and SmugMug - or any other photo service.</p>
			</div>
		</div>
	</div>
</div>

<div class="row post-image-overview-grid">
	<div class="col-sm-6 col-md-4">
		<div class="thumbnail">
			<i class="icon-tasks"></i>
			<div class="caption">
				<h3>Load Balancing</h3>
				<p>If you've integrated a 3rd-party service into your app, it's likely that you have some sort of API rate limit. To avoid overages and extra fees, you can build an adapter that randomizes which service driver is used for each request.</p>
			</div>
		</div>
	</div>
	<div class="col-sm-6 col-md-4">
		<div class="thumbnail">
			<i class="icon-mobile-phone"></i>
			<div class="caption">
				<h3>Device Optimization</h3>
				<p>Mobile is key for most modern applications. <a href="/blog/2014/03/10/responsive-design-is-not-a-panacea">Adaptive Web Design</a> can allow your app to provide fine-tuned performance and a great user experience across desktop, tablet and mobile.</p>
			</div>
		</div>
	</div>
	<div class="col-sm-6 col-md-4">
		<div class="thumbnail">
			<i class="icon-briefcase"></i>
			<div class="caption">
				<h3>Business Model</h3>
				<p>The adapter pattern is a solid design principle that can lead to tremendous flexibility and power for your application. Not only that, it may also be a great, <a href="https://segment.io">viable business model</a> to consider for your app as well.</p>
			</div>
		</div>
	</div>
</div>


Leveraging the Adapter Pattern
-------------------
The adapter design pattern can be used to allow two or more unrelated or incompatible types to communicate. The adapter defines a standard (a set of common requirements) and acts as a bridge or translator for the unique objects. A [socket wrench](http://sourcemaking.com/design_patterns/adapter) is a simple example of an adapter that provides a common interface for sockets of varying sizes and lengths. In this case, the socket wrench is the "adapter" and the varying sockets are "drivers".

Generally, when writing a software adapter, you should create a base, abstract class to represent the "adapter". This adapter class defines the common requirements that will be applied across all driver child classes. Some programming languages support the concept of an "interface" class - which is another valid way to structure the required driver methods.

Let's reference some code from [Volcano](https://github.com/volcano) as an example:

### The Adapter Class
This base gateway adapter class contains several helper methods (```set()```, ```reset()``` and ```id()```) as well as definitions for the required ```find_one()```, ```create()```, ```update()``` and ```delete()``` CRUD driver methods.
<a href="https://github.com/volcano/billing/blob/master/fuel/app/classes/gateway/model.php">View Code <i class="icon-angle-right"></i></a>

~~~
abstract public function find_one($options = array());

abstract public function create(array $data);

abstract public function update(array $data);

abstract public function delete();
~~~


### The Driver Class
This class extends the parent ```Gateway_Model``` adapter class and contains logic to handle the core CRUD methods for Authorize.net - such as the interacting with the SDK to retrieve a payment method from Authorize.net.
<a href="https://github.com/volcano/billing/blob/master/fuel/app/classes/gateway/authorizenet/paymentmethod.php">View Code <i class="icon-angle-right"></i></a>

~~~
public function find_one($options = array())
{
	...
	
	$request = new AuthorizeNetCIM();
	
	$response = $request->getCustomerPaymentProfile($customer_id, $payment_method_id);
	
	if (!$response->isOk()) {
		Log::error('Unable to retrieve Authorize.net payment method.');
		return null;
	}
	
	$credit_card = $response->xml->paymentProfile->payment->creditCard;
	
	return array(
		'id'          => $response->getPaymentProfileId(),
		'customer_id' => $customer_gateway_id,
		'account'     => '****' . substr($credit_card->cardNumber, -4),
	);
}
~~~

Similar driver classes could be written to provide support for other payment gateways such as PayPal.


Start Designing For Change Today
--------------------------------
You shouldn't [over-architect](https://www.youtube.com/watch?v=0wxyOng0-14) your app and integration points - there's no need to adopt the adapter pattern for every decision you make. **The message here is that designing for change can add great flexibility and power to your application with relatively little effort.** Here are three easy steps you can take when adding a major new piece of functionality to your app:

 1. **Define a Standard:** Figure out what's common across all of the options/3rd-party solutions so you can define a standard (e.g., all shipping solutions provide basic price calculation and label generation).
 2. **Abstract Your Code:** Write a simple wrapper class rather than directly call SDKs and other 3rd-party specific code (e.g., write a Shipping class that then references the UPS SDK so you don't have vendor-specific code all over your app).
 3. **Categorize Your Data:** Name certain elements of your data structures generically (e.g. use a "provider" field to track which 3rd-party / driver the data is related to).


What Do You Think?
---------------------------
As I've described above, the adapter design pattern can have a dramatic impact on your app and development cycle. I'd love to hear your thoughts and experiences with using this approach in your apps. You can find me [@smwxforever](http://twitter.com/smwrxforever).
