---
layout: post
title: Cluster Kubernetes - IaC
excerpt: "This project deploys a Kubernetes cluster using Terraform and Amazon EKS..."
date: 2024-10-21
author: Juan Camilo JS
---
**Kubernetes** is a very useful tool for deploying and orchestrating containers. In this short post, I make use of various DevOps tools to deploy a **Kubernetes** cluster in the **AWS** cloud via **infrastructure as code - IaC** using **Terraform** with **Helm** charts.

First, I create a **Virtual Private Cloud - VPC** on **AWS**. It is possible to create it using the **AWS CloudFormation** service. To do this, I have reused the template obtained from the [_Linux Academy repository_](https://github.com/linuxacademy/eks-deep-dive-2019/blob/master/1-2-Configuring-Cluster/amazon-eks-vpc-sample.yaml).

This is the network infrastructure architecture.



To define a valid network address in CIDR format in the VPC I used private IP address blocks that follow the `RFC 1918` standard. These private IP ranges include:

>**`10.0.0.0.0/8`** (from **`10.0.0.0.0`** to **`10.255.255.255`**) \
**`172.16.0.0/12`** (from **`172.16.0.0.0`** to **`172.31.255.255.255`**) \
**`192.168.0.0/16`** (from **`192.168.0.0.0`** to **`192.168.255.255`**) 

The mask determines how many IP addresses will be available. For example:

>**`/8`** offers about 16 million IP addresses. \
**`/16`** offers about 65,000 IP addresses. \
**`/24`** offers 256 IP addresses. \
**`/28`** offers 16 IP addresses.

In **AWS**, 3 to 5 IPs are typically reserved for internal cloud uses, such as: Network Address, AWS Internal Gateway, AWS DNS Service, Broadcast Address, among others.
The main address range for the VPC (**`172.21.0.0/16`**) is divided into specific subnets. In this case, with **`/24`** mask for each public subnet. This allows to organize the IP address space for different subnets within the VPC.






{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].


[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
