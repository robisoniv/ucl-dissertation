# WORKING TITLE: Edge computing, connected sensors, and smart contracts: prototyping and modeling a connected logistics network

*Outline, Dissertation, MSc Spatial Data Science and Visulalisation*

**UCL Bartlett Centre for Advanced Spatial Analysis**

Cover page, Acknowledgements.

1. Introduction

Frame ethical context. Define key terms. Literature review. Concise problem statement. Research questions. Hypotheses. Outline approach.

2. Enabling Technologies

Wireless data transfer. Empirical sensors. Localization - GPS, FOAM. Asymmetric cryptography - encrypt-decrypt, sign-verify. Hashing algorithms and usage (checksums, Merkle trees). Homomorphic cryptography. Proxy re-encryption. Trusted hardware. Blockchains and distributed ledgers. Smart contracts / EVM. Public blockchains (mainly Ethereum). Private blockchains (probably mainly Corda, possibly Hyperledger).

3. Concept / System Design

Outline a feasible system for a distributed store of data collected by connected sensors, with access controls governed by a DAO.








4. Agent-based models

Implement, visualize and analyze the outputs of agent-based models designed to simulate the behavior of such a network of connected sensors operating at various scales, based on different governance schemes (single authority (centralized), oligarchic authority (private blockchain), decentralized, fractal federated).

The research question these simulations are designed to explore needs to be significantly constrained prior to model design and implementation.

- OPP Protocol
- Visualizing outputs (web visualization?)
- Analysis of data recorded from model execution / parameter sweeps.

Implement in Python? Maybe even Javascript? (https://github.com/backspaces/agentscript? https://github.com/wybo/agentbase? https://github.com/noncomputable/AgentMaps?)

5. Transition: Ethical and Pragmatic Considerations

Discuss the ethics of the system and possible implications of its emergence. Outline several pragmatic considerations affecting its implementation, including:

- Political. Domestic (which countries?) and international. Propose Ricardian treaties.
- Economic. Key question - incentivizing private actors to share data (Lloyd's List Singapore panel on smart ports). Identify key industries and actors to convert in order to lead adoption, and ongoing initiatives to do so.
- Behavioral. Why would people adopt a sub-optimal system?

Propose DAO shepherds.

6. Conclusion

Appendices.