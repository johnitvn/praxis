# Praxis Ontology

The formal concept model for the Praxis reasoning skill.

## Concepts

Core concepts that define the reasoning domain.

See `concepts.yaml` for the machine-readable concept registry.

## Methods

Reasoning methods — procedural approaches to thinking about problems.

See `methods.yaml` for the machine-readable method registry.

## Patterns

Problem-solving patterns — recurring structures for applying methods to problem classes.

See `patterns.yaml` for the machine-readable pattern registry.

## Domains

Problem domains that influence method selection.

See `domains.yaml` for the machine-readable domain registry.

## Relationships

Cross-cutting relationships between concepts, methods, patterns, and domains.

See `relationships.yaml` for the machine-readable relationship registry.

## Usage

The ontology is the source of truth for:

1. **Method selection** — the router uses method metadata to match problems to methods
2. **Composition** — relationship data defines valid method combinations
3. **Discovery** — agents can explore the ontology to find methods they don't know
4. **Extension** — new methods register here with their metadata