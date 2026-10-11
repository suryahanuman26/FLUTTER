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
      title: 'Animation Demo',
      theme: ThemeData(
        primarySwatch: Colors.deepPurple,
      ),
      home: const HomeScreen(),
    );
  }
}

// ======================================================
// HOME SCREEN
// ======================================================

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  void openAnimation(
    BuildContext context,
    Widget page,
  ) {
    Navigator.push(
      context,
      MaterialPageRoute(
        builder: (context) => page,
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Flutter Animation Demo'),
        centerTitle: true,
      ),

      body: Center(
        child: Padding(
          padding: const EdgeInsets.all(20),

          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,

            children: [
              const Icon(
                Icons.animation,
                size: 90,
                color: Colors.deepPurple,
              ),

              const SizedBox(height: 20),

              const Text(
                'Animation Effects',
                style: TextStyle(
                  fontSize: 28,
                  fontWeight: FontWeight.bold,
                ),
              ),

              const SizedBox(height: 40),

              // FADE
              SizedBox(
                width: double.infinity,
                child: ElevatedButton(
                  onPressed: () {
                    openAnimation(
                      context,
                      const FadeAnimationScreen(),
                    );
                  },
                  child: const Text('Fade Animation'),
                ),
              ),

              const SizedBox(height: 15),

              // SLIDE
              SizedBox(
                width: double.infinity,
                child: ElevatedButton(
                  onPressed: () {
                    openAnimation(
                      context,
                      const SlideAnimationScreen(),
                    );
                  },
                  child: const Text('Slide Animation'),
                ),
              ),

              const SizedBox(height: 15),

              // SCALE
              SizedBox(
                width: double.infinity,
                child: ElevatedButton(
                  onPressed: () {
                    openAnimation(
                      context,
                      const ScaleAnimationScreen(),
                    );
                  },
                  child: const Text('Scale Animation'),
                ),
              ),

              const SizedBox(height: 15),

              // ROTATION
              SizedBox(
                width: double.infinity,
                child: ElevatedButton(
                  onPressed: () {
                    openAnimation(
                      context,
                      const RotationAnimationScreen(),
                    );
                  },
                  child: const Text('Rotation Animation'),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

// ======================================================
// 1. FADE ANIMATION
// ======================================================

class FadeAnimationScreen extends StatefulWidget {
  const FadeAnimationScreen({super.key});

  @override
  State<FadeAnimationScreen> createState() =>
      _FadeAnimationScreenState();
}

class _FadeAnimationScreenState
    extends State<FadeAnimationScreen>
    with SingleTickerProviderStateMixin {

  late AnimationController controller;
  late Animation<double> fadeAnimation;

  @override
  void initState() {
    super.initState();

    controller = AnimationController(
      vsync: this,
      duration: const Duration(seconds: 2),
    );

    fadeAnimation = Tween<double>(
      begin: 0.0,
      end: 1.0,
    ).animate(
      CurvedAnimation(
        parent: controller,
        curve: Curves.easeIn,
      ),
    );

    controller.forward();
  }

  @override
  void dispose() {
    controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Fade Animation'),
      ),

      body: Center(
        child: FadeTransition(
          opacity: fadeAnimation,

          child: const Icon(
            Icons.favorite,
            size: 150,
            color: Colors.red,
          ),
        ),
      ),
    );
  }
}

// ======================================================
// 2. SLIDE ANIMATION
// ======================================================

class SlideAnimationScreen extends StatefulWidget {
  const SlideAnimationScreen({super.key});

  @override
  State<SlideAnimationScreen> createState() =>
      _SlideAnimationScreenState();
}

class _SlideAnimationScreenState
    extends State<SlideAnimationScreen>
    with SingleTickerProviderStateMixin {

  late AnimationController controller;
  late Animation<Offset> slideAnimation;

  @override
  void initState() {
    super.initState();

    controller = AnimationController(
      vsync: this,
      duration: const Duration(seconds: 2),
    );

    slideAnimation = Tween<Offset>(
      begin: const Offset(-1.0, 0.0),
      end: Offset.zero,
    ).animate(
      CurvedAnimation(
        parent: controller,
        curve: Curves.easeOut,
      ),
    );

    controller.forward();
  }

  @override
  void dispose() {
    controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Slide Animation'),
      ),

      body: Center(
        child: SlideTransition(
          position: slideAnimation,

          child: Container(
            width: 200,
            height: 200,

            decoration: BoxDecoration(
              color: Colors.blue,
              borderRadius: BorderRadius.circular(20),
            ),

            child: const Center(
              child: Text(
                'SLIDE',
                style: TextStyle(
                  color: Colors.white,
                  fontSize: 30,
                  fontWeight: FontWeight.bold,
                ),
              ),
            ),
          ),
        ),
      ),
    );
  }
}

// ======================================================
// 3. SCALE ANIMATION
// ======================================================

class ScaleAnimationScreen extends StatefulWidget {
  const ScaleAnimationScreen({super.key});

  @override
  State<ScaleAnimationScreen> createState() =>
      _ScaleAnimationScreenState();
}

class _ScaleAnimationScreenState
    extends State<ScaleAnimationScreen>
    with SingleTickerProviderStateMixin {

  late AnimationController controller;
  late Animation<double> scaleAnimation;

  @override
  void initState() {
    super.initState();

    controller = AnimationController(
      vsync: this,
      duration: const Duration(seconds: 2),
    );

    scaleAnimation = Tween<double>(
      begin: 0.0,
      end: 1.0,
    ).animate(
      CurvedAnimation(
        parent: controller,
        curve: Curves.easeOutBack,
      ),
    );

    controller.forward();
  }

  @override
  void dispose() {
    controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Scale Animation'),
      ),

      body: Center(
        child: ScaleTransition(
          scale: scaleAnimation,

          child: const Icon(
            Icons.star,
            size: 180,
            color: Colors.orange,
          ),
        ),
      ),
    );
  }
}

// ======================================================
// 4. ROTATION ANIMATION
// ======================================================

class RotationAnimationScreen extends StatefulWidget {
  const RotationAnimationScreen({super.key});

  @override
  State<RotationAnimationScreen> createState() =>
      _RotationAnimationScreenState();
}

class _RotationAnimationScreenState
    extends State<RotationAnimationScreen>
    with SingleTickerProviderStateMixin {

  late AnimationController controller;
  late Animation<double> rotationAnimation;

  @override
  void initState() {
    super.initState();

    controller = AnimationController(
      vsync: this,
      duration: const Duration(seconds: 3),
    );

    rotationAnimation = Tween<double>(
      begin: 0.0,
      end: 1.0,
    ).animate(controller);

    controller.repeat();
  }

  @override
  void dispose() {
    controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Rotation Animation'),
      ),

      body: Center(
        child: RotationTransition(
          turns: rotationAnimation,

          child: const Icon(
            Icons.settings,
            size: 150,
            color: Colors.green,
          ),
        ),
      ),
    );
  }
}
