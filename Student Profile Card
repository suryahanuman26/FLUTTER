import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Student Profile Card',
      home: Scaffold(
        backgroundColor: Color(0xffdccfda),
        appBar: AppBar(
          title: const Text('Student Profile Card'),
          centerTitle: true,
          backgroundColor: Colors.blue,
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              CircleAvatar(
                radius: 55,
                backgroundColor: Colors.blue,
                child: const CircleAvatar(
                  radius: 50,
                  backgroundImage: AssetImage('assets/images/vishnu_logo.jpg'),
                ),
              ),
              const SizedBox(height: 20),
              const Text(
                'Student Name: Saimpu Karthik',
                style: TextStyle(
                  fontSize: 22,
                  fontWeight: FontWeight.bold,
                ),
              ),
              const SizedBox(height: 10),
              const Text(
                'Roll Number: 24pa1a05k3',
                style: TextStyle(fontSize: 18),
              ),
              const SizedBox(height: 10),
              const Text(
                'Branch: CSE',
                style: TextStyle(fontSize: 18),
              ),
              const SizedBox(height: 30),
              Container(
                width: 320,
                margin: const EdgeInsets.symmetric(vertical: 8),
                padding: const EdgeInsets.all(15),
                decoration: BoxDecoration(
                  color: Colors.white,
                  borderRadius: BorderRadius.circular(15),
                  boxShadow: const [
                    BoxShadow(
                      color: Colors.grey,
                      blurRadius: 6,
                      offset: Offset(2, 2),
                    ),
                  ],
                ),
                child: const Row(
                  children: [
                    Icon(
                      Icons.phone,
                      color: Colors.green,
                    ),
                    SizedBox(width: 15),
                    Text(
                      '9876543210',
                      style: TextStyle(fontSize: 18),
                    ),
                  ],
                ),
              ),
              Container(
                width: 320,
                margin: const EdgeInsets.symmetric(vertical: 8),
                padding: const EdgeInsets.all(15),
                decoration: BoxDecoration(
                  color: Colors.white,
                  borderRadius: BorderRadius.circular(15),
                  boxShadow: const [
                    BoxShadow(
                      color: Colors.grey,
                      blurRadius: 6,
                      offset: Offset(2, 2),
                    ),
                  ],
                ),
                child: const Row(
                  children: [
                    Icon(
                      Icons.email,
                      color: Colors.red,
                    ),
                    SizedBox(width: 15),
                    Text(
                      '24pa1a05k3@vishnu.edu.in',
                      style: TextStyle(fontSize: 18),
                    ),
                  ],
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
