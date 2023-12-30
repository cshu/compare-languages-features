<h1>A list of features of different programming languages for easy comparison</h1>
<br>

<a href="https://en.wikipedia.org/wiki/Category:Programming_language_comparisons">Programming_language_comparisons</a>
<br>
<a href="https://en.wikipedia.org/wiki/Comparison_of_programming_languages_(basic_instructions)">basic_instructions</a>
<br>
<a href="https://en.wikipedia.org/wiki/Comparison_of_programming_languages_(strings)">strings</a>
<br>
<a href="https://en.wikipedia.org/wiki/Comparison_of_programming_languages_(string_functions)">string_functions</a>
<br>


<table>
<caption><h2>arbitrary-precision arithmetic</h2></caption>
<tr>
<td>
python
</td>
<td>
out of the box, int is similar to java BigInteger
<br>
but no equivalent to java BigDecimal (python decimal is not really arbitrary precision)
</td>
</tr>
<tr>
<td>
go
</td>
<td>
https://pkg.go.dev/math/big
</td>
</tr>
<tr>
<td>
java
</td>
<td>
BigInteger and BigDecimal
</td>
</tr>
</table>



<table>
<caption><h2>between num and num</h2></caption>

<tr><td>
python
</td><td>
<pre>
float(the_int)
int(the_float) #or round(the_float) if you need to round
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
the_u64 as u32 //or use u32::try_from(the_u64) for more safety
the_i32 as f64
the_f64 as i32
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
int64(the_int32)
int32(the_int64)
int(the_float64)
float64(the_int64)
</pre>
</td></tr>

<tr><td>
java
</td><td>
<pre>
(int) theLong
(int) theDouble
</pre>
</td></tr>

<tr><td>
awk
</td><td>
<pre>
int(x)
</pre>
This removes fractional part (but remember there is no integer type. All representation and computation are floating point)
</td></tr>

</table>



<table>
<caption><h2>between num and str</h2></caption>

<tr><td>
python
</td><td>
<pre>
int(the_str)
str(the_int)
float(the_str)
str(the_float)
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
.parse::&lt;i32&gt;()?
.to_string()
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
strconv.Atoi(s)
strconv.Itoa(i)
</pre>
</td></tr>

<tr><td>
java
</td><td>
<pre>
Integer.parseInt(str)
Integer.toString(n)
Double.parseDouble(str)
Double.toString(n)
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
Number() OR parseFloat()
''+n OR n.toString() OR String(n)
</pre>
</td></tr>


<tr><td>
awk
</td><td>
thestr+0 for str-to-num
<br>
thenum"" for num-to-str (concat)
</td></tr>

</table>



<table>
<caption><h2>dict</h2></caption>

<tr><td>
python
</td><td>
<pre>
d = {}
k in d
d[k] OR d.get(key[, default])
d[k] = v
del d[k] OR .pop(key[, default]) #and there is also d.popitem()
.clear()
.copy()#shallow copy
len(d)
.keys() OR list(d)
.values() OR list(d.values())
d | other OR d |= other
for k, v in d.items():
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
HashMap::new()
.contains_key(k)
d[k] OR .get(k)
d.insert(k, v)
.remove(k)
.clear()
.clone()
.len()
.keys()
.values()
.extend(d2)
for k, v in &amp;d {}
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
make(map[K]V)
_, ok := d[k]
d[k]
d[k] = v
delete(d, k)
clear(d)//since go 1.21
//https://pkg.go.dev/maps#Clone //since 1.21 func Clone(m M) M
len(d)
//https://pkg.go.dev/golang.org/x/exp/maps#Keys
//https://pkg.go.dev/golang.org/x/exp/maps#Values
//https://pkg.go.dev/maps#Copy //since 1.21 func Copy(dst M1, src M2)
for k, v := range d {}
</pre>
</td></tr>

<tr><td>
c#
</td><td>
<pre>
new Dictionary&lt;K, V&gt;()
.ContainsKey(k)
d[k] OR TryGetValue
d[k] = v
.Remove(k)
.Clear()
d2 = new Dictionary&lt;K, V&gt;(d);
.Count
.Keys
.Values
src.ToList().ForEach(x => dst.Add(x.Key, x.Value));
foreach(KeyValuePair&lt;K, V&gt; kvp in d) {}
</pre>
</td></tr>

<tr><td>
java
</td><td>
<pre>
new HashMap&lt;&gt;()
.containsKey(k)
.get(k) OR .getOrDefault(k, dv)
.put(k, v)
.remove(k)
.clear()
d2 = new HashMap(d)
.size()
.keySet()
.values()
dst.putAll(src)
for (Map.Entry&lt;K, V&gt; entry : d.entrySet()) {}
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
new Map()//mozilla.org mentions map being better than obj: Performs better in scenarios involving frequent additions and removals of key-value pairs.
.has(k)
.get(k)
.set(k, v) //d[k]=v is wrong. It does NOT throw, but it does not work as you expect
.delete(k)
.clear()
d2 = new Map(d)
.size
.keys()
.values()
newMap = new Map([...map1, ...map2])
for (const [k, v] of d) {}
</pre>
</td></tr>

<tr><td>
dart
</td><td>
<pre>
var d = Map&lt;K, V&gt;() //note LinkedHashMap is default, not HashMap
.containsKey(k)
d[k]
d[k] = v
.remove(k)
.clear()
clonedMap = Map&lt;K, V&gt;.of(d)//Map.of is better than Map.from. Cuz it is newer, with generics
.length
.keys
.values
dst.addAll(src)
for (final entry in d.entries) {}
</pre>
</td></tr>

</table>



<table>
<caption><h2>division returning integer (might be floordiv)</h2></caption>

<tr><td>
python
</td><td>
<pre>
x//y
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
Math.trunc(x/y) OR Math.floor(x/y)
</pre>
</td></tr>

<tr><td>
dart
</td><td>
<pre>
x ~/ y
</pre>
</td></tr>

<tr><td>
awk
</td><td>
<pre>
int(x/y)
</pre>
</td></tr>

<tr><td>
pwsh
</td><td>
<pre>
[Math]::DivRem(x,y,[ref]$null)
</pre>
</td></tr>

</table>



<table>
<caption><h2>dynamic array</h2></caption>

<tr><td>
python
</td><td>
<pre>
l = []
l.append(e)
l.index(e)
l[0]
l.insert(idx, e)
l += list2 OR l.extend(list2)
l.sort()
l.reverse()
l.copy()
l.clear() OR del l[:]
len(l)
l.pop([idx]) OR del l[idx]
l.remove(e)#search and remove first e! or raises err if not found!
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
l = vec![]
l.push(e)
l.iter().position(|&amp;r| r==x).unwrap()
l[0] OR l.get(0)
l.insert(idx, e)
l.extend(iter) OR l.extend_from_slice(sli) //"Note that this function is same as extend except that it is specialized to work with slices instead."
l.sort()
l.reverse()
l.clone()
l.clear()
l.len()
l.pop()//returns option
l.remove(idx)
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
l := make(S, s_len) OR var l []int
l = append(l, e)
slices.Index(l, e)//since go 1.21
l[0]
l = slices.Insert(l, idx, e)
l = append(l, l2...)
slices.Sort(l)
slices.Reverse(l)
slices.Clone(l)
l = nil OR l = l[:0] //depends on whether you want gc to kick in or you want keep capacity
len(l)//there also exists a cap(l) for capacity
</pre>
</td></tr>

<tr><td>
c#
</td><td>
<pre>
new List&lt;T&gt;()
.Add(e)
.IndexOf(e)
l[0]
.Insert(idx, e)
.AddRange(IEnumerable)
.Sort()
.Reverse()
clonedList = new List&lt;T&gt;(l)
.Clear()
.Count
.RemoveAt(idx)
.Remove(e)//search and remove first e! return false if not found!
</pre>
</td></tr>

<tr><td>
java
</td><td>
<pre>
new ArrayList&lt;&gt;()
.add(e)
.indexOf(e)
l.get(0)
.add(idx, e)
.addAll(collection)
Collections.sort(l) OR l.sort(String::compareToIgnoreCase)
Collections.reverse(l)
clonedList = new ArrayList&lt;&gt;(l);
clear()
size()
remove(idx)
remove(e)//search and remove first e! return false if not found!
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
l = []
.push(e)
.indexOf(e)//note compared like ===
l[idx]
.splice(idx, 0, e)
l.push(...list2) OR l = l.concat(list2)
.sort() OR .sort(cmpFn) //defualt cmpFn do string cmp
.reverse()
.slice()//shallow copy
.length = 0
.length
.pop()
.splice(idx, 1)//delete l[idx] does not change length, the elem becomes undefined. This is different from del in python
</pre>
</td></tr>

<tr><td>
dart
</td><td>
<pre>
final growableList = &lt;String&gt;['A', 'B']
l.add(e)
l.indexOf(e)
l[idx]
.insert(idx, e)
l.addAll(iterable)
sort([int compare(E a, E b)?])
.reversed//this returns Iterable, to get list, you need .toList()
clonedList = List&lt;T&gt;.of(l)//List.of is better than List.from. Cuz it is newer, with generics
.clear() OR .length = 0
.length
.removeLast()
.removeAt(idx)
.remove(e)//search and remove first e! return false if not found!
</pre>
</td></tr>

</table>



<table>
<caption><h2>enumerate</h2></caption>
<tr>
<td>
python
</td>
<td>
<pre>
lst = ["a", "b", "c"]
 
for elem in enumerate(lst):
  print (elem)#each elem is tuple like (0, 'a')

#OR

for idx, elem in enumerate(lst):
  print (idx, elem)

#python enumerate() can have a 2nd parameter as start index
</pre>
</td>
</tr>
<tr>
<td>
rust
</td>
<td>
calling enumerate() on a iterator to create an iterator of tuples.
<br>
commonly used like somevec.iter().enumerate()
</td>
</tr>
<tr>
<td>
go
</td>
<td>
<pre>
for i, v := range sli {
}
</pre>
go for range already has index. It is NOT optional. You can use `_` though.
</td>
</tr>
<tr>
<td>
c#
</td>
<td>
<pre>
foreach (var (elem, i) in lst.Select((elem, i) => ( elem, i )))
</pre>
//https://stackoverflow.com/questions/43021/how-do-you-get-the-index-of-the-current-iteration-of-a-foreach-loop
</td>
</tr>
</table>



<table>
<caption><h2>exponentiation operator</h2></caption>

<tr><td>
python/bash/js/perl/php
</td><td>
<pre>
**
</pre>
</td></tr>

<tr><td>
bc/awk
</td><td>
<pre>
^
</pre>
</td></tr>

</table>



<table>
<caption><h2>loop iterable</h2></caption>

<tr><td>
python
</td><td>
<pre>
for x in lst:
</pre>
</td></tr>

<tr><td>
rust
</td><td>
for x in lst {}
</td></tr>

<tr><td>
go
</td><td>
<pre>
for i, v := range sli {
}
</pre>
</td></tr>

<tr><td>
c#
</td><td>
foreach (var x in lst) {}
</td></tr>

<tr><td>
java
</td><td>
<pre>
for (T x : lst) {}
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
for (const x of lst) {}
</pre>
</td></tr>

<tr><td>
dart
</td><td>
for (final e in l) {}
</td></tr>

<tr><td>
awk
</td><td>
for (idx1base in array)#idx starts from 1, though actually awk array is closer to dict than array
</td></tr>

</table>



<table>
<caption><h2>Multiple results returned by a function</h2></caption>

<tr><td>
python
</td><td>
use tuple
<pre>
def f():
 return True, False
x, y = f()
</pre>
</td></tr>

<tr><td>
rust
</td><td>
use tuple
<pre>
fn nums() -> (isize, isize) {
    (1, 2)
}
let (foo, bar) = nums();
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
func xystr(x, y string) (string, string) {
	return y, x
}
</pre>
</td></tr>

<tr><td>
c#
</td><td>
use tuple
<pre>
(string, string, string) Mkstrs()
{
    return ("one", "two", "three"); //tuple
}
var (first, second, third) = Mkstrs();
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
const [foo, bar] = mkAnArray() //simply return an array and then do "Destructuring assignment"
</pre>
</td></tr>

</table>



<table>
<caption><h2>Null coalescing operator</h2></caption>
<tr><td>
<a href="https://en.wikipedia.org/wiki/Null_coalescing_operator">link</a>
</td></tr>
</table>



<table>
<caption><h2>raw string literals</h2></caption>

<tr><td>
python
</td><td>
<pre>
r'\n'
r"\n"
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
r""
r#""#
br""
br#""#
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
``
</pre>
</td></tr>

<tr><td>
c#
</td><td>
<pre>
@"" //or use """ similar to java. It can also be longer like """"
</pre>
</td></tr>

<tr><td>
java
</td><td>
<pre>
"""
"""
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
console.log(String.raw`\n`)
</pre>
</td></tr>

</table>



<table>
<caption><h2>set</h2></caption>

<tr><td>
python
</td><td>
<pre>
s = set()
k in s
.add(k)
.remove(k)#can raise err
.clear()
.copy()#shallow copy
len(s)
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
HashSet::new()
.contains(k)
.insert(k)
.remove(k)
.clear()
.clone()
.len()
.extend(s2)
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
make(map[K]bool)
_, ok := d[k]
d[k] = true
delete(d, k)
clear(d)//since go 1.21
//https://pkg.go.dev/maps#Clone //since 1.21 func Clone(m M) M
len(d)
//https://pkg.go.dev/maps#Copy //since 1.21 func Copy(dst M1, src M2)
for k, _ := range d {}
</pre>
</td></tr>

<tr><td>
c#
</td><td>
<pre>
new HashSet&lt;T&gt;()
.Contains(k)
.Add(k)
.Remove(k)
.Clear()
s2 = new HashSet&lt;T&gt;(s);
.Count
</pre>
</td></tr>

<tr><td>
java
</td><td>
<pre>
new HashSet&lt;&gt;()
.contains(k)
.add(k)
.remove(k)
.clear()
s2 = new HashSet(s)
.size()
</pre>
</td></tr>

<tr><td>
js
</td><td>
<pre>
new Set()
.has(k)
.add(k)
.delete(k)
.clear()
s2 = new Set(s)
.size
</pre>
</td></tr>

<tr><td>
dart
</td><td>
<pre>
var d = &lt;T&gt;{} //note LinkedHashSet is default, not HashSet
.contains(k)
.add(k)
.remove(k)
.clear()
clonedSet = Set&lt;T&gt;.of(d)//Set.of is better than Set.from. Cuz it is newer, with generics
.length
dst.addAll(src)
</pre>
</td></tr>

</table>



<table>
<caption><h2>spread operator</h2></caption>
<tr>
<td>
python
</td>
<td>
<pre>
*list
</pre>
</td>
</tr>
<tr>
<td>
js
</td>
<td>
...array
</td>
</tr>
</table>



<table>
<caption><h2>String interpolation</h2></caption>
<tr>
<td>
python
</td>
<td>
<pre>
'My age is {age}.'.format(age=age)#can be int
f'My age is {age}'#after 3.6
</pre>
</td>
</tr>
<tr>
<td>
go
</td>
<td>
<pre>
fmt.Sprint()
fmt.Sprintf()//this one is particularly close to what other languagues provide
fmt.Sprintln()
</pre>
</td>
</tr>

<tr><td>
rust
</td><td>
format!("{x} equals {y}");
</td></tr>

<tr><td>
c#
</td><td>
<pre>
$"Hello, {ident}"
$"""Hello, {ident}"""
</pre>
</td></tr>

<tr>
<td>
java
</td>
<td>
String.format("Make %s %d", "str", 42);
</td>
</tr>

<tr><td>
js
</td><td>
<pre>
`Hello ${expr}`
</pre>
</td></tr>

</table>



<table>
<caption><h2>str.contains</h2></caption>
<tr>
<td>
python
</td>
<td>
`in` operator
<br>
`needle_str in haystack` (`__contains__`)
<br>
(no way to check byte. And no char type)
</td>
</tr>
<tr>
<td>
go
</td>
<td>
strings.Contains(haystack, needleStr)
<br>
strings.IndexByte(haystack, needleByte) != -1
</td>
</tr>
<tr>
<td>
rust
</td>
<td>
`.contains(a_pattern)`
</td>
</tr>
<tr>
<td>
java
</td>
<td>
.contains(CharSequence s)
</td>
</tr>

<tr><td>
js
</td><td>
<pre>
.includes(str)
</pre>
</td></tr>

</table>



<table>
<caption><h2>str.find</h2></caption>
<tr>
<td>
python
</td>
<td>
str.find(sub[, start[, end]]) OR str.index(sub[, start[, end]]) #.index can raise err
<br>
(no fn for byte. And no char type)
<br>
(note python idx is based on code points)
</td>
</tr>
<tr>
<td>
go
</td>
<td>
strings.Index(haystack, needleStr)
<br>
strings.IndexByte(haystack, needleByte)
</td>
</tr>
<tr>
<td>
rust
</td>
<td>
`.find(a_pattern)` returns `Option&lt;usize&gt;`
</td>
</tr>
<tr>
<td>
java/js
</td>
<td>
.indexOf(str)
(java can also .indexOf(int))
</td>
</tr>
</table>



<table>
<caption><h2>str literal concat</h2></caption>

<tr><td>
python
</td><td>
"FOO" "BAR"
</td></tr>

<tr><td>
c
</td><td>
"FOO" "BAR"
</td></tr>

<tr><td>
awk
</td><td>
"FOO" "BAR"
<br>
#actually awk do any concat like this, not only literal concat
</td></tr>

</table>



<table>
<caption><h2>swap values</h2></caption>

<tr><td>
python
</td><td>
<pre>
x, y = y, x
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
mem::swap(&amp;mut x, &amp;mut y)
</pre>
</td></tr>

<tr><td>
go
</td><td>
<pre>
x, y = y, x
</pre>
</td></tr>

<tr><td>
c#
</td><td>
<pre>
(a, b) = (b, a);//since C# 7
</pre>
</td></tr>

<tr><td>
java
</td><td>
just use tmp variable
</td></tr>

<tr><td>
js
</td><td>
<pre>
[a, b] = [b, a];
</pre>
</td></tr>

<tr><td>
dart
</td><td>
<pre>
(b, a) = (a, b);//since Dart 3 record pattern
</pre>
</td></tr>

</table>



<br>
<a href="https://en.wikipedia.org/wiki/Switch_statement">Switch_statement</a>
<br>
<table>
<caption><h2>switch statement</h2></caption>

<tr><td>
python 3.10
</td><td>
<pre>
match x:
 case 'a' | 'c':
  #do sth #NOTE fallthrough does NOT happen!
 case 'b':
  #do sth
 case _:#default
  #do sth
</pre>
</td></tr>

<tr><td>
rust
</td><td>
<pre>
match x {
 1 | 2 => what(),
 3 => whaat(),
 _ => wha(),
}
</pre>
</td></tr>

<tr><td>
go
</td><td>
Just normal switch-case except that by default it does not fallthrough (But there is a `fallthrough` keyword you can use to force it fallthrough)
<br>
(BTW you can do `switch {...}` without any condition)
</td></tr>

<tr><td>
dart
</td><td>
Just normal switch-case except that only empty cases fallthrough. (Non-empty cases do NOT fallthrough)
</td></tr>

<tr><td>
java/c#/c/c++/js/awk(mawk does not have it?)
</td><td>
Just normal switch-case
</td></tr>

</table>
