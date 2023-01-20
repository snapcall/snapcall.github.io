---
title: "How did we build Video Software Architecture for SnapCall"
date: 2022-01-20
---

## Identifying the Goals and Requirements

This step was essential in SnapCall software architecture design process. It involves understanding the needs and expectations of the target customers and stakeholders, as well as the objectives of the business. This information is used to guide the design and development of the software, ensuring that it meets the needs of the users and aligns with the overall business strategy.

The process of identifying goals and requirements starts by analysing the market and understanding the targeted customers. This includes researching the competition, identifying customer pain points, and gathering feedback through interviews and surveys. During last 2 years, a video platform helping online transactions became obvious. The gathered information from our customers, tech and business partnerships help us to create user personas and use cases that represent the different types of users and their needs. These user personas and use cases are then used to guide the design of the software, ensuring that it addresses the needs of the targeted customers.

We also defined a set of measurable and specific goals and objectives for the product, such as key performance indicators (KPIs) and business objectives. It's important that the goals and objectives are measurable, so that progress can be tracked and the product can be continuously improved. By clearly identifying the goals and requirements of SnapCall video platform, the development team was able to design a product that aligns with the overall business strategy, and addresses the pain points and needs of market.

## Designing the High-Level Software Architecture

Designing the high-level software architecture is a crucial step in SnapCall platform development process, as it provided the foundation for the entire system. It involved identifying the main components of the software, their interactions, and the overall structure of the system. A well-designed high-level software architecture help us to ensure that the system is easy to maintain, scalable, and adapted to changing requirements.

One key aspect of SnapCall design in the high-level software architecture was to establish the main Video service of the system, also called "Streamer". We’ve got two options : use an existing video API (Twilio, Vonage …) or build our own stack. For costs scalability and tech constraints we’ve chose the second option. The video “streamer” micro service was designed to be loosely coupled and highly cohesive. This means that the different others micro services have minimal dependencies on each other, allowing for more flexibility and easier maintenance in the future. All services are also focused on a specific functionality : load balancing, API, recording... Making the system more maintainable and easier to understand.

The chosen high-level architecture was also aligned with the goals and requirements of SnapCall platform. It also consider the scalability and performance aspects, taking into account the expected number of users, data volumes, and the need to support concurrent access. Additionally, the architecture also consider aspects such as security, reliability, and availability. Designing the high-level software architecture of SnapCall product required a deep understanding of the business, technical and operational requirements of the product and a balance between different considerations to deliver a robust and flexible architecture.

## Choosing the Right Technologies and Frameworks

Choosing the right technologies and frameworks is an important step in our software development process, as it has a significant impact on the success of SnapCall product. The technologies and frameworks used in the development of video real time platform can affect everything from performance and scalability to ease of maintenance and integration with other systems.

When choosing technologies and frameworks, we considered the specific needs and requirements of SnapCall, as well as the skillset of the development team. SnapCall development team has a strong experience and expertise in Javascript and C/C++ , as this helped us to ensure that the software is developed efficiently and effectively. It was also important to evaluate the scalability, performance and security of the chosen technology. Very naturally our backends micro services are all based on Node.js server environment. For frontend side we used the React library coupled to Next.js framework. For a concrete example, SnapCall video streamers are based on Node.js server running a fork of MediaSoup C/C++ library.

It was also important to consider the long-term maintainability of the software. Technologies and frameworks that are widely used and have a large and active community are more beneficial in terms of getting help and finding solutions to problems. Priority was to select frameworks and libraries that are well-documented, secure, and have a good track record of performance and scalability are preferred. Choosing the right technologies and frameworks was a crucial decision and was based on a balance of technical, operational and business considerations.

## Building and Testing the Software

Building and testing the software has been a critical step in our software development process, as it ensures that the all is functioning as expected and meets the requirements and goals of the SnapCall product. Our building and testing process is running through Github actions, it has been broken down into several stages, including unit testing, integration testing then building.

Unit testing is the process of testing individual units or components of our code. This typically involves creating automated tests that are run against the code to ensure that it is functioning as expected. Unit tests has been designed to be fast and easy to run, those tests are automatically executed using Jest Framework, each time a developer open a pull request in Github  with fresh code. As long as the tests are not OK, the PR can’t be merged. Building is finally executing during our release process, still using Github actions.

Finally, a good practice for building and testing the software is to automate the process as much as possible, as this can greatly increase the speed, efficiency and accuracy of the testing process. It also allows for easy regression testing and continuous integration, which is essential for keeping the software reliable and maintainable over time.

## Deployment and Scalability

Deployment and scalability are very important aspects of SnapCall software development process, as they ensure that the SnapCall video platform is available and able to handle the demands of an increasing user base.

Deployment is the process of making SnapCall product available to users, by installing and configuring it on our AWS cloud environment. In SaaS business, it's important to have a robust deployment process in place to ensure that the software is deployed quickly and efficiently, with minimal disruption to the user base. This often involves automating the deployment process as much as possible, We fully automatised this process using tools like AWS ECS service and Docker. Each time we deploy new version of our video streamer, Docker containers with new product release are launched and handle new video requests, during this time new connections  are stopped by load balancers to docker instance with old version of code. Thanks to this process, we are able to deploy new versions of our service without any disruptions to users.  

Scalability is the ability of SnapCall platform to handle an increasing number of users and requests. For SnapCall, scalability is important because it ensures that the product can continue to perform well as the user base grows. It's important to design the architecture of the software with scalability in mind, and to regularly test and monitor the performance of the system under load to identify and address any potential bottlenecks. Techniques such as load balancing, horizontal scaling, and caching helped us to improve scalability.

Finally, It is important to also be ready to scale quickly, as the SnapCall  may experience sudden growth, and it should be possible to add more resources on short notice. One way of achieving this is to make use of AWS services that offer automatic scaling, which can be activated as needed. Each time a Docker instance running one of SnapCall micro service reach a high level of CPU, new one is automatically started.

## Continual Monitoring and Improvement

Continual monitoring and improvement is an essential part of our software development process, as it ensures that the SnapCall platform is functioning as expected and that any issues are identified and addressed quickly.

Monitoring give us the ability of gathering data and metrics on the performance, usage and behavior of the services. This includes metrics such as bandwidth, response time, error rates, and resource usage. These data are used to identify performance bottlenecks, track user engagement, and measure the impact of changes to the product. By monitoring the system, it's possible to identify potential issues early on and take steps to address them before they become major problems.

Improvement help us to make changes to the software based on the data collected from monitoring. This can include changes to the software architecture, adding new features, or improving the performance of the system. By continuously monitoring and improving the product, it's possible to ensure that the SnapCall product is meeting the needs of the users, and that the product is aligned with the overall business strategy.

It's also important to have a system in place to manage and prioritize the improvements suggested by the monitoring. One way of achieving this is to use a system like a Jira board, which allows the development team to see the status of different improvements and to prioritize them according to their impact with the product team and the business. Continual monitoring and improvement is essential to keep the SnapCall reliable, maintainable, and competitive in the market.
