# لعبة نصية بسيطة مستوحاة من Diablo II (باستخدام Python)
import random

class Character:
    def __init__(self, name, char_class):
        self.name = name
        self.char_class = char_class
        self.health = 100
        self.gold = 0

    def attack(self):
        damage = random.randint(5, 20)
        print(f"{self.name} يهاجم ويسبب {damage} نقطة ضرر!")
        return damage

    def take_damage(self, damage):
        self.health -= damage
        print(f"{self.name} يتلقى {damage} ضرر. الصحة المتبقية: {self.health}")

# بداية اللعبة
print("مرحبًا في عالم Diablo II المبسط!")
name = input("ادخل اسم شخصيتك: ")
char_class = input("اختر فئتك (مقاتل/ساحر): ")

player = Character(name, char_class)
print(f"\nتم إنشاء {player.name} الفئة {player.char_class}!")

# معركة مبسطة
monster_health = 30
print("\nظهر وحش! ابدأ المعركة.")

while monster_health > 0 and player.health > 0:
    input("\nاضغط Enter للهجوم...")
    damage = player.attack()
    monster_health -= damage
    print(f"صحة الوحش المتبقية: {monster_health}")

    if monster_health > 0:
        monster_damage = random.randint(3, 10)
        player.take_damage(monster_damage)

if player.health > 0:
    print("\nانتصرت! لقد جمعت 50 ذهب.")
    player.gold += 50
else:
    print("\nلقد هزمت... حاول مرة أخرى!")