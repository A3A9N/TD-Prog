Hier zijn al die scripts die staan op de Class Diagram en hun logica, en hier de link naar al mij scripts van de TD: https://github.com/A3A9N/TowerdefenseAdukos/tree/main/Assets/Code/Scripts

GameManager(BuildManager, LevelManager:
Dit script beheert het spel zelf: de resources, de levens van de speler, en de algemene controle over win- of verliescondities.

Tower/plot:
De basisclass voor alle torens, met attributen zoals kosten, bereik (range), en vuursnelheid (fireRate). Dit script bevat methoden voor het plaatsen van een toren en aanvallen van vijanden.

SniperTower:
Een subklasse van Tower, die een unieke aanvalsmethode heeft (bijvoorbeeld een special attack).

Enemy(EnemyMovement:
De basisclass voor vijanden, met attributen zoals movement levens, en schade (damage). Bevat methoden zoals move(), takeDamage(), en onDeath().

Archer, SniperArcher:
Subclasses van Archer, elk met unieke eigenschappen of gedrag:

Archer: Het is basic met normale snelheid en verstand atack.
SniperArcher: Is langzamer maar schiet van verder.

WaveSystem(Het is de LevelManager.cs script)
Beheert het spawnsysteem van vijanden en de golven in het spel. Verantwoordelijk voor het starten van een nieuwe golf en het spawnen van vijanden.

FieldOfView( Archer.cs):
Een script dat verantwoordelijk is voor het detecteren van vijanden binnen een bepaald bereik en hoek (Field of View). Dit wordt gebruikt door torens en kan interacties met vijanden beheren.

Bullet:
Beheert projectielen die door torens worden afgevuurd, inclusief de beweging en impact op vijanden.
