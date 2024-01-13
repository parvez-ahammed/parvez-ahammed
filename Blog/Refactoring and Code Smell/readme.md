
# Refactoring

## What is refactoring?

Refactoring is a disciplined technique for restructuring an existing body of code, altering its internal structure without changing its external behavior

## What does refactoring does?
1. It doesn't fix a 
2. helps finding the bug
3. Does not add a new feature
4. Makes code easier to understand

## Why we write code?
1. Technical debt
    
    a. Intentional
    
    b. Unintentional

2. Ignorance or will do it later attittude


## When refactoring needed?

+ When there is no idea what the code does 
+ When the code is understood but the question of "Why this way arises"
+ After fixing a bug
+ After adding a feature
+ Performance Optimization
+ Readability of code
+ platform of framework changes

## Work flow of refractoring

```mermaid

graph LR
    RED[Write tests that fail] --> Green[Write code that passes the tests]
    Green --> Refactor[Optimise the code]
    Refactor --> RED[Repeat]
```

## Example of Refactoring

### Composing Methods

- Extract Method
- Inline Method
- Inline Temp
- Replace Temp with Query
- Introduce Explaining variables
- Split Temporary Variable
- Remove Assignments to Parameters
- Replace Method with Method Object
- Substitute Algorithm

### Moving Features Between Objects
- Move Method
- Move Field
- Extract Class
- Inline Class
- Hide Delegate
- Remove Middle Man
- Introduce Foreign Man
- Introduce Local Extension

### Organizing Data
- Self Encapsulate Field
- Replace Data Value with Object
- Change Value to Reference 
- Change Reference to Value
- Replace Array with Object
- Duplicate Observed Data
- Encapsulate Field 
- Encapsulate Collection
- Replace Subclass with Fields

### Simplifying Conditional Expressions
- Decompose Conditional
- Remove Control Flag
- Replace Conditional with Polymorphism
- Introduce Null Object
- Introduce Assertion

### Making Method Calls Simpler
- Rename Method
- Add Parameter
- Remove Parameter
- Parameterized Method
- Preserve Whole Object
- Replace Parameter with Object
- Introduce Parameter Object
- Remove Setting Method
- Hide Method

### Dealing with Generalization
- Pull Up Field/Method/Constructor Body
- Push Down Field/Method
- Extract Subclass/Superclass/Interface
- Collapse Hierarchy
- Form Template Method
- Replace Inheritance with Delegation
- Replace Delegation with Inheritance


# OOP

## OOP Principles
The four principles of object-oriented programming are

1. `Inheritance` - The advantage of inheritance is that we define a more generic class and then we go with as many sub-classes as we need. The sub-classes inherit the properties and methods of the parent class. This way we can reuse the code and add new features to the sub-classes.<br>
This also ensures that the code is more readable and maintainable. We can also override the methods of the parent class in the sub-classes. This is called method overriding. So sometime we can merge multiple classes into one class and use inheritance to reuse the code and sometimes we can split a class into multiple classes and use inheritance to add new features to the sub-classes. 

2. `Encapsulation` - It means that we are keeping the information within the class but only revealing what's necessary to the outside world. This is done by using access modifiers. We can use public, private, protected and internal access modifiers to control the visibility of the members of a class. By applying encapsulation, we can make sure that the code is more maintainable and flexible. We can also use encapsulation to hide the implementation details of a class from the outside world. This is called information hiding.

3. `Abstraction` - It makes easier for use to work with only selected behaviours using simplified and high level overview of the object. It is done by using abstract classes and interfaces. We can use abstract classes to define a template for a class. We can then use this template to create new classes. We can also use interfaces to define a contract for a class. We can then use this contract to create new classes. By applying abstraction, we can make sure that the code is more maintainable and flexible. We can also use abstraction to hide the implementation details of a class from the outside world. This is called information hiding.

4. `Polymorphism` - It means that we can have multiple classes that can be used interchangeably. This is done by using inheritance, abstract classes and interfaces. We can use inheritance to create a more generic class and then we can use this class to create more specific classes. We can then use these specific classes interchangeably. We can also use abstract classes and interfaces to create a contract for a class. We can then use this contract to create more specific classes. We can then use these specific classes interchangeably. By applying polymorphism, we can make sure that the code is more readable and maintainable.


## Practical use of OOP Principles
# Code Smells

## Types of code smells with solutions

1. **Rename Field/Variable/Method Name:**



    
```java

public class Player {
    String n;

    public void s(String name) { 
        n = name;
    }

    public String g() { 
        return n;
    }
}

```

- Explanation: Poorly named elements in code can make it difficult to understand.
- Solution : Rename the field, variable, or method to something descriptive and meaningful, following established naming conventions.



    
```java

public class Player {
    private String playerName;

    public void setUserName(String name) {
        playerName = name;
    }

    public String getUserName() {
        return playerName;
    }
}

```


2. **Long Method:**



    
```java

public class GamePointProcessor {
    public void processPoint(String[] data) {
        for (String item : data) {
            if (item.isEmpty()) {
                System.out.println("Error: Data contains empty values.");
            }
        }

        for (int i = 0; i < data.length; i++) {
            data[i] = data[i].trim();
        }

        int[] transformedData = new int[data.length];
        for (int i = 0; i < data.length; i++) {
            transformedData[i] = Integer.parseInt(data[i]);
        }

        for (int value : transformedData) {
            if (value < 0) {
                System.out.println("Error: Negative values are not allowed.");
            }
        }

        int sum = 0;
        for (int value : transformedData) {
            sum += value;
        }

        System.out.println("Result: " + sum);

        if (sum > 100) {
            System.out.println("The sum is greater than 100.");
        } else {
            System.out.println("The sum is not greater than 100.");
        }

        if (transformedData.length > 0 && transformedData[0] == 0) {
            System.out.println("The first element in the transformed data is zero.");
        }

        System.out.println("Processing complete.");
    }
}

    
```
    

- Explanation : A method with excessive lines of code, making it hard to read and maintain.

- Solution: Break the long method into smaller, more focused methods with descriptive names that perform specific tasks.

```java

public class GamePointProcessor {
    public void processPoint(String[] data) {
        try {
            checkForEmptyValues(data);
            trimData(data);
            int[] transformedData = transformData(data);
            checkForNegativeValues(transformedData);
            int sum = calculateSum(transformedData);
            printResult(sum);
            printSumComparisonMessage(sum);
            checkAndPrintFirstElement(transformedData);
            printProcessingComplete();
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }

    private void checkForEmptyValues(String[] data) {
        for (String item : data) {
            if (item.isEmpty()) {
                throw new IllegalArgumentException("Data contains empty values.");
            }
        }
    }

    private void trimData(String[] data) {
        for (int i = 0; i < data.length; i++) {
            data[i] = data[i].trim();
        }
    }

    private int[] transformData(String[] data) {
        int[] transformedData = new int[data.length];
        for (int i = 0; i < data.length; i++) {
            transformedData[i] = Integer.parseInt(data[i]);
        }
        return transformedData;
    }

    private void checkForNegativeValues(int[] data) {
        for (int value : data) {
            if (value < 0) {
                System.out.println("Error: Negative values are not allowed.");
            }
        }
    }

    private int calculateSum(int[] data) {
        int sum = 0;
        for (int value : data) {
            sum += value;
        }
        return sum;
    }

    private void printResult(int sum) {
        System.out.println("Result: " + sum);
    }

    private void printSumComparisonMessage(int sum) {
        if (sum > 100) {
            System.out.println("The sum is greater than 100.");
        } else {
            System.out.println("The sum is not greater than 100.");
        }
    }

    private void checkAndPrintFirstElement(int[] data) {
        if (data.length > 0 && data[0] == 0) {
            System.out.println("The first element in the transformed data is zero.");
        }
    }

    private void printProcessingComplete() {
        System.out.println("Processing complete.");
    }
}

```

3. **Long Parameter List:**

```java

public class GamePointProcessor {
    public void processPoint(String[] data, int threshold, boolean isDebugMode, String dataLabel, String processingStep) {
        // Processing the data
    }
}
```
   - Explanation: Functions with too many parameters can be complex and error-prone.
   - Solution: Use parameter objects to group related parameters, or refactor the method to accept fewer parameters by encapsulating related data in objects.

```java
public class GamePointProcessor {
    public void processPoint(DataProcessingConfig config) {
        // Processing logic using the config object
        // ...
    }
}

public class DataProcessingConfig {
    private String[] data;
    private int threshold;
    private boolean isDebugMode;
    private String dataLabel;
    private String processingStep;

    public DataProcessingConfig(String[] data, int threshold, boolean isDebugMode, String dataLabel, String processingStep) {
        this.data = data;
        this.threshold = threshold;
        this.isDebugMode = isDebugMode;
        this.dataLabel = dataLabel;
        this.processingStep = processingStep;
    }

    // Getters for individual parameters if needed

    // Additional methods or validations as needed
}
```

4. **Large Class:**

```java

public class Game {
    private int playerScore;
    private String playerName;
    private String playerLocation;
    private int playerLevel;
    private int playerHealth;
    // ... (more attributes)

    public void playGame() {
        // Game logic here
    }

    public void saveGame() {
        // Save game logic here
    }

    public void loadGame() {
        // Load game logic here
    }

    public void displayPlayerInfo() {
        // Display player information logic here
    }

}


```
   - Explanation: A class that has grown too large and has too many responsibilities.
   - Solution: Divide the class into smaller classes, each responsible for a single aspect, using composition or inheritance if needed.

```java
public class Player {
    private int score;
    private String name;
    private String location;
    private int level;
    private int health;
    // ... (more attributes)

    // Constructor, getters, setters, and relevant methods
}

public class Game {
    private Player player;

    public void playGame() {
        // Game logic here
    }

    public void saveGame() {
        // Save game logic here
    }

    public void loadGame() {
        // Load game logic here
    }
}

public class PlayerInfoDisplay {
    private Player player;

    public PlayerInfoDisplay(Player player) {
        this.player = player;
    }

    public void displayPlayerInfo() {
        // Display player information logic here
    }
}


```



5. **Primitive Obsession:**


```java

public class Weapon {
    private String weaponType;
    private int damage;

    public Weapon(String weaponType, int damage) {
        this.weaponType = weaponType;
        this.damage = damage;
    }
}

```
   - Explanation: Overuse of primitive data types (e.g., strings, integers) instead of creating custom objects to represent concepts.

   - Solution: Create domain-specific classes to encapsulate related data and behavior, improving code clarity and maintainability.

```java

public class Weapon {
    private WeaponType weaponType;
    private int damage;

    public Weapon(WeaponType weaponType, int damage) {
        this.weaponType = weaponType;
        this.damage = damage;
    }
}

public enum WeaponType {
    SWORD,
    AXE,
    BOW,
    SPEAR
}

```

- This can also be an alternative 

```java
public class Weapon {
    private WeaponType weaponType;
    private Damage damage;

    public Weapon(WeaponType weaponType, Damage damage) {
        this.weaponType = weaponType;
        this.damage = damage;
    }

}

public class WeaponType {
    private String value;

    public WeaponType(String value) {
        // Validate and set the value
        this.value = value;
    }

    public String getValue() {
        return value;
    }

   
}

public class Damage {
    private int value;

    public Damage(int value) {
        // Validate and set the value
        this.value = value;
    }

    public int getValue() {
        return value;
    }

}


```



6. **Switch Statement:**
```java 

public class GameCharacter {
    private String characterType;

    public void attack() {
        switch (characterType) {
            case "Warrior":
                performWarriorAttack();
                break;
            case "Mage":
                performMageAttack();
                break;
            case "Archer":
                performArcherAttack();
                break;
            // ... (more cases)
            default:
                throw new IllegalArgumentException("Invalid character type");
        }
    }
}

```
   - Explanation: Overuse of switch/case statements can lead to code that's hard to extend and maintain.
   - Solution: Replace switch statements with polymorphism (e.g., using interfaces and subclasses) or create lookup tables to handle different cases more elegantly.
```java
public interface Character {
    void attack();
}

public class Warrior implements Character {
    // Warrior-specific attributes and methods
    @Override
    public void attack() {
        // Warrior attack logic
    }
}

public class Mage implements Character {
    // Mage-specific attributes and methods
    @Override
    public void attack() {
        // Mage attack logic
    }
}

public class Archer implements Character {
    // Archer-specific attributes and methods
    @Override
    public void attack() {
        // Archer attack logic
    }
}

// Usage example:
public class Game {
    public static void main(String[] args) {
        Character warrior = new Warrior();
        Character mage = new Mage();
        Character archer = new Archer();

        warrior.attack();
        mage.attack();
        archer.attack();
    }
}


```

7. **Duplicate Code:**

```java

public class GameCharacter {
    private int health;
    private int damage;

    public int getHealth() {
        return health;
    }

    public GameCharacter(int initialHealth, int initialDamage) {
        this.health = initialHealth;
        this.damage = initialDamage;
    }

    public void attack() {
        // Other additional logic
        System.out.println("Performing common attack");
        health -= 5;
        System.out.println("Health decreased by 5");
    }

    public void defend() {
        // Other additional logic
        System.out.println("Performing common defend");
        health -= 3;
        System.out.println("Health decreased by 3");
    }   
}


```

   - Explanation: Repeating the same code in multiple places in the codebase.
   - Solution: Extract duplicated code into reusable functions or methods to ensure consistency and maintainability.

```java 
public class GameCharacter {
    private int health;
    private int damage;

    public GameCharacter(int initialHealth, int initialDamage) {
        this.health = initialHealth;
        this.damage = initialDamage;
    }

    public void attack() {
        performAction("attack", 5);
    }

    public void defend() {
        performAction("defend", 3);
    }

    private void performAction(String action, int impact) {
        System.out.println("Performing common " + action);
        health -= impact;
        System.out.println("Health decreased by " + impact);
    }

    public int getHealth() {
        return health;
    }

}

```

8. **Lazy Class:**


```java

class Player {
    private String playerName;
    private PlayerInventory inventory;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.inventory = new PlayerInventory();
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: " + inventory.getInventoryInfo(); // Delegating to PlayerInventory
    }
}

class PlayerInventory {
    public String getInventoryInfo() {
        // Logic for retrieving inventory information
        return "Health Potions: 5, Weapons: 3";
    }
}


```
   - Explanation: Classes that don't provide much value and have too few responsibilities.
   - Solution: Remove or combine classes that don't contribute significantly to the system, redistributing their responsibilities to more relevant classes.
```java
class Player {
    private String playerName;
    private int health;
    private int healthPotions;
    private int weapons;

    public Player(String playerName, int initialHealth, int initialHealthPotions, int initialWeapons) {
        this.playerName = playerName;
        this.health = initialHealth;
        this.healthPotions = initialHealthPotions;
        this.weapons = initialWeapons;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health + ", Health Potions - " + healthPotions + ", Weapons - " + weapons;
    }
}

```
9. **Feature Envy:**

```java
class Player {
    private String playerName;
    private int health;
    private int healthPotions;
    private int weapons;

    public Player(String playerName, int initialHealth, int initialHealthPotions, int initialWeapons) {
        this.playerName = playerName;
        this.health = initialHealth;
        this.healthPotions = initialHealthPotions;
        this.weapons = initialWeapons;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health + ", Health Potions - " + healthPotions + ", Weapons - " + weapons;
    }
}

class PlayerEnvyFeatureChecker {
    public boolean isPlayerInGoodHealth(Player player) {
        // Feature envy: Excessive use of player's data
        int totalStats = player.health + player.healthPotions + player.weapons;
        return totalStats > 150; // Arbitrary condition for example
    }
}

```
   - Explanation: One class is excessively accessing or manipulating another class's features.
   - Solution: Refactor the code to move the functionality to the class that owns the data, promoting better encapsulation and modular design.

```java
class Player {
    private String playerName;
    private int health;
    private int healthPotions;
    private int weapons;

    public Player(String playerName, int initialHealth, int initialHealthPotions, int initialWeapons) {
        this.playerName = playerName;
        this.health = initialHealth;
        this.healthPotions = initialHealthPotions;
        this.weapons = initialWeapons;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health + ", Health Potions - " + healthPotions + ", Weapons - " + weapons;
    }

    public boolean isInGoodHealth() {
        int totalStats = health + healthPotions + weapons;
        return totalStats > 150; // Arbitrary condition for example
    }
}
```
10. **Temporary Field:**

```java
class Player {
    private String playerName;
    private int health;
    // Temporary field
    private int temporaryBuff;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
        this.temporaryBuff = 0;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + (health + temporaryBuff);
    }

    public void applyTemporaryBuff(int buffValue) {
        // Simulating the use of a temporary field for a specific situation
        this.temporaryBuff = buffValue;
    }
}
```
- Explanation: A class has fields that are only used in certain situations and aren't needed most of the time.
- Solution: Remove unnecessary fields or encapsulate them within methods or objects used during those specific situations.

```java 
class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        // Simulating the application of a temporary buff without a temporary field
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}
```

11. **Comments:**

```java 
class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }
    /*This is method that returns the player's stats as a string for display
     It returns the player's name and health as a string
     It is called when the player's stats need to be displayed
     It takes no parameters
    */
    public String xyz() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}
```
- Explanation: Excessive or unclear comments can indicate a lack of self-documenting code.

- Solution: Rewrite the code to be more expressive, use meaningful variable and method names, and only include comments when necessary for explaining complex or non-obvious logic.

```java 
class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }
    
    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}
```

12. **Inappropriate Intimacy:**

```java
public class Player {
    // Health is declared as public allowing other classes to directly access and modify it
    public String playerName;
    public int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }
    
    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}
```
- Explanation: Inappropriate relationships and dependencies between classes can lead to tight coupling and complexity.
- Solution: Refactor the code to reduce unnecessary relationships and encapsulate behavior where it belongs.

```java

public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = calculateBuffedHealth(buffValue);
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    private int calculateBuffedHealth(int buffValue) {
        return health + buffValue;
    }

    // Proper method to get the health value
    public int getHealth() {
        return health;
    }

    // Proper method to set the health value
    public void setHealth(int newHealth) {
        this.health = newHealth;
    }
}

```

13. **Shotgun Surgery:**

```java
public class Player {
    private String playerName;
    private int health;
    private int armor;

    public Player(String playerName, int initialHealth, int initialArmor) {
        this.playerName = playerName;
        this.health = initialHealth;
        this.armor = initialArmor;
    }
    
    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health + ", Armor - " + armor;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        int buffedArmor = armor + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth + ", Buffed Armor: " + buffedArmor);
    }
}
```
- Explanation: When a single change to the codebase requires multiple edits in various places, it indicates that changes are not localized.
- Solution: Reorganize the code to make it more cohesive, grouping related functionality together to reduce the need for widespread changes.

```java

public class Player {
    private String playerName;
    private Stats stats;

    public Player(String playerName, int initialHealth, int initialArmor) {
        this.playerName = playerName;
        this.stats = new Stats(initialHealth, initialArmor);
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: " + stats;
    }

    public void applyTemporaryBuff(int buffValue) {
        stats.applyBuff(buffValue);
        System.out.println("Temporary buff applied. " + stats);
    }
}

class Stats {
    private int health;
    private int armor;

    public Stats(int initialHealth, int initialArmor) {
        this.health = initialHealth;
        this.armor = initialArmor;
    }

    public void applyBuff(int buffValue) {
        this.health += buffValue;
        this.armor += buffValue;
    }

    @Override
    public String toString() {
        return "Health - " + health + ", Armor - " + armor;
    }
}

```

14. **Refused Bequest:**

```java
public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}

class AdvancedPlayer extends Player {
    private int specialAbility;

    public AdvancedPlayer(String playerName, int initialHealth, int initialSpecialAbility) {
        super(playerName, initialHealth);
        this.specialAbility = initialSpecialAbility;
    }

    // Refusing to use the applyTemporaryBuff method from the superclass
    @Override
    public void applyTemporaryBuff(int buffValue) {
        System.out.println("Advanced player's special ability activated!");
        // Special logic for applying buffs, ignoring the superclass behavior
    }
}
```
- Explanation: Subclasses inherit methods and attributes from a superclass but don't use or need them, leading to an awkward inheritance hierarchy.

- Solution: Refactor the class hierarchy, either by removing unnecessary inheritance or breaking the superclass into more meaningful components.
```java
public interface Player {
    String getCharacterStats();
    void applyTemporaryBuff(int buffValue);
}

public class BasicPlayer implements Player {
    private String playerName;
    private int health;

    public BasicPlayer(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    @Override
    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    @Override
    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}

public class AdvancedPlayer implements Player {
    private String playerName;
    private int specialAbility;

    public AdvancedPlayer(String playerName, int initialSpecialAbility) {
        this.playerName = playerName;
        this.specialAbility = initialSpecialAbility;
    }

    @Override
    public String getCharacterStats() {
        return playerName + "'s Stats: (Advanced Player)";
    }

    @Override
    public void applyTemporaryBuff(int buffValue) {
        System.out.println("Advanced player's special ability activated!");
        // Special logic for applying buffs
    }
}
```

15. **Middle Man:**

```java
public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    // Middle Man method
    public void displayCharacterStats() {
        System.out.println(getCharacterStats());
    }
}

```
- Explanation: Classes that serve as intermediaries between clients and the classes they interact with, offering little additional value.
- Solution: Directly access the classes or refactor the middle man to provide more meaningful services.

```java
public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}
```

16. **Data Class:**

```java
public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    // Accessors and mutators
    public String getPlayerName() {
        return playerName;
    }

    public void setPlayerName(String playerName) {
        this.playerName = playerName;
    }

    public int getHealth() {
        return health;
    }

    public void setHealth(int health) {
        this.health = health;
    }
}


```
- Explanation: Classes that only contain data without behavior, essentially acting as simple data structures.
- Solution: Add behavior to these classes to encapsulate the data's functionality, making the class more useful and expressive.
```java 

public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    public void takeDamage(int damage) {
        if (damage > 0) {
            health -= damage;
            System.out.println(playerName + " took damage. Remaining Health: " + health);
        }
    }

    
}

```

17. **Incomplete Library Class:**

```java

public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}

```
- Explanation: Library classes that lack important features or functionality, forcing developers to create their own solutions.
- Solution: Extend the library class to include missing features or choose a more comprehensive library.
```java

public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    public void dealDamage(int damage) {
        health -= damage;
        System.out.println("Player took damage. Remaining Health: " + health);
    }

    public void heal(int healingAmount) {
        health += healingAmount;
        System.out.println("Player healed. Updated Health: " + health);
    }

    public boolean isAlive() {
        return health > 0;
    }
}

```

18. **Data Clumps:**

```java

public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    // Data clump: playerName and health are frequently passed together
    public void dealDamage(int damage) {
        System.out.println(playerName + " took damage. Remaining Health: " + (health - damage));
    }

    // Data clump: playerName and health are frequently passed together
    public void heal(int healingAmount) {
        System.out.println(playerName + " healed. Updated Health: " + (health + healingAmount));
    }
}
```
- Explanation: When groups of data (e.g., parameters) frequently appear together in code, it suggests a missing object to encapsulate them.

- Solution: Create a class or object to group related data, improving code readability and maintainability.

```java

public class Player {
    private PlayerStats playerStats;

    public Player(String playerName, int initialHealth) {
        this.playerStats = new PlayerStats(playerName, initialHealth);
    }

    public String getCharacterStats() {
        return playerStats.getStats();
    }

    public void applyTemporaryBuff(int buffValue) {
        playerStats.applyBuff(buffValue);
    }

    public void dealDamage(int damage) {
        playerStats.takeDamage(damage);
    }

    public void heal(int healingAmount) {
        playerStats.heal(healingAmount);
    }
}

class PlayerStats {
    private String playerName;
    private int health;

    public PlayerStats(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    public void takeDamage(int damage) {
        health -= damage;
        System.out.println(playerName + " took damage. Remaining Health: " + health);
    }

    public void heal(int healingAmount) {
        health += healingAmount;
        System.out.println(playerName + " healed. Updated Health: " + health);
    }
}

```

19. **Speculative Generality:**

```java

public interface Character {
    String getCharacterStats();
    void applyBuff(int buffValue);
}

public class Player implements Character {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    @Override
    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    @Override
    public void applyBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}
```
- Explanation: Creating overly complex or abstract code with features that are not currently needed.
- Solution: Simplify the code by removing unused or unnecessary abstractions, refactoring as required when the need arises.

```java
public class Player {
    private String playerName;
    private int health;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health;
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }
}
```

20. **Message Chain:**
```java
public class Player {
    private String playerName;
    private int health;
    private Inventory inventory;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
        this.inventory = new Inventory();
    }

    public String getCharacterStats() {
        return playerName + "'s Stats: Health - " + health + ", Inventory - " + inventory.getInventoryInfo();
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    private class Inventory {
        private int healthPotions;
        private int weapons;

        public Inventory() {
            this.healthPotions = 5;
            this.weapons = 3;
        }

        public String getInventoryInfo() {
            return "Health Potions: " + healthPotions + ", Weapons: " + weapons;
        }
    }
}


```
- Explanation: A chain of method calls between objects, which can lead to tight coupling and reduce code maintainability.

- Solution: Introduce intermediate methods or encapsulate the chain in a single method to minimize the coupling and improve readability.

```java
public class Player {
    private String playerName;
    private int health;
    private Inventory inventory;

    public Player(String playerName, int initialHealth) {
        this.playerName = playerName;
        this.health = initialHealth;
        this.inventory = new Inventory();
    }

    public String getCharacterStats() {
        return inventory.getCharacterStats();
    }

    public void applyTemporaryBuff(int buffValue) {
        int buffedHealth = health + buffValue;
        System.out.println("Temporary buff applied. Buffed Health: " + buffedHealth);
    }

    private class Inventory {
        private int healthPotions;
        private int weapons;

        public Inventory() {
            this.healthPotions = 5;
            this.weapons = 3;
        }

        public String getCharacterStats() {
            return playerName + "'s Stats: Health - " + health + ", Inventory - Health Potions: " + healthPotions + ", Weapons: " + weapons;
        }
    }
}

```
Addressing these code smells can lead to cleaner, more maintainable, and more efficient code, ultimately improving software quality and development practices.




## References
+ Book - Refactoring: Improving the Design of Existing Code by Martin Fowler, Ken Beck
+ Refactoring Catalog: https://www.refactoring.com/catalog/index.html
+ Workflow of Refactoring: https://www.youtube.com/watch?v=vqEg37e4Mkw 
+ Book - Design Patterns: Elements of Reusable Object Oriented Software by Gangs of Four (GoF)
+ Refactoring Guru: https://refactoring.guru/ 
+ Source Making: https://sourcemaking.com/
+ Streams Tech Refactoring: https://www.youtube.com/watch?v=ToI4ZHqdDkg&list=PLi7ghxtNM46_s9p_6oxctq1IkRD6PxkfH  






