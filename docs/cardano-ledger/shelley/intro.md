This document is a formal specification of the functionality of the
ledger on the blockchain. This includes the blockchain layer determining
what is a valid block, but does not include any concurrency issues such
as chain selection. The details of the background and the larger context
for the design decisions formalized in this document are presented
in [@shelley-delegation-design].

In this document, we present the most important properties that any
implementation of the ledger must have. Specifically, we model the
following aspects of the functionality of the ledger on the blockchain:

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
