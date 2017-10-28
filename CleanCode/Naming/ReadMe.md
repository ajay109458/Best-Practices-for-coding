# Coding convention for Naming
Naming is very important aspect of coding as naming is everywhere we name our variables, functions, directories, files, namespaces etc.

### Reveal your intention behind name

##### Bad
```
int d // elapsed time in days
```

##### good
```
int elapsedTimeInDays
```
### Name in way so that reader can pronounce

##### Bad
```
int pc_gwda
```

##### good
```
int numberOfStudents
```

#####  Bad
```
public int getYYYY() {
  return this.year;
}
```

##### good
```
public int getYear() {
  return this.year;
}
```

##### Bad
```
int qty_tests=0;
int qty_tests_m=0;
int qty_tests_s=0;
int qty_skip=0;
int qty_failed=0;
```

##### good
```
int testsCount = 0;
int testMethodsCount = 0;
int testScenariosCount = 0;
int skippedTestsCount = 0;
int failedTestsCount = 0;
```

### Don't use hungarian notation in coding as IDE are now smarter.
Earlier people use to put prefix I for interface, C for class, A for Abstract class etc. But it reduces the readaility of code.

Account is better than IAccount

### Part of speach
Class name should be a Noun. Avoid words like manager, processor, data, info

Methods should be Verb.

If a method or variable representing boolean value it should be written as predicate. Like IsEmpty()

Enums represents state so they are often adjective.

```
  if(employee.isLate()) {
    employee.reprimend();
  }
```

### Shorter name is fine if it's being used closed to it's declartation
example
```
for(Cars c: carsList) {
  System.out.println("My car is " + c.name);
}
```

In above code meaning of c is clear as it's being used very close to it's declartation

### Longer name is fine if it's private
E.g.

openFileAndThrowIfNotFound is bad name if it's public and being used at many places. If it's private then it's fine because in that behaves as comments.
