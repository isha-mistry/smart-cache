# smart-cache

SmartCache is an automated caching-as-a-service system for Arbitrum Stylus contracts. It allows developers to optimize contract performance directly from their code, without needing to manually interact with the CacheManager through a GUI or CLI.  

Using a simple annotation such as #[auto_cache], developers can indicate which contracts or functions should be evaluated for caching. An off-chain service then handles the entire process: benchmarking gas usage, analyzing cost-efficiency, and submitting a bid through Arbitrum’s CacheManager if the caching decision is financially beneficial.  

This eliminates the need for manual performance monitoring, scripting, or running local infrastructure. SmartCache streamlines caching for developers, allowing them to focus on building their applications while performance is automatically optimized in the background.  

We have already developed a working MVP that includes backend automation and a user dashboard. This dashboard visualizes cache status, gas savings, and fee breakdowns, and allows developers to review or override strategies if needed.  SmartCache charges a small service fee only when caching results in gas savings, creating an incentive-aligned system that benefits both developers and the network.  

MVP - [SmartCache](
)

Demo Video - [SmartCache Demo Video](
)
What innovation or value will your project bring to Arbitrum? What previously unaddressed problems is it solving? Is the project introducing genuinely new mechanisms

SmartCache introduces a new approach to contract caching in the Arbitrum ecosystem by making the caching process automated, developer-native, and outcome-driven. It addresses a key gap in current tooling: the lack of automation and integration in CacheManager usage.

Today, caching on Arbitrum requires developers to manually benchmark gas usage, fetch bid suggestions, evaluate cost-benefit scenarios, and submit transactions using either the CLI or GUI. This process is time-consuming, prone to error, and difficult to scale across multiple contracts or high-frequency deployments.

SmartCache solves these issues by offering:

Declarative caching intent, expressed directly in code through annotations such as #[auto_cache], making caching a part of the development workflow.
Off-chain automation that handles benchmarking, ROI analysis, and bid submissions, removing the need for manual interaction or local infrastructure.
Outcome-based pricing, where developers are only charged a fee when caching leads to measurable gas savings. This ensures alignment with developer interests and reduces risk.
This is a fundamentally new mechanism for interacting with Arbitrum’s CacheManager. It shifts caching from a manual task to a background service that intelligently manages performance optimization.

By making contract caching easier, smarter, and more accessible, SmartCache encourages broader adoption of Arbitrum’s performance features, reduces technical overhead for developers, and supports scalable deployment of Stylus-based applications.

What is the current stage of your project

We are currently at the MVP stage.

We have developed a working prototype that includes the core backend automation system and a web-based user dashboard. The backend benchmarks gas usage for Stylus contracts, fetches suggested bid values from Arbitrum’s CacheManager, and performs return-on-investment analysis to determine whether caching is cost-effective.

The dashboard allows developers to view cache status, historical bid data, estimated gas savings, and fee breakdowns. It also includes functionality for manual overrides and contract monitoring.

Our next steps involve finalizing the developer-facing library and CLI tools, improving the bid submission engine, and onboarding early adopters for testing. We aim to open-source the full system and make it production-ready during the grant period.

Do you have a target audience? If so, which one

Yes, SmartCache is designed primarily for developers and protocol teams building with Stylus on Arbitrum, especially those looking to improve performance without managing caching manually.

Our key target audiences include:

Stylus developers deploying high-performance smart contracts who want caching to be handled automatically.
DeFi protocols, DAOs, and dApps seeking gas-efficient execution at scale, with minimal operational overhead.
Infrastructure and tooling engineers who want to integrate caching logic into CI/CD workflows or deployment pipelines.
Orbit Chain teams are deploying multiple contracts where caching can provide immediate performance improvements.
Hackathon participants and early-stage builders who benefit from having caching handled without needing to learn the full CacheManager flow.
SmartCache is particularly useful for teams that prioritize developer productivity, cost savings, and performance optimization, regardless of project size or technical background.

Do you know about any comparable protocol, event, game, tool or project within the Arbitrum ecosystem

Yes, the most directly comparable tool within the Arbitrum ecosystem is the CacheManager GUI, which allows developers to interact with Arbitrum’s CacheManager contract through a visual dashboard. It enables manual monitoring of contract cache status, bid submissions, and gas savings evaluation.

While the GUI improves usability over the command-line interface, it still requires developers to:

Manually monitor contract performance,
Fetch and assess bid values,
Decide whether caching is worthwhile,
Submit transactions through the interface,
And deploy or access the hosted infrastructure to use the tool.
SmartCache builds on this foundation by offering an automation layer that removes the need for manual interaction. Instead of relying on dashboards or scripts, developers declare caching intent in their code, and SmartCache handles the rest, from performance benchmarking to bid submission.

To our knowledge, no other tool in the Arbitrum ecosystem currently automates caching decisions based on real-time gas data, caching cost analysis, and direct integration with the developer workflow.

We see SmartCache as complementary to existing tools, useful for developers who want full control through the GUI, and essential for teams seeking automated performance optimization at scale.

Have you received a grant from the DAO, Foundation, or any Arbitrum ecosystem related program or conducted any IRL like a hackathon or workshop

No, we have not received any grant for SmartCache from the Arbitrum DAO, Foundation, or any ecosystem-related program so far.

We did apply for the Stylus Sprint program in January 2025, but our proposal was not approved at that time. Based on the feedback we received, we have since revised several aspects of our approach, including clarifying the value proposition, strengthening the team structure, and developing a long-term sustainability plan beyond the grant period.

Here’s the proposal from Stylus Sprint: https://arbitrum.questbook.app/dashboard/?chainId=10&role=builder&proposalId=67812259faef5017a8572fe8&grantId=671a105a2047c84bb8a73770

Have you received a grant from any other entity in other blockchains that are not Arbitrum

We have not received any grant for SmartCache from any other blockchain ecosystem.

The development of SmartCache has been entirely self-funded so far by Lampros DAO. All progress on the MVP, dashboard, and backend automation has been achieved through internal team contributions. We have chosen to focus on Arbitrum from the beginning, particularly due to the opportunities presented by Stylus and the need for performance-focused developer tooling in this ecosystem.

What is the idea/project for which you are applying for a grant

We are applying for a grant to develop SmartCache, an automated caching-as-a-service tool for Arbitrum Stylus smart contracts. SmartCache simplifies the use of Arbitrum’s CacheManager by allowing developers to define caching intent directly in code and automating the entire process of cost analysis and bid submission.

Our goal is to make smart contract caching on Arbitrum automatic, efficient, and accessible, allowing developers to focus on their applications while performance is optimized in the background. SmartCache is designed to improve both developer productivity and the overall efficiency of Stylus-based applications on Arbitrum.

Problem

While the CacheManager helps reduce execution costs, it currently requires manual effort. Developers must:

Monitor gas usage across their contracts,
Retrieve current suggested bid values,
Analyze whether caching would be cost-effective,
Submit bid transactions manually via CLI or GUI,
Maintain infrastructure for tracking bid status and gas savings.
This workflow creates unnecessary friction and doesn’t scale well across large or complex projects.

Our Solution

SmartCache introduces a fully automated caching workflow that starts in the developer’s code and ends with optimized contract execution:

Developers use a simple code annotation (e.g., #[auto_cache]) or configuration file to express caching intent.
Our backend service listens for deployments, benchmarks gas usage, evaluates CacheManager bid recommendations, and determines if caching will be beneficial.
If it is, a caching bid is submitted automatically.
A small service fee is charged only when caching leads to gas savings, ensuring developers pay only when they benefit.
This approach removes the need for manual monitoring or scripting and helps developers optimize performance with minimal effort.

Implementation Plan

We will deliver SmartCache in five key components:

Developer Library (Rust Crate)
Provides #[auto_cache] annotations or a smartcache.toml file to declare caching strategy.
Acts as metadata without affecting contract execution directly.
Backend Automation Engine
Monitors deployments and gas usage.
Calculates suggested bids from the CacheManager.
Runs return-on-investment logic.
Submits bids if cost-effective.
User Dashboard
Displays cache status, gas savings, bidding history, and current fee breakdowns.
Allows optional manual overrides for advanced users.
CLI Tool
Provides lightweight access to caching status, simulation, and manual bid options.
Designed to integrate with developer workflows and CI/CD pipelines.
Security and Wallet Management
Developers can choose to fund bids from their own wallet, a DAO treasury, or a managed SmartCache pool.
Support for multisig or smart wallet configurations.
Current Status

We have already built a working MVP with basic automation and a functioning dashboard. During the grant period, we will:

Finalize the developer library and CLI tools,
Expand backend functionality for reliability and accuracy,
Open source the system with full documentation,
Onboard early users and integrate feedback.
Outline the major deliverables you will obtain with this grant

The grant will support the completion of SmartCache through the following deliverables:

SmartCache Developer Library (Rust Crate)
A lightweight library allowing Stylus developers to mark contracts or functions for caching using annotations like #[auto_cache].
Support for project-level configuration files (e.g., smartcache.toml) to define caching thresholds and strategies.
Designed to integrate smoothly with existing Stylus project structures and CI/CD pipelines.
Automated Cache Evaluation Engine
A backend service that:
Parses deployed contracts and identifies caching candidates.
Simulates gas usage with and without caching.
Fetches live CacheManager bid recommendations.
Calculates return on investment based on projected usage.
Automated Bid Submission System
Logic to place cache bids only when cost savings outweigh the bid amount.
Secure wallet integration for bid transactions, with support for:
Developer-owned wallets,
DAO treasuries,
Managed SmartCache fund.
Web-Based User Dashboard (v1)
A live interface to:
View contract caching status and historical bid data,
Track gas savings and fee breakdowns,
Manually override or simulate caching actions.
Initial version is already live; grant support will complete integration and polish the UI.
SmartCache CLI Tool
A command-line utility to:
Analyze contract caching potential,
Simulate gas savings,
View live caching status,
Submit or cancel caching bids without requiring the GUI or custom scripts.
Outcome-Based Billing Engine
A system to charge a small fee only when caching results in measurable gas savings.
Configurable fee rates and detailed usage tracking, ensuring transparency and fair pricing.
Developer Onboarding & Open Source Launch
Public release of the core system under an open-source license.
Full documentation for library, CLI, API, and dashboard usage.
Tutorials and example integrations to support adoption.
Support for pilot testing with early Stylus developers and Orbit teams.
Please explain how your idea/project aligns with the Arbitrum ecosystem goals

SmartCache supports several key priorities of the Arbitrum ecosystem, particularly around developer enablement, performance infrastructure, and scalable DeFi growth. By automating a critical but currently manual process, contract caching, it directly improves both developer experience and network efficiency.

Enhancing Developer Productivity and Tooling
Arbitrum Stylus enables developers to build high-performance smart contracts using WebAssembly (WASM), but managing caching still requires manual steps. SmartCache simplifies this by allowing caching to be declared in code and handled automatically.

This:

Reduces technical overhead,
Lowers the barrier to entry for newer developers,
Encourages broader adoption of Stylus and Arbitrum-native tooling.
By making advanced performance features more accessible, SmartCache strengthens Arbitrum’s position as a developer-first ecosystem.

Improving Network Efficiency and Supporting DeFi Scalability
Cached contracts on Arbitrum are cheaper and faster to execute. This is especially important for high-throughput DeFi applications where every unit of gas saved contributes to better UX and lower costs for users.

SmartCache ensures that only contracts with clear cost-saving potential are cached, optimizing how CacheManager resources are used and promoting more efficient application design.

This supports Arbitrum’s goal of DeFi dominance by making it easier for protocols to scale affordably without compromising on performance.

Enabling Ecosystem Growth and Orbit Chain Participation
As new teams and builders join the Arbitrum ecosystem, particularly through Orbit chains, the need for developer-friendly infrastructure becomes even more important.

SmartCache:

Reduces the need for custom infrastructure or manual optimization,
Makes caching accessible to teams with limited DevOps capacity,
Supports multi-chain deployments by providing chain-agnostic automation.
This aligns with Arbitrum’s broader mission of expanding its ecosystem by empowering more developers to build and deploy efficiently.

Creating a Sustainable and Incentive-Aligned Service Layer
SmartCache introduces a new type of infrastructure primitive: performance optimization as a service. It aligns incentives between developers, network performance, and service providers by charging only when value is created (i.e., when gas savings are realized).

This model is scalable, sustainable, and creates long-term value across the ecosystem.

What is your requested grant

20,000 USD.

Website

https://stylus-cache-manager.vercel.app/

Please provide a detailed breakdown of the budget in term of utilizations, costs and other relevant information

https://docs.google.com/spreadsheets/d/1w0AnZ35R6AlNuVXdK3ik8IKl75eJBPdJETfcFcR49Lk/edit?usp=sharing

Provide a list of the milestones, with the USD amount of the grant associated to it, the deliverables that will be provided, and the estimated completion time

Milestone 1: Finalize Backend Automation Service

Deliverables:

Develop the off-chain service to benchmark gas usage for Stylus contracts.
Integrate with Arbitrum CacheManager for retrieving bid suggestions and submitting caching bids.
Implement the ROI analysis engine to determine caching efficiency.
Grant Allocation: $5,000

Estimated Completion: June 15, 2025

Milestone 2: Developer Dashboard (v1 Full Integration)

Deliverables:

Build a real-time dashboard showing:
Cache status, bid history, gas savings, and fee breakdown.
Implement manual override functionality for advanced users.
Set up basic authentication and contract registration flow.
Grant Allocation: $4,000

Estimated Completion: July 15, 2025

Milestone 3: SmartCache CLI Tool & Project Config Support

Deliverables:

Create a CLI tool to:
Analyze caching potential,
Trigger and check caching status,
Integrate config file support (e.g., smartcache.toml).
Grant Allocation: $3,000

Estimated Completion: August 10, 2025

Milestone 4: SmartCache Library (Developer Crate)

Deliverables:

Publish a Rust crate supporting #[auto_cache] annotations.
Include build-time parsing or metadata extraction.
Provide integration guides and code examples.
Grant Allocation: $4,000

Estimated Completion: August 31, 2025

Milestone 5: Open-Source Release, Documentation & Pilot Testing

Deliverables:

Open-source all key components (library, CLI, backend).
Publish complete documentation and tutorials.
Onboard 3+ pilot users or projects.
Collect early feedback to inform future development.
Grant Allocation: $4,000

Estimated Completion: September 30, 2025

Are milestones clearly defined, time-bound, and measurable with quantitative metrics where applicable? What are your reference KPI, if applicable, for each milestone

Yes, all SmartCache milestones are structured to be clearly defined, time-bound, and measurable. Below is a breakdown of each milestone along with its respective KPIs:

Milestone 1: Finalize Backend Automation Service

Estimated Completion: June 15, 2025

KPIs:

Complete benchmarking for at least 3 Stylus contracts (cached vs uncached).
Successfully integrate with CacheManager to fetch live suggested bid values.
Implement ROI logic to calculate expected savings.
Submit at least 1 cache bid automatically through the backend.
Internal logs and test reports verifying bid logic execution.
Measurement: Output logs, internal dashboard records, and bid transactions on-chain

Milestone 2: Developer Dashboard (v1 Full Integration)

Estimated Completion: July 15, 2025

KPIs:

Publicly accessible UI with user login and contract registration.
Track cache status and gas savings for at least 3 deployed contracts.
Display bidding history and fee breakdown in real-time.
Manual override functionality active and tested.
Hosted link and screen recording as proof of functionality.
Measurement: Live dashboard demo, screen recordings, hosted link

Milestone 3: SmartCache CLI Tool & Project Config Support

Estimated Completion: August 10, 2025

KPIs:

CLI supports: analyze, status, and trigger-bid commands.
Functional config file (smartcache.toml) parsed and applied in 2 example projects.
Use CLI to submit at least 1 successful cache bid.
User testing logs confirming full CLI flow.
Measurement: CLI command logs, config file samples, user testing outputs

Milestone 4: SmartCache Library (Developer Crate)

Estimated Completion: August 31, 2025

KPIs:

Publish Rust crate with support for #[auto_cache] annotation.
Integrate with backend to recognize and register caching intent.
Demonstrate usage in at least 2 real Stylus contracts.
Include working code examples and published documentation.
Measurement: Crate code, test project using it, deployment logs

Milestone 5: Open-Source Release, Documentation & Pilot Testing

Estimated Completion: September 30, 2025

KPIs:

All components (library, CLI, backend) open-sourced on GitHub.
Publish full documentation and 1 demo tutorial (written and video).
Onboard a minimum of 3 pilot users or teams.
Submit at least 3 cache bids from pilot projects via SmartCache.
Collect feedback from 2 pilot users to inform future iterations.
Measurement: GitHub repo, README, documentation site, pilot reports

What is the estimated maximum time for the completion of the project

Estimated Completion Date: September 30, 2025

How should the Arbitrum community measure the success of this grant

The success of the SmartCache grant will be measured by its adoption, impact on developer experience, demonstrated gas savings, and alignment with Arbitrum’s broader ecosystem goals.

First, the tool will demonstrate meaningful gas savings. For at least three Stylus contracts, caching through SmartCache will result in net reductions in gas costs. These savings will be visible on the public dashboard, alongside real-time data showing the number of cache bids submitted and any service fees charged, only in cases where savings were realized.

Second, SmartCache will improve the developer experience. Developers will be able to adopt and benefit from caching without interacting with the GUI or writing custom scripts. Feedback from early adopters, especially those who integrate SmartCache into CI/CD pipelines, will reflect the ease of use and value added.

Third, the project will contribute to open-source tooling within Arbitrum. All components will be released under an open-source license. Full documentation and tutorials will also be published for public reference.

Lastly, SmartCache will contribute to Orbit Chain and ecosystem expansion. Community recognition of SmartCache as a reliable, automated alternative to manual CacheManager usage will signal broader impact and long-term relevance.

What is the economic plan for maintaining operations or continuing the growth of your project after the grant period

SmartCache is built on a sustainable and outcome-based business model designed to ensure long-term viability beyond the grant period.

The core economic structure is simple: developers or protocols are only charged when caching results in actual gas savings. If caching does not generate a net benefit, no bid is submitted and no fee is charged. When caching proves cost-effective, a small service fee is applied as a percentage of the gas saved.

This model ensures that all stakeholders benefit:

Developers save time and money while improving contract performance.
The SmartCache system earns revenue only when it delivers measurable value.
The network benefits from broader caching adoption, which leads to more efficient contract execution.
Because the fee structure is tied directly to performance, SmartCache naturally scales with usage. As more developers adopt the tool and more contracts are optimized, the service becomes increasingly self-sustaining. This model also allows us to reinvest in future improvements, developer support, and feature expansion.

Over time, we also plan to introduce optional services, such as enterprise integrations, custom caching strategies for DAOs, and managed infrastructure for Orbit Chains, that can further support the project’s growth and maintenance.

Market Needs: For developers building apps and interfaces, what specific challenges or opportunities do they face in Arbitrum

Arbitrum offers a highly scalable environment for smart contract development, and the introduction of Stylus has opened new possibilities for high-performance applications. However, developers still face several practical challenges when it comes to optimizing performance and managing infrastructure efficiently.

One major challenge is the complexity of interacting with the CacheManager. While the CacheManager provides significant performance benefits, it currently requires developers to:

Manually benchmark gas usage across contracts,
Retrieve and analyze suggested bid values,
Determine whether caching is economically viable,
Submit caching bids via scripts or dashboards,
And maintain infrastructure for monitoring and tracking results.
This process is time-consuming, error-prone, and not easily scalable, especially for teams managing multiple contracts, participating in hackathons, or deploying to Orbit chains with minimal tooling support.

There is also a lack of automation in performance optimization. Developers are left to monitor and manage caching manually, which creates friction and delays in improving the user experience. This gap results in missed opportunities to lower gas costs, improve execution speeds, and enhance the responsiveness of applications.

Additionally, as more projects adopt Stylus and deploy on Orbit chains, the demand for simplified tooling and plug-and-play infrastructure is growing. Many developers, especially those in early-stage teams or working with limited resources, need solutions that are easy to integrate, require minimal configuration, and work reliably across environments.

At the same time, Arbitrum presents a strong opportunity. With increasing adoption of Stylus and the expansion of Orbit chains, there is a clear need and market for tools like SmartCache that lower technical barriers and improve performance without increasing operational overhead.

By addressing these challenges, SmartCache helps unlock the full potential of the Arbitrum ecosystem for developers building the next generation of dApps.

Composability: How can your proposed developer tooling (existing or new) facilitate seamless interaction between different protocols and tools built on Arbitrum, the Nova ecosystem and other Orbit chains

SmartCache is designed from the ground up to be modular, extensible, and compatible with the broader Arbitrum ecosystem, including Arbitrum One, Nova, and custom Orbit chains. Its architecture supports seamless integration with different developer tools, contract deployment environments, and protocol-level workflows.

Cross-Chain Compatibility

The SmartCache backend is chain-agnostic and interacts with Arbitrum’s CacheManager through standard RPC-compatible endpoints. This allows it to support:

Arbitrum One for general-purpose dApps,
Arbitrum Nova for low-cost, high-throughput use cases,
Custom Orbit chains that deploy their own instance of the CacheManager.
We plan to include dynamic chain configuration, enabling the system to detect and route caching logic based on the specific deployment environment, so developers can manage caching across chains using a single interface.

Integration with Developer Toolchains

SmartCache is designed to work seamlessly with existing tools used by Arbitrum developers. This includes:

Stylus project workflows, including cargo stylus,
CI/CD systems where caching decisions can be automated as part of deployment,
Infrastructure scripts that manage deployments across different environments.
The CLI tool and configuration files (e.g., smartcache.toml) allow for easy customization without locking developers into a specific interface or workflow.

Protocol-Level Composability

For protocols with multiple contracts or modular systems, such as DeFi apps, DAOs, or games, SmartCache provides a unified caching strategy. It enables:

Centralized management of caching decisions across all deployed contracts,
Reusable configuration logic across dev, staging, and production environments,
Shared optimization strategies within multi-contract architectures.
Compatibility with Orbit Tooling and Infrastructure

As Orbit chains grow and diversify, many will require performance tools that do not rely on centralized dashboards or manual setup. SmartCache offers Orbit builders:

A managed service or self-hostable caching engine,
Easy integration into custom deployment stacks,
Infrastructure-light caching automation to improve performance out of the box.
Adoption: If your grant focuses on a Growth or Orbit Chain developer tool, how would you ensure its widespread adoption within the developer community

To ensure widespread adoption of SmartCache within the Arbitrum developer community, especially across Orbit Chains, we are taking a multi-pronged approach focused on ease of use, direct value, and ecosystem integration.

1. Frictionless Developer Experience

SmartCache is intentionally built to integrate seamlessly into the existing developer workflow. Developers can signal caching intent using a simple annotation like #[auto_cache] or define caching rules in a smartcache.toml file. This design ensures that SmartCache feels native and requires no new interfaces or steep learning curves.

The CLI tool and optional dashboard provide intuitive access to performance data, while caching decisions are handled automatically by the backend. This low-friction approach makes the tool appealing to both experienced developers and newcomers building on Stylus.

2. Orbit Chain Enablement

We will actively collaborate with Orbit Chain developers to offer SmartCache as a default performance layer for their contracts. This includes:

Supporting self-hosted and managed deployments of SmartCache tailored to Orbit environments.
Providing pre-integrated modules that can be included in Orbit chain templates or starter kits.
Helping Orbit teams implement caching for key contracts from day one, demonstrating real performance improvements without added operational cost.
By removing infrastructure burdens and making caching automatic, we make it easier for smaller teams and new builders to optimize performance from the start.

3. Early Pilots and Ecosystem Partnerships

We plan to onboard an initial group of 3–5 early adopters, including Stylus-based dApps and DAO infrastructure teams. These pilot projects will:

Serve as live case studies showcasing gas savings and automation benefits.
Provide early feedback that helps refine the tool and guide future development.
Act as reference implementations for other teams exploring SmartCache adoption.
We will also explore integration opportunities with existing Arbitrum tooling providers and grant recipients to expand visibility and encourage bundling with other infrastructure offerings.

4. Educational Content and Developer Activation

To drive awareness and lower the adoption barrier, we will publish:

Step-by-step tutorials and quickstart guides,
Examples comparing contract performance before and after SmartCache integration,
Video walkthroughs and use-case demonstrations.
We will also engage with the community through Discord, the Arbitrum Forum, hackathons, Twitter Spaces, and AMAs to answer questions, showcase updates, and gather community input.

5. Open Source, Extensibility, and Community Ownership

SmartCache will be released as an open-source project, encouraging transparency and extensibility. This will allow protocol teams to audit and adapt the tool to their needs, while also opening the door to external contributions and long-term community stewardship.

The open nature of the project helps build trust and ensures that SmartCache can evolve in line with the ecosystem’s priorities.

If working on Orbit Chain Onboarding and Tooling: How would you adapt your existing developer tooling (or propose a new tool) to simplify building applications on custom Arbitrum Layer 3 chains (Orbit Chains)

We will adapt SmartCache to simplify Orbit Chain development by:

Making it Orbit-ready and deploy-friendly,
Supporting Orbit-specific caching flows out of the box,
Providing infrastructure and educational support for L3 builders,
And enabling Orbit operators to run SmartCache as part of their default toolchain.
Instagram

N/A.

If applying for a growth oriented grant: Please provide success metrics for the grant with milestone-oriented disbursements

N/A.

LinkedIn

N/A.

Discord

@eupho.7

Others

GitHub - https://github.com/meetpaladiya44/Stylus_Cache_Manager; MVP - https://stylus-cache-manager.vercel.app/; Demo Video - https://drive.google.com/file/d/18ItQgPtlwlTPFgySay-2bwUSS8XF3veO/view?usp=sharing

Do you acknowledge that your team will be subject to a KYC requirement

Yes

Do you acknowledge that, in case of approval, you will have to provide a report at the completion of the grant and, three months later, complete a survey about your experience

Yes

Team experience and completeness

Our team is fully assembled and well-positioned to execute this grant without the need for additional hires. Each member contributes specific technical and operational strengths that directly support the successful delivery of the proposed milestones.

Team Members and Roles

Euphoria – Project Lead & Strategy

Euphoria leads the team and oversees project coordination, community engagement, and alignment with Arbitrum governance goals. With a background in management and over 18 months of active contribution in the Arbitrum DAO, he has led multiple successful governance-focused projects, including the Arbitrum Governance and Development Initiative and LTIPP research bounties. As a Top 50 active delegate in the Arbitrum DAO under Lampros DAO, he ensures effective communication between the project, community, and stakeholders.

Forum Profile - https://forum.arbitrum.foundation/u/euphoria/summary
Twitter Profile - https://x.com/Euphoria_0077
LinkedIn Profile - https://www.linkedin.com/in/sagarverma7/
Purvik Panchal – Backend Automation Lead

Purvik specializes in backend architecture and automation. He has worked directly with Stylus, deploying CacheManager contracts, implementing gas benchmarking flows, and automating ROI-based bid submissions. His experience in SDK development, off-chain scripting, and infrastructure automation forms the core of SmartCache’s logic layer.

https://github.com/purvik6062/
https://www.linkedin.com/in/iampurvikpanchal/
Meet Paladiya – Full-stack & Infrastructure Developer

Meet built the full SmartCache MVP, including the frontend dashboard and backend system. He set up Arbitrum Nitro nodes, handled Stylus deployments, and integrated cache evaluation into a seamless UI/UX. His experience ensures reliable connectivity between the smart contract layer and SmartCache’s automation engine.

https://github.com/meetpaladiya44/
https://www.linkedin.com/in/meetpaladiya44/
Isha Mistry – Frontend Engineer & Developer Experience

Isha is responsible for the SmartCache frontend and UX. She has previously worked on platforms like Chora Club and Maxxit, where she built responsive UIs and integrated APIs for real-time data. Her focus on usability helps bridge the complexity of backend logic with simple, accessible developer tooling.

https://github.com/isha-mistry
https://www.linkedin.com/in/isha-mistry-51b414239/
Bhumi Sadariya – Smart Contract Developer & DeFi Logic Specialist

Bhumi brings deep experience in DeFi tooling and smart contract architecture. She has worked on systems like Omnikit and Smart Disperse, contributing to vault logic, token routing, and protocol safety mechanisms. Her knowledge supports the performance optimization goals of SmartCache from a contract-level perspective.

https://github.com/0xBhumi?tab=overview&from=2025-04-01&to=2025-04-26
Davinci – Technical Advisor

Davinci will provide technical mentorship and strategic oversight. With experience as a project manager and former co-founder of https://www.neerx.in/, he currently leads the https://speedrun-stylus-react-app.vercel.app/ initiative. He brings deep hands-on experience in Stylus, smart contract development, and platform scaling. Davinci guides architectural decisions, code quality, and Stylus-specific integration to ensure the project aligns with Arbitrum’s technical standards.

https://in.linkedin.com/in/abhishek-dubey-128aa0126?original_referer=
https://github.com/AbhishekDubey013
