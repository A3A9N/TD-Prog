---
Title: Class Diagram Tower Defense
---

```mermaid
classDiagram
    class GameManager {
        - int playerHealth
        - int resources
        + startGame()
        + endGame()
        + updateResources(int amount)
        + takeDamage(int damage)
    }

    class Tower {
        - int cost
        - float range
        - float fireRate
        + placeTower(Vector3 position)
        + attackEnemy(Enemy target)
    }

    class SniperTower {
        - float zoomLevel
        + specialAttack()
    }
    Tower <|-- SniperTower

    class Enemy {
        - float speed
        - int health
        - int damage
        + move()
        + takeDamage(int amount)
        + onDeath()
    }

    class FastEnemy {
        - float extraSpeed
    }
    Enemy <|-- FastEnemy

    class ArmoredEnemy {
        - int armor
    }
    Enemy <|-- ArmoredEnemy

    class HealerEnemy {
        + heal(Enemy target)
    }
    Enemy <|-- HealerEnemy

    class WaveSystem {
        - List<Enemy> activeEnemies
        + startNextWave()
        + spawnEnemy()
    }
    GameManager ..> WaveSystem

    class FieldOfView {
        - float angle
        - float radius
        + detectEnemies()
    }
    Tower ..> FieldOfView
    Enemy ..> FieldOfView

    class Projectile {
        - float speed
        - int damage
        + move()
        + hitTarget(Enemy target)
    }
    Tower ..> Projectile

    GameManager ..> Tower
    GameManager ..> Enemy
