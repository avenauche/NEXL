# NEXL — Natural Expression Language

> **NEXL** is a plain-text language for expressing intent, ambiguity, branching, sequence, and relationships in a way that is natural for humans and precise for AI.

NEXL is designed for:

* AI users writing **precise prompts**
* Developers expressing **logic, flow, and decisions** in text
* Tool users working with **text-based grammars** (Mermaid, sequence diagrams, graphs)

Primary goals:

* Human-first, paper-friendly notation
* Low cognitive load
* Low token usage for AI
* Explicit handling of ambiguity

---

## Repository Structure (suggested)

```
/
├── README.md        # Overview + quick start
├── SPEC.md          # Formal NEXL specification
├── LICENSE          # MIT
├── examples/
│   ├── decision.nxl
│   ├── flow.nxl
│   └── relations.nxl
```

File extensions:

* **.nxl** (canonical)
* **.nexl** (accepted alias)

---

## Core Philosophy

* Punctuation and symbols are **semantic operators**, not decoration
* Ambiguity must be **explicitly marked**, not hidden in prose
* Resolution happens via **branching**, not assumption
* Structure is preferred over verbosity

---

## Lexical Conventions

### 1. Headings and Scope

```
Introduction:
- Context:
-- Problem:
```

Rules:

* A trailing `:` opens a scope
* Heading text is used as-is
* Hierarchy is defined by leading `-`
* Indentation is visual only

---

### 2. Ordered Lists (Sequence)

```
1. step one
2. step two
```

Rules:

* Numbers represent **execution order**
* Order is local to the current scope

#### Decimal Steps (Drill-down / Insertion)

```
1. main step
1.0 inserted prerequisite
1.1 sub-step
```

Meaning:

* Decimals refine or expand a step
* `x.0` indicates a retroactively added, higher-priority prerequisite

---

### 3. Ambiguity Marker

```
Should I eat today?
```

Rules:

* `?` marks uncertainty
* Demands resolution
* Must be followed by branching

---

### 4. Branching (Alternatives)

```
Should I eat today?
=> yes
=> no
```

Rules:

* `=>` introduces an alternative path
* Sibling branches are mutually exclusive unless stated
* No implied order between branches

#### Branch with Consequences

```
=> no
    1. fasting
    2. weight loss
```

#### Extracted Branch (Preferred over deep nesting)

```
2. weight loss -> Risks of Weight Loss
```

---

### 5. Sequence vs Relationship

#### Sequence (Temporal)

```
action 1 > action 2
```

Meaning:

* Ordered execution

#### Relationship (Structural)

```
User -> Account
```

Meaning:

* Directed association
* No time implied

---

### 6. Certainty Encoding

```
battery - bulb
battery -- bulb
```

Meaning:

* `-` : confirmed connection
* `--` : tentative / assumed connection

---

### 7. Tables (CSV-style)

```
name,role,priority
login,auth,high
logout,auth,low
```

Rules:

* First row is header by default
* No ASCII borders
* Contiguous block = table

---

### 8. Comments

```
---> this is a comment
--> also a comment
```

Rules:

* Comment lines are ignored by parsers

---

## Minimal Example

```
Decision:
Should I eat today?
=> yes
    1. eat soon
    2. gain calories
=> no
    1. fasting
    2. weight loss -> Risks of Weight Loss
```

---

## Design Principles

* Prefer **shallow trees** over deep nesting
* Extract complex branches into named subtrees
* Use symbols consistently; never overload meaning

---

## License

MIT License

---

## Status

* Version: **v0.1 (draft)**
* Stable core semantics
* Open to extensions without breaking changes

---

> NEXL is intended to sit between human thought and machine reasoning — minimal, explicit, and precise.
