---
Title: Class Diagram Tower Defense
---

```mermaid
classDiagram
    class EnemySpawner {
        - GameObject[] enemyPrefabs
        - int baseEnemies
        - float enemiesPerSecond
        - float timeBetweenWaves
        - float difficultyScalingFactor
        - int currentWave
        - float timeSinceLastSpawn
        - int enemiesAlive
        - int enemiesLeftToSpawn
        - bool isSpawning
        + UnityEvent onEnemyDestroy
        + void Awake()
        + void Start()
        + void Update()
        + void EnemyDestroyed()
        + IEnumerator StartWave()
        + void EndWave()
        + void SpawnEnemy()
        + int EnemiesPerWave()
    }

    class MainMenu {
        + void PlayGame()
        + void OpenSettings()
        + void QuitGame()
    }

    class Menu {
        - TextMeshProUGUI currencyUI
        - Animator anim
        - bool isMenuOpen
        + void ToggleMenu()
        + void OnGUI()
        + void SetSelected()
    }

    class MenuMovement {
        - float mousePosX
        - float mousePosY
        + void Start()
        + void Update()
    }

    class GameMusicManager {
        - AudioSource gameMusic
        - float fadeDuration
        - float targetVolume
        + void Start()
        + IEnumerator FadeIn(AudioSource audioSource, float duration, float targetVolume)
    }

    class LevelManager {
        + static LevelManager main
        + Transform startPoint
        + int currency
    }

    class EnemyMovement {
        + void Initialize(EnemySpawner spawner)
        + void AnimationUpdate()
    }

    class Archer {
        - Bullet bulletPrefab
        + void Shoot()
    }

    class Bullet {
        + void Move()
        + void OnCollision()
    }

    class Health {
        + UnityEvent onDeath
        + void TakeDamage()
    }

    EnemySpawner --> EnemyMovement : Spawns
    EnemySpawner --> Health : Registers Death
    EnemySpawner --> LevelManager : Accesses StartPoint
    MainMenu --> LevelManager : Accesses Currency
    Menu --> LevelManager : Accesses Currency
    Menu --> Animator : Controls
    GameMusicManager --> AudioSource : Controls Volume
    Archer --> Bullet : Fires
