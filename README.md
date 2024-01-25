Analysis of 5G-ProSe-AKA
==================

Organization
------------

 - `5G_ProSe_CP_AKA`: analysis of 5G-ProSe-CP-AKA as specified in TS 33.503 v18.0.0. The folder includes the CP-AKA model, the privacy model of CP-AKA, 'oracle' file to verify the model, all finded attacks (including '*.spthy' file and attack trace).
 - `5G_ProSe_CP_AKA_fix`: We also give a model implementing our fixes. The fixes consist of all countermeasures in section 5.3. The main difference between two fixes  can be referred to '*two countermeasures for NI on RSC with the Remote UE in terms of the HN'* in section 5.3.  The modified derived process of AT_MAC corresponds to  5G_ProSe_CP_AKA_fix1.  The added confirmation message from the Relay to the HN corresponds to  5G_ProSe_CP_AKA_fix2.  
 - `5G_ProSe_UP_AKA`: analysis of 5G-ProSe-UP-AKA as specified in TS 33.503 v18.0.0. The folder includes the UP-AKA model, the privacy model of UP-AKA, 'oracle' file to verify the model, all finded attacks (including '*.spthy' file and attack trace).
 - `5G_ProSe_UP_AKA_fix`: We also give a model implementing our fix. The fixes consist of all countermeasures in section 5.3.

How to reproduce the results about verified lemmas
--------------------------------------------------------------------

This analysis uses version 1.4.0 of the [Tamarin-prover](https://github.com/tamarin-prover/tamarin-prover). Instructions for the installation and usage can be found in chapter 2 of the [manual](https://tamarin-prover.github.io/manual/book/002_installation.html).

Due to the complexity of the proofs, oracle files that guide the proof search are required. 

The verified lemmas about authentication and secrecy properties can be proven automatically using our oracle, the results can be reproduced by the following command:

`tamarin-prover interactive --heuristic=o --oracle=5G_ProSe_CP_AKA.oracle 5G_ProSe_CP_AKA.spthy`

For the verified  lemmas about privacy properties can be  proven automatically using our oracle, the results can be reproduced by the following command:

`tamarin-prover interactive --diff --heuristic=o --oracle=5G_Prose_CP_AKA_privacy.oracle 5G_Prose_CP_AKA_privacy.spthy` 

Note1:  Once an interactive Tamarin session is launched, one can select and load the appropriate Tamarin file  and navigate through the model and the different lemmas.

Note2: The lemmas can also be verified in the command mode and they can be timed. More details can be referred in the manual.

## How to reproduce the results about stored attacks

Lemmas that are annotated with 'attack' cannot be disproven automatically. We have provided these attacks into the folder '5G_ProSe_CP_AKA_attack' and '5G_ProSe_CP_AKA_privacy_attack'. 

The stored attacks about authentication and secrecy properties can be reloaded with the tool by the following command:

`tamarin-prover interactive  *.spthy`

The stored attacks about privacy properties can be reloaded with the tool by the following command:

`tamarin-prover interactive --diff *.spthy`





