## APL 

An overview into the value system that kdb/q has inherited from APL, see Aaron Hsu's video, "Design Patterns vs Anti pattern in APL by Aaron W Hsu at FnConf17".

    https://confengine.com/functional-conf-2017/proposal/4620/design-patterns-vs-anti-pattern-in-apl
    Skip the first few minutes due to audio problems:
        https://www.youtube.com/watch?v=v7Mt0GYHU9A&t=3m15s

At 40m50s, Hsu contrasts "APL Practice" vs "Accepted Practice"

    Brevity vs Verbosity
    Macro vs Micro
    Transparency vs Abstraction
    Idioms vs Libraries
    Data vs Control Flow
    Structure vs Names
    Implicit vs Explicit
    Syntax vs Semantics

These differences make APL / q very productive in the hands of a skilled developer.  However the more traditional patterns have established themselves for a reason.


Here are some forces which stand in the way of using q in the “APL style” in Production in large organizations:

    Zero Developer Access to Production
        ZDAP is a specialization of "Separation of Duties".   It is intended to prevent developers from tampering with Production systems to perpetrate fraud or accidentally destabilize the system.
        It falls upon the Production Management / DevOps team to determine the cause of the error and whether to escalate.  Often, the support team is not deeply steeped in q.  Instead, they consult “run books” for the list of steps to restore smooth functioning.
        Much of the core functionality in q.k such as .Q.chk[…] reports nonspecific error messages which assume access to the console to decode the root cause.  This is not feasible in a ZDAP environment and that core functionality must be reimplemented with more detailed logging.
    Organizational Silos
        Wherever there’s an organizational boundary, there’s a chance that technology choices will be different on each side.
        Some parts of the organization may choose to interact with kdb+ only through client APIs and develop the barest minimum of q familiarity.
        There may be separate teams who support kdb vs Python (for example) with different deployment permissions.  Therefore, cross-language plugins may need to be buildable in a way that allows deployment in two pieces.
    Versioning
        Even if multiple teams choose q, they may evolve their components / systems on different timelines.  A module loading system needs to allow for this.
        Plugins need to be binary compatible.  Although the C ABI is stable, the C++ ABI is not.  Compiler upgrades or library evolution can result in a process that fails to start up, or worse yet, mysteriously crashes or otherwise misbehaves.
    Security
        Out of the box, “that which is not forbidden is permitted”.  Given that kdb instances in financial services organizations may hold confidential data, the narrative needs to be flipped to, “that which is not permitted is forbidden”.
        As the number of users grows, access controls need to become finer grained to provide data on a “need to know” basis.  At the most basic level, there will be a division between those with “administrative” access and those who do not.  However, there are other entitlements which may need to be enforced based on role (eg. may view P&L) or client coverage.
    Complexity
        For systems with hundreds of thousands of lines of code, it’s simply unrealistic for every developer to know all of them in detail.  Specialization naturally occurs.  Abstraction becomes necessary.
        Short names inevitably lead to collisions resulting in confusion.