Vytvořte Java aplikaci, ve které budou aplikovány návrhové vzory Factory a Singleton.
# Kontext:
Vaším úkolem je vytvořit jednoduchý systém pro konfiguraci a objednávání automobilů v autosalonu. Každý zákazník má možnost nakonfigurovat svůj automobil pomocí různých parametrů, jako je typ motoru, barva karoserie nebo typ kol. Pro konfiguraci automobilů použijte návrhový vzor Builder. Třída reprezentující autosalon a obsahuje seznam objednaných automobilů musí být implementován jako Singleton, aby bylo zajištěno, že bude existovat pouze jedna jeho instance, která spravuje všechny objednávky.
# Požadavky:
Vaše implementace by měla zahrnovat dvě hlavní části:
Automobil s použitím návrhového vzoru Builder.
Autosalon s použitím návrhového vzoru Singleton.
## 1. Třída Car:
Vytvořte třídu Car, která bude mít následující atributy:

`engine (typ motoru, např. "1.0L", "1.4L", "1.6L", "2.0L", "Electric")
color (barva karoserie, např. "red", "blue", "black")
wheels (typ kol, např. "standard", "sport", "offroad")`

Pro konstrukci objektů třídy Car použijte návrhový vzor Builder. Použití builderu musí podporovat řetězení metod (tzv. fluent interface), tzn. že volání metod může probíhat stylem:

`Car.builder().setEngine(...).setColor(...).build();`

Vrámci implementace vytvořte třídu CarBuilder, která bude umožňovat nastavení jednotlivých atributů vozu.

Příklad použití:

`Car car = new Car.CarBuilder()
                .setEngine("2.0L")
                .setColor("red")
                .setWheels("sport")
                .build();`

## 2. Třída CarDealershipSingleton (Autosalon):
Vytvořte třídu CarDealershipSingleton, která bude spravovat objednávky automobilů. Tato třída musí být implementována jako Singleton, což zajistí, že bude vždy existovat pouze jedna instance autosalonu.
Metody autosalonu:
getInstance() – statická metoda, která vrátí jedinou instanci autosalonu.
orderCar(Car car) – metoda pro přijetí objednávky automobilu.
printOrders() – metoda, která vypíše všechny objednané automobily.

Příklad použití:

`CarDealershipSingleton dealership = CarDealershipSingleton.getInstance();
dealership.orderCar(car);`

## Testovací scénář:
Ve své implementaci vytvořte třídu Main, kde demonstrujete následující funkčnost:
Sestavte alespoň dva různé automobily pomocí návrhového vzoru Builder.
Tyto automobily objednejte v autosalonu, který je implementován jako Singleton.
Zobrazte seznam všech objednaných automobilů pomocí metody `printOrders().`

V Main metodě nelze získat instance `CarDealershipSingleton` jiným způsobem než pomocí metody `getInstance()`. Nelze volat konstruktor ~~new CarDealershipSingleton()~~ v rámci main metody. 

### Očekávané chování:
Při každé objednávce by měl být vypsán detail automobilu (např. motor, barva, kola).
Při volání metody `printOrders()` by se měl zobrazit seznam všech objednaných automobilů.

# Hodnocení:
- 1.5 bodu za správně implementovaný návrhový vzor Builder v třídě Car.
- 1.5 bodu za správně implementovaný návrhový vzor Singleton v třídě CarDealershipSingleton.
- 1 bod za přehlednost, čitelnost a správné komentování kódu.
- 1 bod za správné a funkční testovací scénáře v třídě Main.
