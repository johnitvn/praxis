# Network Analysis

## Purpose
Analyze the structure of relationships in a network to identify key nodes, community structure, propagation paths, and vulnerabilities that are invisible when examining nodes in isolation.

## When to Use
- When the problem is about how something spreads through a connected system (information, influence, disease, failure).
- When you need to identify which nodes are most central, influential, or vulnerable.
- When the problem involves relationships that are not hierarchical but form a web of connections.
- When you need to find communities, clusters, or structural holes in a connected system.
- When you are asked to assess the resilience or fragility of a network to targeted or random failure.

## When Not to Use
- When relationships are strictly hierarchical (a tree structure) — organizational analysis methods may be more appropriate.
- When you have no data about connections between entities.
- When the network is trivially small (fewer than 5-10 nodes) and the structure is obvious by inspection.

## Problem Signals
- "How does X spread through the organization?"
- "Who are the key influencers or gatekeepers?"
- "Why does information flow well in one part of the organization but not another?"
- "Which node, if removed, would fragment the network?"
- "Are there distinct communities or clusters in this system?"

## Inputs
- A list of nodes (entities, people, components).
- A list of edges (connections, relationships, flows) between nodes.
- Edge attributes if relevant: direction, weight/strength, type of relationship.
- The question being asked about the network (centrality, community, propagation, resilience).

## Procedure
1. Define nodes and edges. Be explicit about what counts as a connection. A connection must be a meaningful relationship — not just co-occurrence.
2. Characterize the network topology. Is it random, scale-free, small-world, or modular? This determines the network's basic behavior.
3. Compute centrality measures relevant to the question:
   - **Degree centrality**: number of direct connections. Identifies local hubs.
   - **Betweenness centrality**: how often a node lies on the shortest path between others. Identifies gatekeepers and bottlenecks.
   - **Closeness centrality**: how quickly a node can reach all others. Identifies efficient broadcasters.
   - **Eigenvector centrality**: connections to well-connected nodes. Identifies influential nodes.
   Choose the measure that matches the question. Do not compute all of them mechanically.
4. Detect communities if the question involves clustering. Look for groups of nodes that are more connected to each other than to the rest of the network. Note structural holes — gaps between communities where no connections exist.
5. Assess propagation. If the question involves spread, trace how something would move through the network. Consider: does the network accelerate or inhibit propagation? Where are the choke points?
6. Assess resilience. If the question involves failure, test: what happens if the most central nodes are removed? Does the network fragment or stay connected?
7. Synthesize findings. Answer the original question using the network metrics and structure. Do not just report numbers — explain what they mean for the system.

## Output
- A characterization of the network topology.
- Relevant centrality rankings with interpretation.
- Community structure (if applicable).
- Propagation or resilience assessment (if applicable).
- A clear answer to the original question, grounded in the network structure.

## Strengths
- Reveals structural importance that is invisible from node attributes alone.
- Provides quantitative measures (centrality, modularity) that support decisions.
- Identifies vulnerabilities and leverage points that component-level analysis misses.

## Limitations
- Requires complete or representative network data; missing edges distort metrics.
- A static snapshot may miss temporal dynamics — networks change over time.
- Centrality is sensitive to boundary choices: including or excluding nodes changes rankings.

## Common Failure Modes
- **Computing every metric and reporting none**: the agent calculates degree, betweenness, closeness, and eigenvector centrality for every node, producing a data dump without interpretation. Choose the metric that answers the question.
- **Ignoring edge meaning**: treating all connections as equal when they differ in strength, direction, or type. A "follow" on social media is not the same as a trust relationship.
- **Boundary blindness**: failing to acknowledge that the network boundary is a choice and that nodes just outside the boundary may be the most important ones.
- **Centrality as importance**: assuming that a high centrality score means a node is "important" without defining what important means in context.

## Verification
- Is the network boundary explicitly stated and justified?
- Are the chosen centrality measures justified by the question being asked?
- Does the output interpret the metrics, not just report them?
- Is there a clear answer to the original question?

## Combine With
- **systems-thinking**: for the broader system context that the network is embedded in.
- **feedback-analysis**: when the network is the substrate through which feedback loops operate.
- **risk-analysis**: for assessing how failures propagate through the network.
- **emergence-analysis**: when the network structure produces emergent macro-level patterns.

## Conflicts With
- **hierarchical analysis**: treating the system as a tree when it is a web.
- **aggregate statistics**: reducing the network to averages (e.g., average degree) that hide the structural features that matter.

## Example

**Problem**: A project team wants to improve knowledge sharing. Some members seem to have all the information while others are repeatedly out of the loop.

**Network**: Nodes are team members. Edges are "who do you go to for technical questions?" (directed).

**Analysis**:
- Topology: small-world with a few central hubs.
- Degree centrality (in-degree): Alice (8), Bob (7) are the go-to people. They are bottlenecks.
- Betweenness centrality: Carol is low on degree but high on betweenness — she connects the frontend and backend clusters. If Carol leaves, the two groups stop communicating.
- Community detection: two clear clusters (frontend, backend) with only Carol bridging them.

**Synthesis**: The knowledge-sharing problem is structural. Alice and Bob are overloaded hubs. Carol is a single point of failure between communities. The frontend and backend clusters are isolated from each other.

**Recommendations**: (1) Document what Alice and Bob know to reduce dependency on them. (2) Create additional bridges between frontend and backend so Carol is not the only one. (3) Rotate cross-team knowledge-sharing sessions.

## Selection Metadata
```
id: network-analysis
category: systems
best_for: [relational problems, propagation, influence mapping, community detection, resilience assessment]
requires: [nodes, edges, connection definition, topology]
produces: [centrality measures, community structure, propagation paths, resilience assessment]
strengths: [captures relational structure, identifies key nodes, reveals vulnerabilities]
limitations: [requires complete network data, static snapshots, boundary sensitivity]
combine_with: [systems-thinking, feedback-analysis, risk-analysis, emergence-analysis]
avoid_when: [relationships are not network-like, data is unavailable, network is trivially small]
```