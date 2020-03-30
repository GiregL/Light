# Light

Light is a functional programming language inspired by Haskell and an experiment.
I use this project to practice and improve my skills with pure functional languages.

More informations about this project will come later.

## Language Specification

Light will be a pure functional language with abuse of pattern matching, 
replacing in the same way the if and else expressions.
For example :

```
boolAnd :: Bool -> Bool -> Bool
boolAnd b1 b2 =
    match (b1, b2) with
    | (True, True) => True
    | _            => False

-- or

boolOr :: Bool -> Bool -> Bool
boolOr False False = False
boolOr b1 b2       = True
```

Some builtin types will come with the language :

| Types | Example Values |
| :----: | :-----: |
|Bool|**True** and **False**|
|Int| 0, -59, 999, ...|
|Double|0.2, -0.8, 990.4|
|Char|'c', 'h', 'a', '5', '\\'', ...|
|String| "hello", "world", "156", ...|
|List (of type t)|[1, 2, 3, 4] ['a', 'b', 'c']|

Later, there will be a type architecture that permit some type substitution.

```
-- Declare a typeclass that instanciates the (+) function
typeclass Num
    where
        (+) :: Num -> Num -> Num

type Int = omitted
    derives Num where
        (+) :: Int -> Int -> Int
        a (+) b = omitted

type Double = omitted
    derives Num where
        (+) :: Double -> Double -> Double
        a (+) b = omitted

type Fractional = Fractional
    { numerator   :: Int 
    , denominator :: Int
    }
    derives Num where
        (+) :: Fractional -> Fractional -> Fractional
        a (+) b = omitted


-- To define an instance of a type that already exists :
derive MyTypeClass for BuiltinType where
    myFunction = omitted

-- To define an instance of a class that already exists for your types :
derive Num for MyType where
    mt1 (+) mt2 = omitted
```

Here are some basic operators : `+ - * / >= <= > < == != && ||`

|Operator|Type|
|:---:|:---:|
|+|Num -> Num -> Num|
|-|Num -> Num -> Num|
|*|Num -> Num -> Num|
|/|Num -> Num -> Num|
|\>= and >|Num -> Num -> Num|
|<= and \<|Num -> Num -> Num|
|!=|a -> a -> Bool|
|==|a -> a -> Bool|
|&&|Bool -> Bool -> Bool|
|\|\||Bool -> Bool -> Bool|