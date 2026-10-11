import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatefulWidget {
  const MyApp({super.key});

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  bool isEnabled = true;

  void enableButton() {
    setState(() {
      isEnabled = true;
    });
  }

  void disableButton() {
    setState(() {
      isEnabled = false;
    });
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: const Text("Enable Disable Example"),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              // Controlled Container
              Container(
                width: 250,
                height: 100,
                alignment: Alignment.center,
                decoration: BoxDecoration(
                  color: isEnabled ? Colors.green : Colors.grey,
                  borderRadius: BorderRadius.circular(15),
                ),
                child: Text(
                  isEnabled ? "Enabled" : "Disabled",
                  style: const TextStyle(
                    color: Colors.white,
                    fontSize: 25,
                  ),
                ),
              ),

              const SizedBox(height: 30),

              // Enable Button
              ElevatedButton(
                onPressed: enableButton,
                child: const Text("Enable"),
              ),

              const SizedBox(height: 15),

              // Disable Button
              ElevatedButton(
                onPressed: disableButton,
                child: const Text("Disable"),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
