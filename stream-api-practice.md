# Java Stream API Practice Problems

## Basic Problems

### 1. Create a list of integers and filter out even numbers.
<details>
  <summary>Show Solution without streams</summary>

```java
public List<Integer> filterEvenNumbers(List<Integer> numbers) {
        List<Integer> oddNumbers = new ArrayList<>();
        for (Integer number : numbers) {
            if (number % 2 != 0) {
                oddNumbers.add(number);
            }
        }
        return oddNumbers;
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
public static List<Integer> filterEvenNumbers(List<Integer> numbers) {
        return numbers.stream()
                      .filter(n -> n % 2 != 0)
                      .collect(Collectors.toList());
    }
```
</details>

### 2. Create a list of strings and convert all strings to uppercase.
<details>
  <summary>Show Solution without streams</summary>

```java
public List<String> convertToUppercase(List<String> strings) {
        List<String> uppercaseStrings = new ArrayList<>();
        for (String str : strings) {
            uppercaseStrings.add(str.toUpperCase());
        }
        return uppercaseStrings;
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
public static List<String> convertToUpperCase(List<String> strings) {
        return strings.stream()
                      .map(String::toUpperCase)
                      .collect(Collectors.toList());
    }
```
</details>


### 3. Create a list of integers and find the sum of all numbers.
<details>
  <summary>Show Solution without streams</summary>

```java
public int sumOfNumbers(List<Integer> numbers) {
        int sum = 0;
        for (Integer number : numbers) {
            sum += number;
        }
        return sum;
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
public static int sumOfNumbers(List<Integer> numbers) {
        return numbers.stream()
                      .mapToInt(Integer::intValue)
                      .sum();
    }

```
</details>


### 4. Create a list of strings and find the longest string.
<details>
  <summary>Show Solution without streams</summary>

```java
 public String findLongestString(List<String> strings) {
        String longest = "";
        for (String str : strings) {
            if (str.length() > longest.length()) {
                longest = str;
            }
        }
        return longest;
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
 public static String findLongestString(List<String> strings) {
        return strings.stream()
                      .max((s1, s2) -> Integer.compare(s1.length(), s2.length()))
                      .orElse(null);
    }
```
</details>


### 5. Create a list of integers and sort them in ascending order.
<details>
  <summary>Show Solution without streams</summary>

```java
 public List<Integer> sortAscending(List<Integer> numbers) {
        List<Integer> sortedList = new ArrayList<>(numbers);
        Collections.sort(sortedList);
        return sortedList;
    }

```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java

```
</details>


### 6. Create a list of strings and sort them in descending order.
<details>
  <summary>Show Solution without streams</summary>

```java
public List<String> sortDescending(List<String> strings) {
        List<String> sortedList = new ArrayList<>(strings);
        Collections.sort(sortedList, Collections.reverseOrder());
        return sortedList;
    }
```
</details>

<details>
  <summary>Show Solution with streams</summary>

```java
 public static List<String> sortStringsDescending(List<String> strings) {
        return strings.stream()
                      .sorted((s1, s2) -> s2.compareTo(s1))
                      .collect(Collectors.toList());
    }
```
</details>

### 7. Create a list of integers and find the maximum number.
<details>
  <summary>Show Solution</summary>

```java
public int findMaxNumber(List<Integer> numbers) {
        int max = Integer.MIN_VALUE;
        for (Integer number : numbers) {
            if (number > max) {
                max = number;
            }
        }
        return max;
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
public static int findMaxNumber(List<Integer> numbers) {
        return numbers.stream()
                      .max(Integer::compareTo)
                      .orElse(Integer.MIN_VALUE);
    }
```
</details>


### 8. Create a list of integers and find the minimum number.
<details>
  <summary>Show Solution without streams</summary>

```java
public int findMinNumber(List<Integer> numbers) {
        int min = Integer.MAX_VALUE;
        for (Integer number : numbers) {
            if (number < min) {
                min = number;
            }
        }
        return min;
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
public static int findMinNumber(List<Integer> numbers) {
        return numbers.stream()
                      .min(Integer::compareTo)
                      .orElse(Integer.MAX_VALUE);
    }
```
</details>

### 9. Create a list of strings and concatenate them into a single string.
<details>
  <summary>Show Solution without streams</summary>

```java
public String concatenateStrings(List<String> strings) {
        StringBuilder concatenated = new StringBuilder();
        for (String str : strings) {
            concatenated.append(str);
        }
        return concatenated.toString();
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
 public static String concatenateStrings(List<String> strings) {
        return strings.stream()
                      .collect(Collectors.joining());
    }
```
</details>


### 10. Create a list of integers and count the number of elements.
<details>
  <summary>Show Solution without streams</summary>

```java
  public int countElements(List<Integer> numbers) {
        return numbers.size();
    }
```
</details>
<details>
  <summary>Show Solution with streams</summary>

```java
 public static long countElements(List<Integer> numbers) {
        return numbers.stream()
                      .count();
    }
```
</details>
