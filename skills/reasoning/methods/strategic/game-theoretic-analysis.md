# Game-Theoretic Analysis

## Purpose
Model and predict outcomes in situations where the result of each participant's choice depends on the choices of other participants, all of whom are reasoning strategically about each other. The method identifies equilibrium strategies, reveals the logic of interdependent decisions, and exposes incentives that produce individually rational but collectively suboptimal outcomes.

## When to Use
- When the outcome of your decision depends on what others do, and they are also trying to anticipate your decision
- When analyzing competitive dynamics: pricing, market entry, product positioning, bidding, negotiation
- When designing mechanisms, incentives, or rules where you need to predict how rational actors will respond
- When you observe a pattern of behavior that seems individually irrational and suspect a strategic explanation
- When you need to identify whether cooperation is sustainable or whether defection is inevitable

## When Not to Use
- When decisions are independent: your payoff does not depend on others' choices (use expected-utility or multi-criteria-decision)
- When other actors are not strategic: they do not anticipate or respond to your choices (use standard forecasting)
- When the strategic interaction is so complex that the game cannot be formalized in a tractable way
- When the assumption of rationality is grossly violated (e.g., in contexts driven by ideology, panic, or systemic irrationality)
- When the goal is empathy or user understanding, not strategic prediction (use design-thinking)

## Problem Signals
- The user describes a situation with multiple "players" whose decisions affect each other
- The problem involves pricing, bidding, negotiation, standards competition, or market entry
- The user says "if we do X, they'll respond with Y" or "we need to think about what they'll do"
- The problem has the structure of a prisoner's dilemma, coordination game, or chicken game
- The user is designing a policy, mechanism, or incentive system and wants to predict behavioral responses

## Inputs
- A set of players (decision makers) who are strategically interdependent
- For each player, a set of available strategies (actions, choices)
- A payoff function: for each combination of strategies (one per player), the payoff to each player
- The information structure: what each player knows when they make their decision (simultaneous, sequential, asymmetric)
- The time structure: is the game one-shot, finitely repeated, or infinitely repeated?
- Optionally, the ability of players to communicate, commit, or form binding agreements

## Procedure
1. Identify the players. Only include actors whose choices meaningfully affect and are affected by others. Do not model agencies as players if they are not strategic.
2. Define the strategy space for each player. Simplify: group similar strategies and eliminate obviously dominated ones.
3. Specify the payoff structure. For each strategy combination, what does each player get? Use ordinal rankings (best to worst) if cardinal payoffs are unavailable. Be explicit about what goes into the payoff: profit, market share, utility, reputation, etc.
4. Determine the information and timing structure. Is it simultaneous-move or sequential? Do players have private information? Can they observe past moves?
5. Solve for equilibria:
   - For simultaneous games: find Nash equilibria by checking each strategy profile for unilateral deviation incentives. In 2x2 games, use best-response analysis.
   - For sequential games: use backward induction. Start at the final decision node and work backward, assuming optimal play at each stage.
   - For repeated games: identify whether cooperation can be sustained by trigger strategies (grim trigger, tit-for-tat) given the discount factor.
   - For games with incomplete information: use Bayesian Nash equilibrium or, if signaling is possible, perfect Bayesian equilibrium.
6. If multiple equilibria exist, apply refinement criteria: Pareto dominance, risk dominance, payoff dominance, or focal points (Schelling points).
7. Analyze the strategic implications: what does the equilibrium structure imply about the likely outcome? Who has the advantage? Is there a first-mover advantage? Is the outcome efficient or is there a prisoner's dilemma?
8. Test for robustness: would the conclusion change if a player had slightly different payoffs or if a strategy was added?

## Output
- The game structure: players, strategies, payoffs, and timing
- The equilibrium (or equilibria) identified, with the solution method used
- Strategic implications: who wins, what incentives drive behavior, whether the outcome is efficient
- If multiple equilibria exist: which are most plausible and why
- Sensitivity: what changes in the payoff structure would alter the equilibrium

## Strengths
- Models strategic interdependence explicitly, capturing dynamics that single-agent decision methods miss
- Explains why rational individuals can produce collectively irrational outcomes (prisoner's dilemma, tragedy of the commons)
- Provides predictions that can be tested against observed behavior
- Backward induction gives clear prescriptions for sequential decisions
- The equilibrium concept provides a consistent standard: if everyone is playing an equilibrium, no one has an incentive to change

## Limitations
- The rationality assumption is strong: real actors make mistakes, have bounded rationality, and are influenced by emotions and social norms
- Equilibrium multiplicity is common and selection criteria are often ad hoc
- Real payoffs are often unknown or private information, making the analysis sensitive to assumptions
- The model is only as good as the strategy space; omitted strategies can change the equilibrium
- Does not handle learning or adaptation well unless embedded in an evolutionary or learning framework
- The assumption of common knowledge of rationality is demanding and often violated in practice

## Common Failure Modes
- Modeling too many players or strategies, creating a game too complex to solve or interpret
- Assuming Nash equilibrium is predictive when the game is played once and players lack experience
- Ignoring the possibility of correlated equilibria or communication when players can coordinate
- Treating equilibrium as a normative recommendation rather than a predictive or diagnostic tool
- Omitting the "do nothing" or "status quo" strategy, which is often the equilibrium
- Forgetting that the analyst is often a player: the analysis itself can change behavior if it becomes known
- Assuming zero-sum when the game is actually positive-sum or negative-sum

## Verification
- Check that each player's strategy set is complete and includes the option to maintain the status quo
- Verify that the payoffs are consistent: if A is better than B and B is better than C, A should be better than C
- Confirm that the identified equilibrium is indeed a Nash equilibrium: no player can unilaterally improve by switching
- Test whether the equilibrium survives the addition of a plausible strategy that was not in the original set
- If the game is repeated, verify that the discount factor is high enough to sustain the proposed equilibrium

## Combine With
- scenario-planning: to generate the possible states of the world that affect payoffs
- decision-under-uncertainty: when the game structure is known but the opponent's type or payoffs are uncertain
- strategic-analysis: to identify the competitive landscape before modeling specific interactions
- option-reasoning: when the game involves sequential commitments and the value of flexibility
- risk-analysis: when the equilibrium involves catastrophic outcomes for some players

## Conflicts With
- design-thinking: assumes empathy and user-centeredness; game theory assumes strategic self-interest
- dialectic: assumes truth-seeking through dialogue; game theory assumes strategic signaling
- multi-criteria-decision: evaluates options independently; game theory evaluates them interdependently

## Example
Two ride-sharing companies are deciding whether to enter a new city. If both enter, price competition drives profits to near zero for both. If only one enters, that company earns a monopoly profit of $100M. If neither enters, both earn $0. The payoff matrix is a classic anti-coordination game (chicken) with two pure-strategy Nash equilibria: (Enter, Stay Out) and (Stay Out, Enter). A mixed-strategy equilibrium also exists. Which equilibrium is selected depends on who can commit first. If Company A can pre-announce its entry and incur a sunk cost (building driver infrastructure), the game becomes sequential: Company A moves first, and backward induction shows that Company A enters and Company B stays out. The analysis reveals that the strategic value of commitment through sunk costs outweighs the value of waiting. The recommendation: invest in visible, irreversible commitments before the competitor does.

## Selection Metadata
```
id: game-theoretic-analysis
category: strategic
best_for: [interdependent-decisions, competitive-situations, mechanism-design]
requires: [players, strategies, payoffs, information-structure]
produces: [equilibrium-strategies, strategic-implications, sensitivity-findings]
strengths: [models-interdependence, predicts-strategic-behavior, explains-counterintuitive-outcomes]
limitations: [rationality-assumptions, equilibrium-multiplicity, payoff-uncertainty]
combine_with: [scenario-planning, decision-under-uncertainty, strategic-analysis, option-reasoning]
avoid_when: [decisions-are-independent, players-are-not-strategic, game-is-too-complex-to-formalize]
```