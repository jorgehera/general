# PRACTICA PYTHON

## Python básico:
No sé si esto lo entiendes bien pero por lo que me has dicho antes creo que no, te lo pongo por si acaso.

Python es un lenguaje orientado a objetos, en plan, tu vas a definir clases que pueden tener atributos y métodos. Luego en el código tu vas a declarar instancias específicas de las clases, y ese objeto es el que ejecuta el método. 
Los atributos que quieras que tenga una clase los defines en la funcion __intit__. Por ej:

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

    def saludar(self):
        print(f"Hola, me llamo {self.nombre} y tengo {self.edad} años.")

# luego en el la función main instancias de la clase Persona
persona1 = Persona("Ana", 25) # objeto de tipo persona
persona2 = Persona("Luis", 30) # objeto de tipo persona

# Usar el método saludar
persona1.saludar()
persona2.saludar()
```

En el ej de arriba ves que hay un print, que es lo que no quiere Óscar, lo que te decia antes de sobreescribir una función es lo siguiente:

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

    def __str__(self):
            return f"Persona: {self.nombre}, {self.edad} años"

persona1 = Persona("Ana", 25)
print(persona1) # esto imprimiria por pantalla: Persona Ana, 25 años
```



## Recomendaciones del Óscar easy
- Tener un clase para cada cosa, si dos clases repite código, extraerlo esa parte a una función, o intentar agrupar los métodos.
- Utilizar funciones y atributos privados, y en ese caso crear getters y setters. 
- No imprimir nada fuera de la interfaz, es decir, comprobar absolutamente todo.
- Programar pensando que todo va a fallar, e incluir respectivo control de errores. (si tienes que introducir un numero por pantalla, comprobar que se ha introducido, algo, si es un numero o otro tipo de carácter, si el numero es positivo o si es alguno en específico, etc.)
- Comentar el código (esto es posiblemente lo peor de la práctica jajaja pero si le pasas la función a Charlie no suele comentarla mal)



## Estructura del código

### Clase para "Interfaz gráfica"
Te dan la estructura en el pdf que me has mandado. 

```python
from dna_model import DNA
from dna_operations import DNAOperations
from dna_interface import DNAInterface
# Definimos la clase AppDNA, que será la interfaz gráfica
class AppDNA:
    def __init__(self):
        self.interface = DNAInterface()
        ... # Aquí puedes inicializar lo que sea necesario para la clase

    def ejecutar(self):
        while True:
            # Lógica del menú, llamado a métodos según la opción seleccionada
            opcion = self.interface.mostrar_menu() # Mostrar el menú y obtener la opción del usuario
            if opcion == 1:
                ... # (aquí sería necesario continuar con el resto del menú)

# Punto de entrada del programa (instancias un objeto de tipo interfaz y ejecutas los métodos que necesites)
if __name__ == "__main__":
 miApp = AppDNA()
 miApp.ejecutar()
 ...
```

(Aquí te tendrás que hacer métodos que reciban un número, ya con eso ejecutas ejecutas el método de las clases DNA y Repositorio que necesites.)



### Clase para "ADN" (modela el ADN)
Aquí te haces una clase ADN que tenga los atributos que necesites. En las diapositivas (pg.15) te dan una estructura base con una serie de métodos y atributos (falta un método, te lo pongo más adelante):

```python
class DNA:
    def __init__(self, num):
        self.dna_chain = ""
        self.freqs = {}
        self.dir = os.getcwd()

    def initialise(self, num): # aquí le pasas un número y creas la cadena y la guardas en self.dna_chain
        pass

    def validate(self):
        pass

    def mutate(self, num):
        pass

    def measure_freqs(self):
        pass

    def count_subseq(self, chain_in):
        pass

    def synth_complement(self):
        pass
```
Supuestamente debes de implementar métodos para todo esto (pg.7): 

Operations with DNA:
1. Re-generate your DNA chain
2. Validate DNA chain
3. Mutate DNA chain
4. Measure frequencies
5. Count subsequences
6. Synthesize and complement
7. Measure % GC’s

El 7 falta en el código de arriba, supongo que irá también ahí y se le has olvidado ponerlo.



### Clase para "Repositorio" (gestiona operaciones como guardar y borrar)
En esta clase te defines un método para operación. Creo que las que te pide son:
1. Create new DNA chain
2. Save DNA chain
3. Load DNA from disk
4. List all DNA
    - Devuelve una lista y en la interfaz lo imprimes.
5. Delete DNA info

```python
# En función de si tienes que pasarle alguna variable a algun método, lo añades a parte de 'self'
class Repositorio:
    def __init__(self):
        self.dna = ...
        self.atributo2 = ...

    def create_dna_chain(self, length):
        pass

    def save_dna_chain(self):
        pass

    def load_dna_from_disk(self):
        pass

    def list_all_dna_info(self):
        pass

    def delete_dna_info(self):
        pass

    def operations_with_dna(self):
        pass # dna.metodo()
```

