
![[pendulum_et_tests_lines.webp|963]]
Here I testes SAV on the inverted pendulum balance task.
As ET I compared the reward distribution of a moving window with one that was sampled at the beginning.
- No retrain gave bad performance after the changes
- Not stop train had problems with collapsing results in the stationary areas (Probably to few samples of bad actions)

- Depending of the size of the change the time to detect was shorter. Large change -> faster detection
- Relearning was triggered and resulted in a bad behavior at the beginning of the training. No transfer was done. So this was expected!