D
===

============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== 
`A <A.html>`_  `B <B.html>`_  `C <C.html>`_  `D <D.html>`_  `E <E.html>`_  `F <F.html>`_  `G <G.html>`_  `H <H.html>`_  `I <I.html>`_  `J <J.html>`_  `K <K.html>`_  `L <L.html>`_  `M <M.html>`_  `N <N.html>`_  `O <O.html>`_  `P <P.html>`_  `Q <Q.html>`_  `R <R.html>`_  `S <S.html>`_  `T <T.html>`_  `U <U.html>`_  `V <V.html>`_  `W <W.html>`_  `X <X.html>`_  `Y <Y.html>`_  `Z <Z.html>`_  
============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== ============== 

dApp
^^^^
A distributed application (dApp) is a set of `smart contracts <S.html#smart_contract>`_.

Delegation rate
^^^^^^^^^^^^^^^
Node operators (`validators <V.html#validator>`_) define a commission that they take in exchange for providing staking services. This commission is represented as a percentage of the rewards that the node operator retains for their services.

Delegator
^^^^^^^^^
Delegators are users who participate in the platform's security by delegating their tokens to validators (which adds to their weight) and collecting a part of the rewards proportional to their delegations, net of a cut ("delegation rate") that is collected by the validator.

Deploy
^^^^^^
An **external client to node** message that includes two transactions:

#. **payment transaction** - executed to buy gas for the execution of main **transaction**
#. **main transaction** - the actual piece of software that does the actual processing changing the global state

The **external client** sends a deploy hoping that the network will execute the main transaction against the blockchain.

Devnet
^^^^^^
A version of the network that can be used for development. Users can run nodes and connect to a public trusted node, validators/node operators can spin up nodes, and developers can deploy and execute smart contracts.
