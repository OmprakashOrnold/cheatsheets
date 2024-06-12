list of 100 examples, ranging from basic to advanced, showcasing various methods and functionalities of the Java 8 Stream API.

### Basic Stream Operations

1. **Creating a Stream from a List**
```java
List<String> list = Arrays.asList("a", "b", "c");
Stream<String> stream = list.stream();
```

2. **Creating a Stream from an Array**
```java
String[] array = {"a", "b", "c"};
Stream<String> stream = Arrays.stream(array);
```

3. **Stream.of() to create a Stream**
```java
Stream<String> stream = Stream.of("a", "b", "c");
```

4. **Convert Stream to List**
```java
List<String> result = stream.collect(Collectors.toList());
```

5. **Filter a Stream**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> evenNumbers = numbers.stream()
                                   .filter(n -> n % 2 == 0)
                                   .collect(Collectors.toList());
```

6. **Map a Stream**
```java
List<String> result = list.stream()
                          .map(String::toUpperCase)
                          .collect(Collectors.toList());
```

7. **FlatMap a Stream**
```java
List<List<String>> list = Arrays.asList(Arrays.asList("a"), Arrays.asList("b"));
List<String> result = list.stream()
                          .flatMap(Collection::stream)
                          .collect(Collectors.toList());
```

8. **Limit a Stream**
```java
Stream<Integer> limitedStream = Stream.iterate(1, n -> n + 1)
                                      .limit(5);
```

9. **Skip elements in a Stream**
```java
Stream<Integer> skippedStream = Stream.iterate(1, n -> n + 1)
                                      .skip(5);
```

10. **Sorted Stream**
```java
List<String> sortedList = list.stream()
                              .sorted()
                              .collect(Collectors.toList());
```

### Intermediate Stream Operations

11. **Distinct elements in a Stream**
```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 3, 3, 4);
List<Integer> distinctNumbers = numbers.stream()
                                       .distinct()
                                       .collect(Collectors.toList());
```

12. **Peek operation**
```java
List<String> result = list.stream()
                          .peek(System.out::println)
                          .collect(Collectors.toList());
```

13. **Match operations**
```java
boolean allMatch = list.stream()
                       .allMatch(s -> s.startsWith("a"));

boolean anyMatch = list.stream()
                       .anyMatch(s -> s.startsWith("a"));

boolean noneMatch = list.stream()
                        .noneMatch(s -> s.startsWith("a"));
```

14. **Find operations**
```java
Optional<String> first = list.stream().findFirst();
Optional<String> any = list.stream().findAny();
```

15. **Count elements in a Stream**
```java
long count = list.stream().count();
```

16. **Reduce operation**
```java
Optional<Integer> sum = numbers.stream()
                               .reduce(Integer::sum);
```

17. **Joining Strings**
```java
String result = list.stream()
                    .collect(Collectors.joining(", "));
```

18. **Summarizing statistics**
```java
IntSummaryStatistics stats = numbers.stream()
                                    .mapToInt(Integer::intValue)
                                    .summaryStatistics();
```

19. **Grouping elements**
```java
Map<Integer, List<String>> groupedByLength = list.stream()
                                                 .collect(Collectors.groupingBy(String::length));
```

20. **Partitioning elements**
```java
Map<Boolean, List<Integer>> partitioned = numbers.stream()
                                                 .collect(Collectors.partitioningBy(n -> n % 2 == 0));
```

### Advanced Stream Operations

21. **Parallel Stream**
```java
List<String> parallelList = list.parallelStream()
                                .map(String::toUpperCase)
                                .collect(Collectors.toList());
```

22. **Custom Collector**
```java
Collector<String, ?, List<String>> toListCollector = Collectors.toList();
List<String> result = list.stream()
                          .collect(toListCollector);
```

23. **Stream Builder**
```java
Stream<String> stream = Stream.<String>builder()
                              .add("a")
                              .add("b")
                              .add("c")
                              .build();
```

24. **Generate Stream**
```java
Stream<String> generatedStream = Stream.generate(() -> "element")
                                       .limit(5);
```

25. **Iterate Stream**
```java
Stream<Integer> iterateStream = Stream.iterate(1, n -> n + 2)
                                      .limit(5);
```

26. **Collector of Collectors**
```java
Map<Boolean, Set<String>> result = list.stream()
                                       .collect(Collectors.partitioningBy(s -> s.length() > 2, Collectors.toSet()));
```

27. **Custom Aggregator**
```java
Integer sum = numbers.stream()
                     .reduce(0, (a, b) -> a + b);
```

28. **CollectingAndThen**
```java
List<String> unmodifiableList = list.stream()
                                    .collect(Collectors.collectingAndThen(Collectors.toList(), Collections::unmodifiableList));
```

29. **Mapping in Collectors**
```java
Map<Integer, List<Character>> result = list.stream()
                                           .collect(Collectors.groupingBy(String::length, Collectors.mapping(s -> s.charAt(0), Collectors.toList())));
```

30. **Reducing in Collectors**
```java
int totalLength = list.stream()
                      .collect(Collectors.reducing(0, String::length, Integer::sum));
```

### Specialized Stream Operations

31. **IntStream**
```java
IntStream intStream = IntStream.range(1, 5);
```

32. **LongStream**
```java
LongStream longStream = LongStream.range(1, 5);
```

33. **DoubleStream**
```java
DoubleStream doubleStream = DoubleStream.of(1.0, 2.0, 3.0);
```

34. **Boxing Stream**
```java
List<Integer> list = intStream.boxed()
                              .collect(Collectors.toList());
```

35. **Unboxing Stream**
```java
IntStream intStream = list.stream()
                          .mapToInt(Integer::intValue);
```

36. **Summing Int Stream**
```java
int sum = intStream.sum();
```

37. **Average of Int Stream**
```java
OptionalDouble average = intStream.average();
```

38. **Range Stream**
```java
IntStream rangeStream = IntStream.rangeClosed(1, 5);
```

39. **MapToInt**
```java
IntStream lengths = list.stream()
                        .mapToInt(String::length);
```

40. **MapToLong**
```java
LongStream longLengths = list.stream()
                             .mapToLong(String::length);
```

41. **MapToDouble**
```java
DoubleStream doubleLengths = list.stream()
                                 .mapToDouble(String::length);
```

42. **Stream of Primitives**
```java
IntStream intStream = IntStream.of(1, 2, 3, 4, 5);
```

43. **Stream from Random Numbers**
```java
DoubleStream randomStream = new Random().doubles().limit(5);
```

44. **Using Stream Builder**
```java
Stream<String> stream = Stream.<String>builder()
                              .add("a")
                              .add("b")
                              .add("c")
                              .build();
```

45. **Iterating with IntStream**
```java
IntStream iterateStream = IntStream.iterate(0, n -> n + 2).limit(5);
```

46. **Concatenating Streams**
```java
Stream<String> concatenated = Stream.concat(
    Stream.of("a", "b"),
    Stream.of("c", "d")
);
```

47. **Stream.ofNullable**
```java
Stream<String> stream = Stream.ofNullable(null);
```

48. **TakeWhile**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
List<Integer> result = numbers.stream()
                              .takeWhile(n -> n < 4)
                              .collect(Collectors.toList());
```

49. **DropWhile**
```java
List<Integer> result = numbers.stream()
                              .dropWhile(n -> n < 4)
                              .collect(Collectors.toList());
```

50. **Generating a Stream of Random Numbers**
```java
Stream<Integer> randomNumbers = Stream.generate(() -> new Random().nextInt()).limit(5);
```

### Miscellaneous Stream Operations

51. **Filter with Predicate**
```java
List<String> result = list.stream()
                          .filter(s -> s.startsWith("a"))
                          .collect(Collectors.toList());
```

52. **Map with Function**
```java
List<Integer> lengths = list.stream()
                            .map(String::length)
                            .collect(Collectors.toList());
```

53. **FlatMap with Function**
```java
List<String> flattened = list.stream()
                             .flatMap(s -> Arrays.stream(s.split("")))
                             .collect(Collectors.toList());
```

54. **Peek with Consumer**
```java
list.stream()
    .peek(System.out::println)
    .collect(Collectors.toList());
```

55. **Collect with Supplier, Accumulator, and Combiner**
```java
List<String> result = list.stream()
                          .collect(Array

List::new, ArrayList::add, ArrayList::addAll);
```

56. **toMap Collector**
```java
Map<Integer, String> map = list.stream()
                               .collect(Collectors.toMap(String::length, Function.identity(), (existing, replacement) -> existing));
```

57. **toSet Collector**
```java
Set<String> set = list.stream()
                      .collect(Collectors.toSet());
```

58. **toCollection Collector**
```java
Deque<String> deque = list.stream()
                          .collect(Collectors.toCollection(ArrayDeque::new));
```

59. **Grouping by and Mapping**
```java
Map<Integer, List<Character>> result = list.stream()
                                           .collect(Collectors.groupingBy(String::length, Collectors.mapping(s -> s.charAt(0), Collectors.toList())));
```

60. **Partitioning by and Mapping**
```java
Map<Boolean, List<Character>> result = list.stream()
                                           .collect(Collectors.partitioningBy(s -> s.length() > 2, Collectors.mapping(s -> s.charAt(0), Collectors.toList())));
```

61. **Reducing with Identity and Accumulator**
```java
int totalLength = list.stream()
                      .collect(Collectors.reducing(0, String::length, Integer::sum));
```

62. **Summing Int with Collector**
```java
int totalLength = list.stream()
                      .collect(Collectors.summingInt(String::length));
```

63. **Summing Double with Collector**
```java
double totalLength = list.stream()
                         .collect(Collectors.summingDouble(String::length));
```

64. **Summing Long with Collector**
```java
long totalLength = list.stream()
                       .collect(Collectors.summingLong(String::length));
```

65. **Averaging Int with Collector**
```java
double averageLength = list.stream()
                           .collect(Collectors.averagingInt(String::length));
```

66. **Averaging Double with Collector**
```java
double averageLength = list.stream()
                           .collect(Collectors.averagingDouble(String::length));
```

67. **Averaging Long with Collector**
```java
double averageLength = list.stream()
                           .collect(Collectors.averagingLong(String::length));
```

68. **Summarizing Int with Collector**
```java
IntSummaryStatistics stats = list.stream()
                                 .collect(Collectors.summarizingInt(String::length));
```

69. **Summarizing Double with Collector**
```java
DoubleSummaryStatistics stats = list.stream()
                                    .collect(Collectors.summarizingDouble(String::length));
```

70. **Summarizing Long with Collector**
```java
LongSummaryStatistics stats = list.stream()
                                  .collect(Collectors.summarizingLong(String::length));
```

71. **Joining with Collector**
```java
String result = list.stream()
                    .collect(Collectors.joining(", "));
```

72. **Joining with Prefix and Suffix**
```java
String result = list.stream()
                    .collect(Collectors.joining(", ", "[", "]"));
```

73. **Filtering a Stream in Collector**
```java
List<String> result = list.stream()
                          .collect(Collectors.collectingAndThen(Collectors.toList(), l -> {
                              l.removeIf(s -> s.startsWith("a"));
                              return l;
                          }));
```

74. **Mapping in Collector**
```java
Map<Integer, List<Character>> result = list.stream()
                                           .collect(Collectors.groupingBy(String::length, Collectors.mapping(s -> s.charAt(0), Collectors.toList())));
```

75. **Reducing in Collector**
```java
int totalLength = list.stream()
                      .collect(Collectors.reducing(0, String::length, Integer::sum));
```

76. **Using Custom Collector**
```java
Collector<String, ?, List<String>> toListCollector = Collectors.toList();
List<String> result = list.stream()
                          .collect(toListCollector);
```

77. **Using Stream.Builder**
```java
Stream<String> stream = Stream.<String>builder()
                              .add("a")
                              .add("b")
                              .add("c")
                              .build();
```

78. **Generating Stream**
```java
Stream<String> generatedStream = Stream.generate(() -> "element")
                                       .limit(5);
```

79. **Iterating Stream**
```java
Stream<Integer> iterateStream = Stream.iterate(1, n -> n + 2)
                                      .limit(5);
```

80. **Concatenating Streams**
```java
Stream<String> concatenated = Stream.concat(
    Stream.of("a", "b"),
    Stream.of("c", "d")
);
```

### More Advanced Examples

81. **Parallel Stream Processing**
```java
List<String> parallelList = list.parallelStream()
                                .map(String::toUpperCase)
                                .collect(Collectors.toList());
```

82. **FlatMap with Nested Collections**
```java
List<List<String>> listOfLists = Arrays.asList(Arrays.asList("a", "b"), Arrays.asList("c", "d"));
List<String> flattened = listOfLists.stream()
                                    .flatMap(Collection::stream)
                                    .collect(Collectors.toList());
```

83. **Stream with Infinite Sequence**
```java
Stream<Integer> infiniteStream = Stream.iterate(0, n -> n + 1);
```

84. **Custom Comparator for Sorting**
```java
List<String> sortedList = list.stream()
                              .sorted((s1, s2) -> s2.compareTo(s1))
                              .collect(Collectors.toList());
```

85. **Collecting to Custom Collection**
```java
Deque<String> deque = list.stream()
                          .collect(Collectors.toCollection(ArrayDeque::new));
```

86. **Using Custom Finisher in Collector**
```java
List<String> result = list.stream()
                          .collect(Collectors.collectingAndThen(Collectors.toList(), Collections::unmodifiableList));
```

87. **Reducing with Custom Operator**
```java
String concatenated = list.stream()
                          .reduce("", (s1, s2) -> s1 + s2);
```

88. **Combining Streams in Reduce**
```java
String combined = list.stream()
                      .reduce("", String::concat);
```

89. **Parallel Reduction**
```java
Integer sum = numbers.parallelStream()
                     .reduce(0, Integer::sum);
```

90. **Using a Custom Predicate**
```java
Predicate<String> startsWithA = s -> s.startsWith("a");
List<String> result = list.stream()
                          .filter(startsWithA)
                          .collect(Collectors.toList());
```

91. **Stream from Files**
```java
Path path = Paths.get("file.txt");
Stream<String> lines = Files.lines(path);
```

92. **Stream from BufferedReader**
```java
BufferedReader reader = new BufferedReader(new FileReader("file.txt"));
Stream<String> lines = reader.lines();
```

93. **Stream from Directory**
```java
try (Stream<Path> paths = Files.walk(Paths.get("dir"))) {
    paths.filter(Files::isRegularFile)
         .forEach(System.out::println);
}
```

94. **Creating Infinite Streams**
```java
Stream<Double> infiniteRandom = Stream.generate(Math::random);
```

95. **Limiting Infinite Streams**
```java
List<Double> randomNumbers = infiniteRandom.limit(10)
                                           .collect(Collectors.toList());
```

96. **Infinite Stream with Iterate**
```java
Stream<Integer> infiniteIterate = Stream.iterate(0, n -> n + 2)
                                        .limit(10);
```

97. **IntStream with Random Numbers**
```java
IntStream randomInts = new Random().ints().limit(5);
```

98. **DoubleStream with Random Numbers**
```java
DoubleStream randomDoubles = new Random().doubles().limit(5);
```

99. **LongStream with Random Numbers**
```java
LongStream randomLongs = new Random().longs().limit(5);
```

100. **Filtering with Predicate Combination**
```java
Predicate<String> startsWithA = s -> s.startsWith("a");
Predicate<String> endsWithC = s -> s.endsWith("c");
List<String> result = list.stream()
                          .filter(startsWithA.and(endsWithC))
                          .collect(Collectors.toList());
```
