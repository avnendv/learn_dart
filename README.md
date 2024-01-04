# LEARN DART BASIC

Source post: https://viblo.asia/p/dart-tour-lap-trinh-voi-dart-co-ban-1Je5ED4GlnL

1. Variable
  - Những kiểu dữ liệu trong dart: Numbers, Strings, Booleans, Lists, Sets, Maps, Runes, Symbols
  - Có 3 cách để khai báo biến: 
    - Dùng từ khóa var:
      ```
        var yourName = 'My name is dart';
      ```
    - Dùng từ khóa dynamic:
      ```
        dynamic yourName = 'My name is dart';
      ```
    - Chỉ rõ kiểu dữ liệu:
      ```
        String yourName = "My name is dart";
        String yourName; // null
      ```
  - Hằng số:
    - final là biến có thể set một lần.
    - const là compile-time constant.
    ```
      final name = 'Bob'; // Without a type annotation
      final String nickname = 'Bobby';
      name = 'Alice'; // Error: a final variable can only be set once.
      ---
      const bar = 1000000; // Unit of pressure (dynes/cm2)
      const double atm = 1.01325 * bar; // Standard atmosphere
      ---
      var foo = const [];
      final bar = const [];
      const baz = []; // Equivalent to `const []`

      foo = [1, 2, 3]; // Was const []
      baz = [42]; // Error: Constant variables can't be assigned a value.
    ```

2. Built-in types
  - Number:
    - Dart cung cấp 2 kiểu int và double là subtype của kiểu num cung cấp đầy đủ các toán tử cơ bản như +, -, * và /.
    ```
      // int
      var x = 1;
      var hex = 0xDEADBEEF;

      // double 
      var y = 1.1;
      var exponents = 1.42e5;

      // convert string to number
      var one = int.parse('1');
      var onePointTwo = double.parse('1.2');

      // convert number to string
      String oneString = 1.toString(); // "1"
      String piString = 3.14159.toString(); // "3.14159"
      String piStringFixed2 = 3.14159.toStringAsFixed(2); // "3.14"
    ```
  - Strings:
    ```
      var s1 = 'Single quotes work well for string literals.';
      var s2 = "Double quotes work just as well.";
      var s3 = 'It\'s easy to escape the string delimiter.';
      var s4 = "It's even easier to use the other delimiter.";

      // để chèn một biến hoặc một biểu thức vào chuỗi bằng ta dùng ${expression}
      var yourName = "Bob";
      var yourOld = 12;
      print("My name is $yourName. I'm $yourOld");

      // Nối chuỗi ta có thể dùng các chuỗi liền kề hoặc dùng toán tử +
      var s1 = 'String '
        'concatenation'
        " works even over line breaks.";
      var s2 = 'The + operator ' + 'works, as well.';

      // để khai báo chuỗi trên nhiều dòng, ta có thể dùng ''' hoặc """
      var s1 = '''
        You can create
        multi-line strings like this one.
      ''';

      var s2 = """This is also a
        multi-line string.""";
      ```
  - Boolean:
    ```
      // Check for an empty string.
      var fullName = '';
      assert(fullName.isEmpty);

      // Check for zero.
      var hitPoints = 0;
      assert(hitPoints <= 0);

      // Check for null.
      var unicorn;
      assert(unicorn == null);

      // Check for NaN.
      var iMeantToDoThis = 0 / 0;
      assert(iMeantToDoThis.isNaN);
    ```
  - Lists:
    ```
      var list = [1, 2, 3];

      // spread operator (...) và null-aware spread operator (...?), cung cấp một cách ngắn hơn để insert nhiều elements vào trong collection.
      var list = [1, 2, 3];
      var list2 = [0, ...list];
      // để tránh exception ta nên dùng null-aware spread operator (...?)
      var list;
      var list2 = [0, ...?list];
      assert(list2.length == 1);

      // collection if 
      var nav = [
        'Home',
        'Furniture',
        'Plants',
        if (promoActive) 'Outlet'
      ];

      // collection for 
      var listOfInts = [1, 2, 3];
      var listOfStrings = [
        '#0',
        for (var i in listOfInts) '#$i'
      ];
      assert(listOfStrings[1] == '#1');
    ```
  - Sets & Maps:
    ```
      // set
      var halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};
      Set<String> names = {}; // This works, too.

      // map 
      var gifts = {
        // Key:    Value
        'first': 'partridge',
        'second': 'turtledoves',
        'fifth': 'golden rings'
      };
      var names = {}; // Creates a map, not a set.
    ```

3. Functions
  ```
    int sum(int first, int second) {
      return first + second;
    }
    // or
    int sum(int first, int second) => first + second;
  ```
  - Named parameters:
    ```
      void main() {
        print("${sum(first: 1, second: 2)}"); // (1)
        print("${sum(second: 2, first: 1)}"); // (2)
        // both (1) and (2) are the same
      }

      int sum({int first, int second}) => first + second;

      // named parameters là một kiểu của optional parameter, có thể sử dụng @required annotation để chú thích rằng param đó là bắt buộc.
      sum(first: 1, second: 2);
      sum(first: 1); // Warning: The parameter 'second' is required 
      //Để dùng @required annotation, chúng ta phải có meta package và import package:meta/meta.dart.
    ```
  - Positional parameters:
    ```
      int sum(int first, int second, [int third]) {
        if(third != null) {
          return first + second + third;
        }
        return first + second;
      }

      // without the optional parameter
      sum(1, 2)

      // with the third parameter
      sum(1, 2, 3)
    ```
  - Default parameter values:
    ```
      void main() {
        print(sum1(1, 2)); // print: 3
        print(sum1(1, 2, 3)); // print: 6
        print(sum2(1, 2)); // print: 3
        print(sum2(1, 2, third: 3)); // print: 6
      }

      // Default parameter values with positional parameters
      int sum1(int first, int second, [int third = 0]) {
        return first + second + third;
      }

      // Default parameter values with named parameters
      int sum2(int first, int second, {int third = 0}) {
        return first + second + third;
      }
    ```

4. Operators
  - Type test operators: Dart cung cấp 3 operators: as, is, và is! dùng để ép và kiểu tra kiểu dữ liệu tại runtime.
    - as dùng để ép kiểu
    - is trả về true nếu đúng kiểu được chỉ ra.
    - is! trả về true nếu không đúng kiểu được chỉ ra.
    ```
      (emp as Person).firstName = 'Bob';
      // or 
      if (emp is Person) {
        // Type check
        emp.firstName = 'Bob';
      }
    ```
  - Conditional expressions: condition ? expr1 : expr2 , expr1 ?? expr2
  - Cascade notation (..): cho phép thực hiện chuỗi các operations trên cùng một object.
    ```
      querySelector('#confirm') // Get an object.
        ..text = 'Confirm' // Use its members.
        ..classes.add('important')
        ..onClick.listen((e) => window.alert('Confirmed!'));
      // as
      var button = querySelector('#confirm');
      button.text = 'Confirm';
      button.classes.add('important');
      button.onClick.listen((e) => window.alert('Confirmed!'));

      // Vì querySelector return một selector object. Vì vậy nó cho phép cascade notation hoạt động trên selector object này. Tuy nhiên hãy cẩn thận trong trường hợp
      var sb = StringBuffer();
      sb.write('foo')
        ..write('bar'); // Error: method 'write' isn't defined for 'void'.
    ```
  - Conditional member access: ?. (toán tử cho null-safely)

5. Control flow statements
  - if và else
    ```
      if (isRaining()) {
        you.bringRainCoat();
      } else if (isSnowing()) {
        you.wearJacket();
      } else {
        car.putTopDown();
      }
    ```
  - for loops
    ```
      var message = StringBuffer('Dart is fun');
      for (var i = 0; i < 5; i++) {
        message.write('!');
      }

      // for trong các collections
      var collection = [0, 1, 2];
      for (var x in collection) {
        print(x); // 0 1 2
      }
    ```

6. Exceptions
  ```
    throw FormatException('Expected at least 1 section');
    throw 'Out of llamas!';
  ```

7. Classes