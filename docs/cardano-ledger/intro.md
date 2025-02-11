# Introduction

This document is a formal specification of the functionality of the
ledger on the Cardano blockchain.
This includes the blockchain layer determining what is a valid block,
but does not include any concurrency issues such as chain selection. The
details of the background and the larger context for the design
decisions formalized in this document are presented in Appendix
Section [shelley-delegation-design](#shelley-delegation-design).

In this document, we present the most important properties that any
implementation of the ledger must have. Specifically, we model the
following aspects of the functionality of the ledger on the blockchain:

In defining Cardano, we are concerned with the means to construct
inductive datatypes satisfying some validity conditions. For example, we
wish to consider when a sequence of transactions forms a valid *ledger*,
or a sequence of blocks forms a valid *chain*.

This document describes the methods we use to define such validity
conditions and how they result in the construction of valid states. In
particular, we define inference rules for operations on a blockchain as
a specification of the blockchain layer of Cardano. A block validity
definition is given, which is accompanied by *small-step operational
semantics* inference rules.

The idea behind this document is to formalise what it means for a new
block, to be added to the blockchain, to be valid. Unless a new block is
valid, it cannot be added to the blockchain and thereby extend it. This
is needed for a system that is subscribed to the blockchain and keeps a
copy of it locally.

Each block is made up of transactions and this specification models the
*conditions* that the different parts of a transaction must fulfill so
that they can extend a ledger, which is represented here as a list of
transactions. In particular, we model the following aspects:

Preservation of value

:   relationship between the total value of input and outputs in a new
    transaction, and the unspent outputs.

Witnesses

:   authentication of parts of the transaction data by means of
    cryptographic entities (such as signatures and private keys)
    contained in these transactions.

Delegation

:   validity of delegation certificates, which delegate block-signing
    rights.

Update validation

:   voting mechanism which captures the identification of the voters,
    and the participants that can post update proposals.

Stake

:   staking rights associated to an addresses.

```{=html}
<!-- -->
```

Preservation of value

:   Every coin in the system must be accounted for, and the total amount
    is unchanged by every transaction and epoch change. In particular,
    every coin is accounted for by exactly one of the following
    categories:

    -   Circulation (UTxO)

    -   Deposit pot

    -   Fee pot

    -   Reserves (monetary expansion)

    -   Rewards (account addresses)

    -   Treasury

Witnesses

:   Authentication of parts of the transaction data by means of
    cryptographic entities (such as signatures and private keys)
    contained in these transactions.

Delegation

:   Validity of delegation certificates, which delegate block-signing
    rights.

Stake

:   Staking rights associated to an address.

Rewards

:   Reward calculation and distribution.

Updates

:   The update mechanism for Shelley protocol parameters and software.

While the blockchain protocol is a reactive system that is driven by the
arrival of blocks causing updates to the ledger, the formal description
is a collection of rules that compose a static description of what a
*valid ledger* is. A valid ledger state can only be reached by applying
a sequence of inference rules and any valid ledger state is reachable by
applying some sequence of these rules. The specifics of the semantics we
use to define and apply the rules we present in this document are
explained in detail in [@small-step-semantics] (this document will
really help the reader's understanding of the contents of this
specification).

The structure of the rules that we give here is such that their
application is deterministic. That is, given a specific initial state
and relevant environmental constants, there is no ambiguity about which
rule should be applied at any given time (i.e. which state transition is
allowed to take place). This property ensures that the specification is
totally precise --- no choice is left to the implementor and any two
implementations must behave the same when it comes to deciding whether a
block is valid.
