.. highlight:: cpp

.. _lang-random:

random()
========

The ``random()`` function generates pseudo-random numbers.

Library Documentation
---------------------

.. FIXME [Breathe] use doxygenfunction when possible

.. cpp:function:: random(long max)

   Same as a call to ``random(0, max)``.

.. cpp:function:: random(long min, long max)

   Generate a pseudo-random number with given lower and upper bounds.

   *Parameters*

   - ``min`` - Lower bound on the returned value, inclusive
   - ``max`` - Upper bound on the returned value, exclusive

   *Returns*: A pseudo-random number in the range [min, max).

Discussion
----------

If it is important for a sequence of values generated by
:ref:`random() <lang-random>` to differ, on subsequent executions of a
sketch, use :ref:`randomSeed() <lang-randomseed>` to initialize the
random number generator with a fairly random input, such as
:ref:`analogRead() <lang-analogread>` on an unconnected pin.

Conversely, it can occasionally be useful to use pseudorandom
sequences that repeat exactly. This can be accomplished by calling
``randomSeed()`` with a fixed number, before starting the random
sequence.

Example
-------

The following sketch initializes the random seed based on an :ref:`ADC
<adc>` reading of pin 0.  If this pin is unconnected, the Sketch
should print different values to the :ref:`serial monitor
<ide-serial-monitor>` each time it is run::

    long randNumber;

    void setup() {
      pinMode(0, INPUT_ANALOG);
      randomSeed(analogRead(0));
    }

    void loop() {
      randNumber = random(300);
      SerialUSB.println(randNumber);

      delay(50);
    }

See Also
--------

-  :ref:`randomSeed() <lang-randomseed>`

.. include:: /arduino-cc-attribution.txt
