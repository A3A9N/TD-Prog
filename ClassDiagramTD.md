---
Title: Class Diagram Tower Defense
---

```mermaid
classDiagram
    class LevelManager {
        - static LevelManager main
        - Transform startPoint
        - Transform[] path
        - int currency
        + IncreaseCurrency(int amount)
        + bool SpendCurrency(int amount)
    }

    class BuildManager {
        - static BuildManager main
        - Tower[] towers
        - int selectedBuild
        + Tower GetSelectedBuild()
        + void SetSelectedBuild(int selectedBuildIndex)
    }

    class Tower {
        - string name
        - int cost
        - GameObject prefab
        + Tower(string name, int cost, GameObject prefab)
    }

    class Plot {
        - SpriteRenderer sr
        - Color hoverColor
        - GameObject build
        - Color startColor
        + void OnMouseEnter()
        + void OnMouseExit()
        + void OnMouseDown()
    }

    class Archer {
        - LayerMask EnemyMask
        - GameObject bulletPrefab
        - Transform firePoint
        - float targetingRange
        - float fireRate
        - Transform target
        - float fireCooldown
        + void Update()
        + void FindTarget()
        + void Shoot()
    }

    class EnemyMovement {
        - Rigidbody2D rb
        - Animator anim
        - EnemySpawner enemySpawner
        - float moveSpeed
        - Transform target
        - int pathIndex
        + void Initialize(EnemySpawner spawner)
        + void Update()
        + void FixedUpdate()
    }

    class Health {
        - int hitPoints
        - Animator anim
        - int currencyWorth
        + UnityEvent onDeath
        + void TakeDamage(int damage)
    }

    class Bullet {
        - Rigidbody2D rb
        - float bulletSpeed
        - int bulletDamage
        - Transform target
        + void SetTarget(Transform target)
        + void FixedUpdate()
        + void OnCollisionEnter2D(Collision2D collision)
    }

    %% Relationships
    LevelManager <.. Plot : uses
    LevelManager <.. Archer : uses
    BuildManager <.. Plot : uses
    BuildManager <.. Tower : uses
    Plot o-- Tower : "builds"
    Archer o-- Bullet : "fires"
    Bullet <.. Health : damages
    EnemyMovement <.. LevelManager : uses path
    Health <.. LevelManager : increases currency

