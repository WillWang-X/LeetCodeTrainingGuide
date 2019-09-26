# String Pattern 


Given the length of the words and the continous maximum vowels the word can contain, please tell the number of all formed string. 

- The alphabet in use is all characters in the range ascii[a-z].
- Vowels are in the set {a, e, i, o, u}
- Consonants are the remainder

```
input: word_len, max_vowel
output: total
```


Example:

```
input: 2, 1
ouput: 651
explanantion: 
21 * 21 + 5 * 21 + 21 * 5 = 651, cause we have string pattern {cc, vc, cv} 
c is for consonants and v is for vowels.
```

## Idea

1） 从基础开始写，看看**有没有规律**

```
(word_len, max_vowel) : {all string patterns}

(2, 1): {cc, vc, cv}
(3, 1): {ccc, vcc, cvc, ccv, vcv}
(4, 1): {cccc, vccc, cvcc, ccvc, vcvc, cccv, vccv, cvcv}
```

2） 看看有没有**推导关系**
	- 试图从`（2，1）` 推导出 `（3， 1）`，发现了结尾的特点: (3, 1) = {(2, 1) + c} + {`(2 ,1) end with c` + v} 
	- 即（3，1）中`c`结尾的，直接可以从（2，1） + c 生成，因为不影响`max_vowel`
	- (3, 1) 中`v`结尾的，只能从（2，1）中c结尾的 + v 生成，这样也不影响`max_vowel`

```
{ccc, vcc, cvc} = {cc, vc, cv} + c
{ccv, vcv} = {cc, vc} + v
```

3） 试图进行数学化

|(word_len, max_vowel)|`V`<br>end with v|`C`<br>end with c|`W`<br>the number of all strings|
|:--:|:--:|:--:|:--:|
|(2, 2)|26**1 * 5 | 26**1 * 21| 26**2| 
|(3, 2)| V<sub>(3,2)</sub> = `(26**1 * 21)` * 5 | C<sub>(3,2)</sub> = `26**2` * 21 | W<sub>(3,2)</sub> = V<sub>(3,2)</sub> +   C<sub>(3,2)</sub>|
|(4, 2)|V<sub>(4,2)</sub> = C<sub>(3,2)</sub> * 5|C<sub>(4,2)</sub> = W<sub>(3,2)</sub> * 21|W<sub>(4,2)</sub> = V<sub>(4,2)</sub> +   C<sub>(4,2)</sub>|
|(5, 2)|C<sub>(4,2)</sub> * 5|W<sub>(4,2)</sub> * 21|W<sub>(5,2)</sub> = V<sub>(5,2)</sub> +   C<sub>(5,2)</sub>|
|`(L, M)`| C * 5| W * 21 | C * 5 + W * 21 |


- V<sub>(wordLen, maxVowel)</sub> = C<sub>(wordLen - 1, maxVowel)</sub> * 5
- C<sub>(wordLen, maxVowel)</sub> = W<sub>(wordLen - 1, maxVowel)</sub> * 21
- W<sub>(wordLen, maxVowel)</sub> = V<sub>(wordLen, maxVowel)</sub> +   C<sub>(wordLen, maxVowel)</sub>

4）再考虑一下base case和 edge case的情况

- W<sub>(3, 3)</sub> = 26 * 26 * 26, 因为任何字母都可以使用，同理，
	- V<sub>(3, 3)</sub> = 26 * 26 * 5， 因为要以`vowel`结尾 = {a, e, i, o, u}
	- C<sub>(3, 3)</sub> = 26 * 26 * 21， 因为要以`consonants` 结尾
- W<sub>(3, 0)</sub> = 21 * 21, maxVowel = 0 作为 `edge case` 处理 

小结：本质上，使用的是**数学归纳法**思维过程。

## Code 

### [v 0.1](https://repl.it/@WillWang42/string-pattern)

``` python
def string_pattern(word_len, max_vowel):
	  module = 10 ** 9 + 7 
	  
	  if max_vowel == 0:
		    return 21 ** word_len
	  
	  end_c = 26 ** (max_vowel - 1) * 21
	  end_v = 26 ** (max_vowel - 1) * 5
	  total = 26 ** max_vowel
	  
	  for _ in range(word_len - max_vowel):
		    end_v = (end_c * 5) % module  
		    end_c = (total * 21) % module
		    total = (end_c + end_v) % module
	  return total
```