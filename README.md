# stuartsierra/component co-dependency facility
Based in original co-dependency idea of [Malcolm Sparks](https://github.com/juxt/component) to achieve co-dependency relation in
[stuartsierra/component](https://github.com/stuartsierra/component) library.

This co-dependency proposal is designed on the idea that component doesn't need co-dependencies to start,
and therefore we can "expect" them in the same way as futures values. In this proposal component will have a mutable reference value

## Releases and Dependency Information

Add co-dependency to your project `:dependencies`.

![Clojars Project](http://clojars.org/tangrammer/co-dependency/latest-version.svg)


## Usage
Follow the test provided to learn howto use it :)

... basically you only need to use ```co-dep/co-using``` in the same way as you do with ```component/using```, and after start your system then apply ```(co-dep/start your-system)```

If you use stuartsierra ["reloaded" workflow](http://thinkrelevance.com/blog/2013/06/04/clojure-workflow-reloaded) then you have to change original stuartsierra dev/start function
```clojure
(defn start []
  (alter-var-root #'system component/start))
```
by co-dep/start
```clojure
(defn start
  "Starts the current development system."
  []
  (alter-var-root #'system co-dep/start))
```

## Drawbacks
In contrast with normal dependencies that you get using clojure map functions 

```clojure
(:dependency-key component) 
;;=> dependency
```

when you want to retrieve a co-dependency you need to deref the co-dependency value 

```  
@(:co-dependency-key component)    
;;=> co-dependency
```



## License

Copyright © 2014 tangrammer (JUXT.pro)

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
