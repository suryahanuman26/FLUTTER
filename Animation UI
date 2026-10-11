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
      title: 'Animated Named Routes Demo',

      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(
          seedColor: Colors.deepPurple,
        ),
        useMaterial3: true,
      ),

      initialRoute: '/',

      // Instead of using routes directly, onGenerateRoute allows us
      // to add custom animations between named routes.
      onGenerateRoute: (settings) {
        switch (settings.name) {
          case '/':
            return _createRoute(
              const HomeScreen(),
              AnimationType.fade,
            );

          case '/second':
            return _createRoute(
              const SecondScreen(),
              AnimationType.slide,
            );

          case '/third':
            return _createRoute(
              const ThirdScreen(),
              AnimationType.scale,
            );

          default:
            return _createRoute(
              const HomeScreen(),
              AnimationType.fade,
            );
        }
      },
    );
  }
}

// ----------------------------------------------------------
// ANIMATION TYPES
// ----------------------------------------------------------

enum AnimationType {
  fade,
  slide,
  scale,
}

// ----------------------------------------------------------
// CUSTOM ANIMATED ROUTE
// ----------------------------------------------------------

Route _createRoute(
  Widget page,
  AnimationType animationType,
) {
  return PageRouteBuilder(
    pageBuilder: (
      context,
      animation,
      secondaryAnimation,
    ) {
      return page;
    },

    transitionDuration: const Duration(milliseconds: 500),

    reverseTransitionDuration: const Duration(milliseconds: 400),

    transitionsBuilder: (
      context,
      animation,
      secondaryAnimation,
      child,
    ) {
      final curvedAnimation = CurvedAnimation(
        parent: animation,
        curve: Curves.easeInOut,
      );

      switch (animationType) {
        // Fade Animation
        case AnimationType.fade:
          return FadeTransition(
            opacity: curvedAnimation,
            child: child,
          );

        // Slide Animation
        case AnimationType.slide:
          const begin = Offset(1.0, 0.0);
          const end = Offset.zero;

          final tween = Tween<Offset>(
            begin: begin,
            end: end,
          ).chain(
            CurveTween(
              curve: Curves.easeInOutCubic,
            ),
          );

          return SlideTransition(
            position: animation.drive(tween),
            child: FadeTransition(
              opacity: animation,
              child: child,
            ),
          );

        // Scale Animation
        case AnimationType.scale:
          final scaleAnimation = Tween<double>(
            begin: 0.7,
            end: 1.0,
          ).animate(
            CurvedAnimation(
              parent: animation,
              curve: Curves.easeOutBack,
            ),
          );

          return ScaleTransition(
            scale: scaleAnimation,
            child: FadeTransition(
              opacity: animation,
              child: child,
            ),
          );
      }
    },
  );
}

// ==========================================================
// HOME SCREEN
// ==========================================================

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Home Screen'),
        centerTitle: true,
      ),

      body: Center(
        child: TweenAnimationBuilder<double>(
          tween: Tween(
            begin: 0,
            end: 1,
          ),
          duration: const Duration(milliseconds: 800),
          curve: Curves.easeOutBack,
          builder: (
            context,
            value,
            child,
          ) {
            return Transform.scale(
              scale: value,
              child: Opacity(
                opacity: value.clamp(0.0, 1.0),
                child: child,
              ),
            );
          },
          child: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              const Icon(
                Icons.home_rounded,
                size: 100,
                color: Colors.deepPurple,
              ),

              const SizedBox(height: 20),

              const Text(
                'Welcome Home',
                style: TextStyle(
                  fontSize: 28,
                  fontWeight: FontWeight.bold,
                ),
              ),

              const SizedBox(height: 40),

              ElevatedButton.icon(
                onPressed: () {
                  Navigator.pushNamed(
                    context,
                    '/second',
                  );
                },
                icon: const Icon(
                  Icons.arrow_forward,
                ),
                label: const Text(
                  'Go to Second Screen',
                ),
              ),

              const SizedBox(height: 20),

              ElevatedButton.icon(
                onPressed: () {
                  Navigator.pushNamed(
                    context,
                    '/third',
                  );
                },
                icon: const Icon(
                  Icons.animation,
                ),
                label: const Text(
                  'Go to Third Screen',
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

// ==========================================================
// SECOND SCREEN
// ==========================================================

class SecondScreen extends StatefulWidget {
  const SecondScreen({super.key});

  @override
  State<SecondScreen> createState() => _SecondScreenState();
}

class _SecondScreenState extends State<SecondScreen> {
  bool expanded = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Second Screen'),
        centerTitle: true,
      ),

      body: Center(
        child: Column(
          mainAxisSize: MainAxisSize.min,
          children: [
            // AnimatedContainer automatically animates
            // whenever its properties change.
            GestureDetector(
              onTap: () {
                setState(() {
                  expanded = !expanded;
                });
              },

              child: AnimatedContainer(
                duration: const Duration(
                  milliseconds: 600,
                ),
                curve: Curves.easeInOutBack,

                width: expanded ? 220 : 120,
                height: expanded ? 220 : 120,

                decoration: BoxDecoration(
                  color: expanded
                      ? Colors.deepPurple
                      : Colors.orange,

                  borderRadius: BorderRadius.circular(
                    expanded ? 40 : 100,
                  ),

                  boxShadow: [
                    BoxShadow(
                      color: Colors.black.withValues(
                        alpha: 0.2,
                      ),
                      blurRadius: expanded ? 20 : 8,
                      spreadRadius: expanded ? 5 : 1,
                    ),
                  ],
                ),

                child: Icon(
                  expanded
                      ? Icons.animation
                      : Icons.touch_app,
                  size: expanded ? 90 : 50,
                  color: Colors.white,
                ),
              ),
            ),

            const SizedBox(height: 25),

            const Text(
              'Tap the box to animate',
              style: TextStyle(
                fontSize: 18,
              ),
            ),

            const SizedBox(height: 40),

            ElevatedButton.icon(
              onPressed: () {
                Navigator.pop(context);
              },
              icon: const Icon(
                Icons.arrow_back,
              ),
              label: const Text(
                'Go Back',
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// ==========================================================
// THIRD SCREEN
// ==========================================================

class ThirdScreen extends StatefulWidget {
  const ThirdScreen({super.key});

  @override
  State<ThirdScreen> createState() => _ThirdScreenState();
}

class _ThirdScreenState extends State<ThirdScreen>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;

  late Animation<double> _rotationAnimation;
  late Animation<double> _scaleAnimation;

  @override
  void initState() {
    super.initState();

    _controller = AnimationController(
      vsync: this,
      duration: const Duration(
        seconds: 2,
      ),
    );

    _rotationAnimation = Tween<double>(
      begin: 0,
      end: 1,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeInOut,
      ),
    );

    _scaleAnimation = Tween<double>(
      begin: 0.7,
      end: 1.3,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeInOut,
      ),
    );

    // Repeat forward and backward.
    _controller.repeat(
      reverse: true,
    );
  }

  @override
  void dispose() {
    // AnimationController must be disposed.
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Third Screen'),
        centerTitle: true,
      ),

      body: Center(
        child: Column(
          mainAxisSize: MainAxisSize.min,
          children: [
            // Explicit animation using AnimationController.
            RotationTransition(
              turns: _rotationAnimation,
              child: ScaleTransition(
                scale: _scaleAnimation,
                child: const Icon(
                  Icons.flutter_dash,
                  size: 100,
                  color: Colors.blue,
                ),
              ),
            ),

            const SizedBox(height: 60),

            ElevatedButton.icon(
              onPressed: () {
                Navigator.pop(context);
              },
              icon: const Icon(
                Icons.arrow_back,
              ),
              label: const Text(
                'Go Back',
              ),
            ),

            const SizedBox(height: 20),

            ElevatedButton.icon(
              onPressed: () {
                Navigator.pushNamedAndRemoveUntil(
                  context,
                  '/',
                  (route) => false,
                );
              },
              icon: const Icon(
                Icons.home,
              ),
              label: const Text(
                'Go to Home',
              ),
            ),
          ],
        ),
      ),
    );
  }
}
