# TypeSwitch
Provides a TypeSwitch function in Typescript allowing you to switch on the type of the argument past into the function providing a sudo simple pattern matching function.

The `Case` function used within the `TypeSwitch` is type safe, so you can't use a `String` and then provide a function that uses a number as it's argument. 

The `TypeSwitch` function can be used like this:

```
class MyOwnMarkerClass {
  public someProperty: string = "some property value"
}

const result = TypeSwitch(new MyOwnMarkerClass())(
    Case(Number)
      ((n: number) => `you gave me a number and it was ${n.toString()}`),
    Case(String)
      ((s: string) => `you gave me a string ${s}`),
    Case(MyOwnMarkerClass)
      ((m: MyOwnClass) => `you gave me MyOwnClass with value ${m.someProperty}`)
);
```
The above result const will have the value `you gave me MyOwnClass with value some property value`.

# TypeSwitchWithDefault
Provides the same functionality as above with the addition of a default function if all cases have not been met.

The `TypeSwitchWithDefault` function can be used like this:

```
class MyOwnMarkerClass {
  public someProperty: string = "some property value"
}

const result = TypeSwitchWithDefault(new MyOwnMarkerClass())(
    Case(Number)
      ((n: number) => `you gave me a number and it was ${n.toString()}`),
    Case(String)
      ((s: string) => `you gave me a string ${s}`),
)(
  Default(() => 'this is the default returned value')
);
```
The above result const will have the value `this is the default returned value`.
