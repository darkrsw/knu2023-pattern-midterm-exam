# Midterm Exam

Your submission must satisfy the following requirements:

* R1. Shall initialize your assignment repository from
* R2. Write your `app_analyzer.py` in the repository.
* R3. Test your `app_analyzer.py` by using `pytest`.
* R4. You need to let your TA know your repository URL and your student ID together via Slack.
* R5. Check out `test_analyzer1.py` to figure out the output format.
* R6. Assume that there are no nested classes/methods and anonymous classes.
* R7. Assume that there are no nested directories in the input path.
* R8. The function `collectAccessMapFromPath` takes a path of a directory containing multiple java source code files, and produce a map of accessed member variables of all member methods for each class in the directory as follows:
```
{'SystemUtils':
  {"getEnvironmentVariable['String', 'String']": set(),
   'getHostName[]': {'IS_OS_WINDOWS'},
   ...
  }
```
when the corresponding source code looks like:
```
public static String getEnvironmentVariable(final String name, final String defaultValue) {
    try {
        final String value = System.getenv(name);
        return value == null ? defaultValue : value;
    } catch (final SecurityException ex) {
        // we are not allowed to look at this property
        // System.err.println("Caught a SecurityException reading the environment variable '" + name + "'.");
        return defaultValue;
    }
}
public static String getHostName() {
    return IS_OS_WINDOWS ? System.getenv("COMPUTERNAME") : System.getenv("HOSTNAME");
}
```
* R9: If no member variable is accessed by a method, the value should be an empty set.
* R10: The return value of `collectAccessMapFromPath` should be:
```
{ "class1": {"method1": {"var1", ...}, "method2": ... }, "class2": ...}
```
* R11: As there are many overloaded methods, each method should be represented with the form of `method_name["param_type1", "param_type2", ...]` when the method signature is given as `method_name(param_type1 var1, param_type2 var2, ...)`.


## Note:

* N1. `pytest` (based on `test_analyzer1.py`) is just for validating your program. The final grading will be made by other test cases.
* N2. Submissions via GitHub Classroom will only be accepted. Submissions via LMS or any other means are not accepted.
* N3. DO NOT change files in this repository except for `app_analyzer.py`. Adding new files are allowed.
* N4. Late submissions after 2:45pm are *NOT* allowed.
