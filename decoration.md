# Decoration

> <small>This is an [AnimatedObject](objects#AnimatedObject)</small>

Anything that you may want to add to your scenery. For example, a simple barrel or a NPC that interacts with your player.

You can create decorative or interactive objects using the following builders:

Decoration with a common Sprite:
```dart
GameDecoration.withSprite(
    Future<Sprite> sprite, {
    required Vector2 position, // initial position in world
    required double height,
    required double width,
  })
```

Decoration with a SpriteAnimation:
```dart
import 'package:flame/animation.dart' as FlameAnimation;

GameDecoration.withAnimation(
    Future<SpriteAnimation> animation, {
    required Vector2 position, // initial position in world
    required double height,
    required double width,
  })
```

To add custom behaviors to your Decoration, just extend from `GameDecoration` and create your own class:
```dart
class MyCustomDecoration extends GameDecoration {
  MyCustomDecoration(Position position)
      : super.withAnimation(
          SpriteAnimation.load(
            "itens/chest_spritesheet.png",
            SpriteAnimationData.sequenced(
              amount: 8,
              stepTime: 0.1,
              textureSize: Vector2(16, 16),
            ),
          ),
          width: 32,
          height: 32,
          position: position,
        );

    @override
    void update(double dt) {
        // do anything
        super.update(dt);
    }

    @override
    void render(Canvas canvas) {
        // do anything
        super.render(canvas);
    }
}
```

See more examples of custom Decorations: [torch](https://github.com/RafaelBarbosatec/bonfire/blob/1.0.0-rc/example/lib/decoration/torch.dart) & [chest](https://github.com/RafaelBarbosatec/bonfire/blob/1.0.0-rc/example/lib/decoration/chest.dart)