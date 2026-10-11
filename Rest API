import 'dart:convert';

import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;

void main() {
  runApp(const MyApp());
}


class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'REST API Demo',

      theme: ThemeData(
        primarySwatch: Colors.deepPurple,
      ),

      home: const HomeScreen(),
    );
  }
}



class HomeScreen extends StatefulWidget {
  const HomeScreen({super.key});

  @override
  State<HomeScreen> createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {

  List<dynamic> posts = [];

  bool isLoading = true;

  String errorMessage = '';

  @override
  void initState() {
    super.initState();

    fetchPosts();
  }



  Future<void> fetchPosts() async {
    try {
      final response = await http.get(
        Uri.parse(
          'https://jsonplaceholder.typicode.com/posts',
        ),
      );

      if (response.statusCode == 200) {
        setState(() {
          posts = jsonDecode(response.body);
          isLoading = false;
        });
      } else {
        setState(() {
          isLoading = false;
          errorMessage =
              'Failed to load data. Status code: '
              '${response.statusCode}';
        });
      }
    } catch (e) {
      setState(() {
        isLoading = false;
        errorMessage = 'Error: $e';
      });
    }
  }



  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('REST API Posts'),
        centerTitle: true,
      ),

      body: buildBody(),
    );
  }


  Widget buildBody() {

    if (isLoading) {
      return const Center(
        child: CircularProgressIndicator(),
      );
    }

    if (errorMessage.isNotEmpty) {
      return Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Icon(
              Icons.error,
              size: 60,
              color: Colors.red,
            ),

            const SizedBox(height: 20),

            Text(
              errorMessage,
              textAlign: TextAlign.center,
            ),

            const SizedBox(height: 20),

            ElevatedButton(
              onPressed: () {
                setState(() {
                  isLoading = true;
                  errorMessage = '';
                });

                fetchPosts();
              },
              child: const Text('Retry'),
            ),
          ],
        ),
      );
    }

    return RefreshIndicator(
      onRefresh: fetchPosts,

      child: ListView.builder(
        padding: const EdgeInsets.all(12),

        itemCount: posts.length,

        itemBuilder: (context, index) {
          final post = posts[index];

          return Card(
            margin: const EdgeInsets.only(
              bottom: 12,
            ),

            elevation: 4,

            child: Padding(
              padding: const EdgeInsets.all(16),

              child: Column(
                crossAxisAlignment:
                    CrossAxisAlignment.start,

                children: [

                  CircleAvatar(
                    child: Text(
                      '${post['id']}',
                    ),
                  ),

                  const SizedBox(height: 12),

                  Text(
                    post['title'],
                    style: const TextStyle(
                      fontSize: 19,
                      fontWeight: FontWeight.bold,
                    ),
                  ),

                  const SizedBox(height: 10),

                  Text(
                    post['body'],
                    style: const TextStyle(
                      fontSize: 16,
                      color: Colors.black87,
                    ),
                  ),
                ],
              ),
            ),
          );
        },
      ),
    );
  }
}
