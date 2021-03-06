# Physical and informational security of smart containers

## Vision

We envision a decentralized global logistics network, in which transported units (i.e. containers) are autonomous, transiting the network much like packets of information do on the internet. This means that no specific firm needs to retain custody of the container throughout its transit - instead, various players in the ecosystem can assume custody of the self sovereign object, responsive to changes in the complex system. We suspect that enormous gains in the efficiency and reliability of the global logistics network could be achieved by transitioning to this system. Crucially, we do not see this as a replacement of the existing system: current market leaders would still play a profitable role.

This vision is grounded in the observation that emergent informational architectures - blockchains as globally-accessible informational utilities - the need for cooperative organizations (i.e. firms) to provide the coordination services might be eclipsed by the adherence of players in a less-coordinated ecosystem to open protocols defining the schemas of the information required to shepherd a shipment through the logistics chain, along with the use of globally-accessible smart contract code to keep track of a shipment's meta-information.

However, crucial to this system is the assurance to the owners of the goods being shipped that the physical and informational contents of the container cannot be accessed by unauthorized entities.

Here we outline such a system. This is conceptualized and described as it would be implemented on the Ethereum blockchain, but is general enough to be adapted to other public, or private blockchain implementations.

## Physical security

First: containers must only be accessible to authorized actors. We propose several mechanisms to ensure the security of the contents of the container is maintained, as well as possible responses to the eventuality that container integrity is compromised.

First, and most obviously, accessing the contents of the container - by opening the door - could be controlled by a smart lock and biometric identification system. Access rights could be defined within the smart contract instance probably a `Container` contract, rather than `Shipment`. (More on smart contract design later.)

Critically, a container will need to control its own externally-owned account (EOA). This means that it will need its own private key, from which to derive a public key and wallet address. **IF** we can be confident that transactions signed by that private key did indeed originate onboard the container, and that the on-board processors execute code in a secure or uncompromised environment, we believe the system described is possible.

The reason that a smart container needs its own private key is because it will need to invoke smart contract functions, and use the returned values as inputs into algorithms executed within the container's computing environment. A simple implementation of this would include a mapping of `containerID`s to `address`es authorized to access - unlock - the case. (Similarly, a `struct` containing information about the time and place in which that address has the right to access contents could be defined.) We imagine an authorized entity attempting to gain access require the container to invoke a `view` function, checking if they are authorized, and prove to the container that they are who they say they are, likely by transmitting a piece of data signed by that authorized entity's private key. A simple `verify()` function invocation on the container would provide necessary data for the container to open, or not.

It is very easy to see this extended to multisignature access controls (imagining highly sensitive shipments such as weapons / munitions, dual-use goods, high value objects like art or jewelry, or pharmaceuticals). Further, extending the system to include biometric identification hardware on board the container - camera, fingerprint scan, voice recognition - including, perhaps, an on-chain registry where a container could check to ensure that the person submitting credentials through these scanners is authorized. (Clearly some security scheme would need to be adhered to, as this biometric information may be highly sensitive.)

The key take-away: to write the logic required to gain access to these smart containers directly onto the blockchain, to improve system security. Again, this assumes appropriate management of private keys, as well as reliable hardware (locks) - areas worth further investigation, but assumptions worth making in investigating the feasibility of the concept.


      <!-- |=====================================|
      |                EVM                  |
      |                                     |
      |                                     |
      | hasAccess(containerId, address)     |
      |  |--[True]|[False]-|                |
      |  v                 ^                |
      |  |                 |                |
      |==|=================|================|
         |-----------|     | << Checks if actor
                     v     ^    has access rights
|====================|=====|=|
|   Smart Container  |    [|]|--------<--------| << Sends access request,
|                    |       |                 |    signed by private key
|                    |-{open}|       |=========|====|
|                    |-{not} |       |  Authorized  |
|============================|       |    actor     |
                                     |==============| -->


### Users

#### Container

If imbued with a unique cryptographic identity



Challenges:
- Detecting rogue devices (i.e. secrets have been extracted).
-



## Information security

*End-to-end encryption for IoT data with smart contract access controls*

The Internet of Things holds to promise of improving our collective awareness of the world.  Sensors are installed on web-connected devices that are being deployed or installed in places that have hardly been observed; even well-studied locations now are experiencing a greater density and frequency of empirical observation than ever before. Unlocking the information being captured for the public benefit is a moral imperative. This is an effort to understand technical, ethical, economic and political considerations in creating such a system.

## Case Study: Smart Shipping Containers

Given the heterogeneity of the Internet of Things, this research effort will focus on exploring these considerations as applied to transport and logistics networks. The second half of the 20th century saw the rise of a standard unit of shipment: the twenty-foot equivalent unit (TEU). Shipping containers adhere to this standard, and compose a significant proportion of global goods transport. Designed for intermodal transport, shipping containers can hold goods as they move from origin - point of extraction or assembly - to destination - point of sale, including by sea, road, rail and, less frequently, air. (For more on this, see [The Box by Marc Levinson](https://press.princeton.edu/titles/10724.html)).

Improved situational awareness for stakeholders in the global transport supply chain would create numerous opportunities to improve system efficiency, potentially resulting in commercial and environmental benefits ([UN CEFACT Smart Containers White Paper 2019](http://www.unece.org/fileadmin/DAM/cefact/GuidanceMaterials/WhitePaperSmartContainers.pdf)). A transparent and reliable mechanism to ensure the security of the smart container's meta-information is a requirement if such a smart logistics network is to be implemented.

Capturing the value contained in sensor data is the primary incentive for participants in the logistics network ecosystem to invest in smart container technology. Unless regulated to do so, firms - compelled by a profit motive - will need to see the business case for such an investment. Improvements to operational efficiency may offer enough justification to forward-thinking or large actors in the space, but a clearer path to adoption would be to create new revenue opportunities, rather than increase profits by reducing costs. The clearest revenue opportunity created by investing in smart container technology - beyond  possibly up-charging for carrying freight monitored by sensors - is to monetize the data collected by these sensors.

This opportunity is constrained, however, by technical and business realities. Edge sensors are highly limited by intermittent or low bandwidth, and by constraints to computing capacity due to storage / memory or energy consumption. It is infeasible to transmit all of the data collected by edge sensors to cloud servers, where they could be warehoused. Some blend of edge computing, aggregation and sampling will be necessary to retain the value of the information collected within the technical constraints of the system.

Machine learning tasks often are most successfully performed on structured datasets, with cross-comparable observations. This forms the foundation of the case for the establishment of and adherence to an industry-wide protocol for smart container data (as referenced in the UN CEFACT white paper). By ensuring that data collected - even from a single sensor at a single point in spacetime - is interoperable with data collected by competing entities will improve the value of everyone's data. Larger players in the space will have much less incentive to do this, and to open their data, than smaller ones. Part of this enquiry will explore ways to incentivize participation, and / or spell out the case for regulating device owners to do so.

The motivation is our understanding that the emergence of a network of connected sensors is creating at once immense opportunity and risk to issues of human and environmental justice. Smart container data could provide information about environmental conditions around the world at unprecedented levels. Such data, combined with machine learning methods (supervised classification, perhaps) might be used to detect illicit actors utilizing licit commercial logistics networks to traffic contraband or humans. And, questions surrounding the systems for observing shipping containers also apply to those surveilling public and commercial spaces - cameras, satellites, biometric devices, monitors of internet traffic / social networks, etc. These technologies offer the opportunity to improve societies' physical security through early detection of threats to public safety, but carry the risk of abuse by incompetent, unscrupulous or malevolent authorities.

This is an informal outlet for the process that lies behind this research effort. We invite any questions, discourse or critique to our thinking, code, etc.


- Privacy-preserving sensor data access control smart contracts
  - On-chain mechanism for granting and revoking agents' rights to access information, and defining conditions.
    - Identity
    - Location
    - Time
    - Parametric conditions (temperature etc)
