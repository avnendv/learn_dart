```
  void main() {
    runApp(MaterialApp(
      home: SafeArea(
          child: Scaffold(
        appBar: AppBar(
          backgroundColor: Colors.red,
          title: const Text('Tự học Flutter'),
        ),
        body: const Center(
          child: Text('Hello World'),
        ),
      )),
      debugShowCheckedModeBanner: false, // hide dubug banner
    ));
  }
```
