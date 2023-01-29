---
title: self-service infrastructure platform
tags: [SSP, Cloud, protocol, VMware, Self Service Infrastructure, linux, automation-api]
style: fill
color: light
description: Self-service is an approach where users access resources to find solutions on their own without requiring assistance from a service representative.
---

Source: 
1. [https://nebulon.com/](https://nebulon.com/blog/what-is-self-service-infrastructure/#:~:text=does%20it%20mean%3F-,What%20is%20a%20self%2Dservice%20infrastructure%3F,depending%20on%20IT%20operations%20teams.)
2. [https://github.com/komalali/self-service-platyform](https://github.com/komalali/self-service-platyform)
3. [https://github.com/pulumi/automation-api-examples](https://github.com/pulumi/automation-api-examples)
4. [https://www.pulumi.com/blog/automation-api/](https://www.pulumi.com/blog/automation-api/) 

# self-service infrastructure

**What is a self-service infrastructure?**

With a self-service infrastructure product teams and application owners can rapidly and reliably provision and maintain their application infrastructure without depending on IT operations teams.

This is important because in traditional infrastructure settings, the application owner usually relies on the IT administrator to carve out a slice of infrastructure before they can deploy a new application or scale an existing application. This can take a significant amount of time depending on how many infrastructure teams must be involved as provisioning requires a series of management actions independent administrative and security domains, often by different teams.

What if the application owner were able to control when and how much infrastructure was needed without relying on an IT administrator? That would undoubtedly be much simpler. Plus, the infrastructure team wouldn’t need to worry as the application owner would just pull from a list of curated templates which provide guardrails for application owners, making the entire process error-proof.

{% include elements/figure.html image="https://www.hashicorp.com/img/products/terraform/use-cases/self-service-infrastructure/self-service-challenge.png?fit=max&fm=webp&q=80&w=2000" caption="Developers have to wait for operators to provision and assign dedicated infrastructure" %}

**What does a self-service infrastructure provide?**

Anyone can say that their product is simpler to manage, but the only way to achieve ultimate management simplicity is by leveraging the ease and simplicity of the public cloud on-prem and self-service infrastructure provisioning is a part of that.

**Faster initial time-to-deployment**

The key to achieving this is through an API-first approach which allows the application owner to control every single aspect of their data and that starts with provisioning. I mentioned earlier that in a true self-service model, application owners have access to a service catalog of application templates that they can choose from to make the entire process error-proof. That means application owners can pick the template they want and simply deploy their application.

We compare the idea of self-service infrastructure provisioning to a buffet menu. First, the application owners can pick the application they want to deploy: Kubernetes, VMware, Linux, etc. Next, they pick the number of servers they need: 4, 8, etc. Then, voila! They have their own set of infrastructure provisioned for their selected application at their selected scale.

**Ongoing operational simplicity with easy automation**

Not only do self-service models make deploying applications error-proof, but they also drastically reduce the ongoing complexity of managing application infrastructure for application owners. The reason being that provisioning infrastructure is complex—there really is no other way to put it. There is a reason why infrastructure requires specific administrators: storage, server, network, etc. Storage administrators, specifically have years of experience navigating the obstacles that provisioning storage can pose, and it is a skill most application owners don’t need (or want) to have. This makes automating legacy 3-tier architectures a brittle process as it is highly dependent on each environment’s particular combination of storage array, switch type, and host application server.

With a true self-service provisioning model, application owners can also enjoy the benefits of easy automation. They can easily extend their provisioning workflows and, in as little as 15 minutes, deploy a production-ready Kubernetes cluster. Plus, application owners don’t need to worry about the most basic infrastructure maintenance operations as they’re done automatically. This includes keeping your management stack tailored to the scale of your environment, keeping it up to date, and ensuring that the right people are informed about infrastructure issues. It’s all possible with automation and self-service infrastructure provisioning.


{% include elements/figure.html image="https://www.hashicorp.com/img/products/terraform/use-cases/self-service-infrastructure/self-service-solution.png?fit=max&fm=webp&q=80&w=2000" caption="Library of versioned and validated infrastructure templates to be consumed for on-demand provisioning." %}


## Python example Application to handle SSP

**Self Service Infrastructure Platyform**

This application represents a starting point for how you might develop a self-service infrastructure platform on top of [Pulumi](https://pulumi.com)'s [Automation API](https://www.pulumi.com/blog/automation-api/).

In this case, we've used Python, [Flask](https://flask.palletsprojects.com/en/1.1.x/) and [Jinja](https://jinja.palletsprojects.com/en/2.11.x/) templates to create a web portal that allows users to deploy their own infrastructure.

One resource that we expose are static websites, which you can deploy either by passing in a URL to an HTML file or by manually typing out the content. We've exposed all of the CRUD operations, so you can `update` and `delete` your websites as well.

This idea is just a starting point for how you might build out your own infrastructure platform. The static website resource is fully developed, but databases, virtual machines and VPCs are not yet coded to completion.

Alternatively, you could expose this functionality as a [REST API](https://github.com/pulumi/automation-api-examples/tree/main/python/pulumi_over_http), allowing deployments via CLI in addition to a web interface.

Pulumi's Automation API allows you to abstract away all of the "cloud stuff" that your users might not care to know, and bring them just the details they need, at the click of a button. The possibilities are endless!

**WARNING**: This is just a demo! I have not followed _any_ security best-practices, so please don't deploy this thing to production.

**Instructions**

To run this example you'll need a few pre-reqs:

1. A Pulumi CLI installation ([v3.0.0](https://www.pulumi.com/docs/get-started/install/versions/) or later)
2. The AWS CLI, with appropriate credentials.

First, set up your virtual environment:

1. ```shell
   $ python3 -m venv venv
   ```
2. ```shell
   $ venv/bin/python3 -m pip install --upgrade pip
   ```
3. ```shell
   $ venv/bin/pip install -r requirements.txt
   ```

In a terminal window, run the HTTP server that uses Automation API. It will also stream update logs:

```bash
$ FLASK_RUN_PORT=1337 FLASK_ENV=development FLASK_APP=app PULUMI_ORG=[your-org-name] venv/bin/flask run
 * Serving Flask app "app" (lazy loading)
 * Environment: development
 * Debug mode: on
 * Running on http://127.0.0.1:1337/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 150-956-496
```

Then, in your browser, navigate to `localhost:1337` and you should see a page matching the image below. Click around and start exploring!
