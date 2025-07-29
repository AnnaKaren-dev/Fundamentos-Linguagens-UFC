# Modelo de uma hierarquia simples de classes em Python

```python
# Classe base
class Transport:
    def __init__(self, name, capacity):
        self.name = name
        self.capacity = capacity

    def move(self):
        print(f"{self.name} está se movendo.")

# Subclasse para transporte terrestre
class Land(Transport):
    def move(self):
        print(f"{self.name} está se movendo por terra.")

class Car(Land):
    def honk(self):
        print("Buzina: Beep beep!")

class Motorcycle(Land):
    def wheelie(self):
        print("A moto está empinando!")

# Subclasse para transporte aquático
class Water(Transport):
    def move(self):
        print(f"{self.name} está navegando.")

class Boat(Water):
    def anchor(self):
        print("O barco ancorou.")

# Subclasse para transporte aéreo
class Air(Transport):
    def move(self):
        print(f"{self.name} está voando.")

class Airplane(Air):
    def takeoff(self):
        print("O avião decolou.")

# Teste das classes
car = Car("Fusca", 4)
car.move()
car.honk()

boat = Boat("Lancha", 8)
boat.move()
boat.anchor()

airplane = Airplane("Boeing 737", 180)
airplane.move()
airplane.takeoff()

```

---

## Modelo Entidade-Relacionamento (MER)

Transport (
  TransportId INT PK NOT NULL,
  Name VARCHAR(100) NOT NULL,
  Capacity INT NOT NULL,
  Type TINYINT NOT NULL
)
   |
   |-- Car (
        CarId INT PK NOT NULL,
        TransportId INT FK NOT NULL,
        Model VARCHAR(50) NOT NULL,
        Nwheels INT NOT NULL
   )
   |
   |-- Motorcycle (
        MotorcycleId INT PK NOT NULL,
        TransportId INT FK NOT NULL,
        enginecc INT NOT NULL
   )
   |
   |-- Boat (
        idboat INT PK NOT NULL,
        TransportId INT FK NOT NULL,
        boattype VARCHAR(50) NOT NULL
   )
   |
   |-- Airplane (
        idairplane INT PK NOT NULL,
        TransportId INT FK NOT NULL,
        flightrangekm INT NOT NULL
   )

![alt text](<MER.png>)
