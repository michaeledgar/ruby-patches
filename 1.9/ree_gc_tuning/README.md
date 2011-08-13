# REE's GC Tuning

**Author:** Github users skaes (Stefan Kaes) and funny-falcon

## What it does

Ruby's GC performance is often a bottleneck for large applications which
allocate many objects; Rails is a common victim. There are some parameters
which can be modified to improve this, but changing these parameters
programmatically has not yet landed in Ruby's main distribution. In part,
this is because they are implementation specific.

If you're using Ruby 1.9.2, and want to take advantage of these implementation-specific
parameters, this patch exposes them as environment variables:

* `RUBY_GC_MALLOC_LIMIT`: Specifies a maximum number of objects that can be allocated
  before a mandatory GC sweep begins. Setting this higher means more objects will be
  allocated before a mandatory sweep.  
  **Default:** 8000000  
  **Suggested:** 45000000+ (45 million).  
* `RUBY_HEAP_MIN_SLOTS`: Specifies the minimum number of heap spots to allocate. This
  increases at an exponential rate, but starts too low for a Rails app.  
  **Default:** 10000  
  **Suggested:** 500000+ (500 thousand).  
* `RUBY_FREE_MIN`: A required number of heap slots that are left over after GC runs. If
  GC runs and this many slots are not open, then a new heap slab will be allocated.  
  **Default:** 4096  
  **Suggested:** 50000+ (50 thousand)  

More information can be found in the [REE Documentation](http://www.rubyenterpriseedition.com/documentation.html#_garbage_collector_performance_tuning).