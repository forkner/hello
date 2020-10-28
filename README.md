
This package depends on https://github.com/forkner/greeter1 and https://github.com/forkner/greeter2 which both depend on https://github.com/forkner/greetings

`greeter1` depends on `greetings` v0.0.0-20201028184106-8ac493a6575a

`greeter2` depends on `greetings` v0.0.0-20201028184654-c2499f999001

See both versions here: https://github.com/forkner/greetings/commits/main

Both appear in the `go.sum` for this package and this is not resolved with `go mod tidy` since they are legitimately referred to indirectly. 

Only one is picked for the build and used. This can be seen in the output of `go run .` which is:

```
Greeter1: Howdy!
Greeter2: Howdy!
```

If both versions were included, the output would be:
```
Greeter1: Hello!
Greeter2: Howdy!
```

This can also be seen by running:
`go mod vendor`

Only one copy of the source code is vendored (the one that says Howdy c2499f999001)