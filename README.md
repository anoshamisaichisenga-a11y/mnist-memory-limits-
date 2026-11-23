# mnist-memory-limits

Neural Networks or Template Matching under tight memory limits (MNIST).
Authors: Anoshamisa-I Chisenga (ID_81197), Mariia Ivanova (ID_79862)

## Protocol (fixed before final experiments)
- Data: MNIST via Keras (60,000 train, 10,000 test), pixels scaled to [0,1]
- Sizes: 28x28, 14x14, 7x7 by block averaging (2x2 and 4x4)
- Methods: template matching (nearest centroid), NN0 (softmax regression), NN16 (16 ReLU hidden neurons)
- Training: Adam, default learning rate, 5 epochs, batch 128, 10 seeds (0-9), no tuning on the test set
- Decision rule: paired bootstrap (10,000 resamples), 95% interval of the accuracy difference.
  A beats B if the whole interval is above +1 percentage point; equivalent if inside +/-1 pp; else inconclusive.
- Supporting test: McNemar exact per seed, Holm correction across 9 comparisons
- Memory: stored values x bytes (float32 4, int8 1); runtime RAM = input + activations; worst case = both; fit rule <= 50% of chip memory
