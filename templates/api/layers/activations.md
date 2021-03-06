# Layer activation functions


## Usage of activations

Activations can either be used through an `Activation` layer, or through the `activation` argument supported by all forward layers:

```python
model.add(layers.Dense(64, activation=activations.relu))
```

This is equivalent to:

```python
from tensorflow.keras import layers
from tensorflow.keras import activations

model.add(layers.Dense(64))
model.add(layers.Activation(activations.relu))
```

All built-in activations may also be passed via their string identifier:

```python
model.add(layers.Dense(64, activation='relu'))
```

---

## Available activations


{{autogenerated}}


---


## Creating custom activations

You can also use a TensorFlow callable as an activation
(in this case it should take a tensor and return a tensor of the same shape and dtype):

```python
model.add(layers.Dense(64, activation=tf.nn.tanh))
```

---

## About "advanced activation" layers

Activations that are more complex than a simple TensorFlow function (eg. learnable activations, which maintain a state)
are available as [Advanced Activation layers](/api/layers/advanced_activations),
and can be found in the module `tf.keras.layers.advanced_activations`. These include `PReLU` and `LeakyReLU`.
If you need a custom activation that requires a state, you should implement it as a custom layer.

Note that you should *not* pass activation layers instances as the `activation` argument of a layer.
They're meant to be used just like regular layers, e.g.:

```python
x = layers.Dense(10)(x)
x = layers.LeakyReLU()(x)
```


