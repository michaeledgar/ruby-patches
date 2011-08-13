# Cuts: Transparent Classes

**Author:** Peter Vanbroekhoven

## What it does

Demonstration patches for the ruby source v1.8.2 (it may work for other versions, not for 1.9, requires gperf) to add the notion of transparent subclass or cut for short. This works as follows:

```
  class A
    def m
      "A"
    end
  end

  __cut__ C1 < A
    def m
      "C1" + super + "C1"
    end
  end

  C2 = Cut.new(A) {
    def m
      "C2" + super + "C2"
    end
  }

  A.new.m # => "C2C1AC1C2"
```

A cut can cut:

    * a class
    * a cut
    * a module

However cutting a module only works when adding -DSTORE_CUTS_IN_EXTRA_FIELD to the CFLAGS. See the test cut-test-0.1.rb.