# Elixir Basic

## Value Types

### Integers
### Floating point number
### Atoms

These are all atoms:

```
:fred :is_binary? :var@2 :<> :=== :"func/3" :"long john silver"
```

One thing that makes atoms invaluable is that their name is their value. Two atoms with the same name will always compare as being equal, even if they were created by different applications sitting on two computers separated by an ocean.

### Ranges

### Regular expressions

## System Types

### Pids and Ports

A pid is a reference to a local or remote process, and a port is a reference to a resource that you will be reading or writing.

### References

## Collection Types

### Tuples

```
{1, 2}   {:ok, 42, "next"}  {:error, :enoent}
```
### Lists

```
[1, 2, 3] ++ [4, 5, 6]
[1, 2, 3, 4] -- [2, 4]
1 in [1,2,3,4]
"wombat" in [1, 2, 3, 4]
```
### Keyword Lists

```
[1, fred: 1, dave: 2] => [1, {:fred, 1}, {:dave, 2}]
{1, fred: 1, dave: 2} => {1, [fred: 1, dave: 2]}
```
### Maps
A map is a collection of key/value pairs.

```
%{ key => value, key => value }

status = %{ "Al" => "Alabama", "WI" => "Wisconsin"}
status["AL"] => "Alabama"
```
### Binaries

```
bin = << 1, 2 >> => <<1, 2>>
byte_size bin => 2
```
Binaries are both important and arcane. They’re important because Elixir uses them to represent UTF strings, They’re arcane because, at least initially, you’re unlikely to use them directly.