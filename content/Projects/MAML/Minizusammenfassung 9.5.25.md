MARL mit LIAM auf Predator Prey klappt.
Embedding der Opponent trajectory basierend auf lokalen Observations.
![[pradetor_prey_eval.webp|605]]![[pradetor_prey.webp|634]]

Ich habe an dem Algo etwas rum experimentiert und bessere Performance bekommen. Aber ich glaube das ist nicht so wichtig. War hautsächlich HP tuning und habe mal cyclic CVAEs anstatt CAE ausprobiert.
Das Problem was ich dabei hauptsächlich hatte war, dass die Embeddings nicht mehr interpretierbar wurden und ich da echt nicht mehr weiter wusste, was da schief geht. 
![[LIAM improvement.webp|868]]

Ähnliches wurde schon ausprobiert: LIAM, CALM, GSCU, MacPro
Auch auf online changes in envs während der evaluation. References sind hier: FastTap
Aber changes während dem training und der evaluation. Sowie explicites nutzen der segment Struktur der changes hab ich nicht gefunden.
Hatte auf Predator Prey geschaut wie es sich auswirkt wenn man die opponents austaucht (In expectation 4 Mal in einer Episode).
Die Performance hatte sich nicht wirklich geändert. Darum hatte ich da erst mal nicht weiter gemacht. Es kann natürlich sein, dass dies an dem Env liegt und man da noch mal drauf schauen kann. Vor allem, wenn man mehr Infos braucht um die Opponent Strategie vorherzusagen kann das vielleicht doch noch mal wichtig werden. Also da kann man noch Zeit investieren wenn man mag. hatte da auch schon etwas mehr geschaut aber war nicht vielversprechend.
Also hier die Plots von: In episode change vs constant opponent:
![[piecewise_collision_eval.webp|784]]![[piecewise_eval.webp|794]]
Nicht wundern die Scalen sind anders, weil die Episoden länger geworden sind um auch sinnvolle changes haben zu können. 200 statt 50 time steps.