---
title: '&lt;random&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 5738a1ea5ab950466f347090649e72471edf5608
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458292"
---
# <a name="ltrandomgt"></a>&lt;random&gt;

Define instalaciones para generar números aleatorios, lo que permite crear números aleatorios distribuidos de manera uniforme.

## <a name="requirements"></a>Requisitos

**Encabezado**: \<> aleatorio

**Espacio de nombres:** std

> [!NOTE]
> La \<Biblioteca > aleatoria utiliza la instrucción ' #include < initializer_list > '.

## <a name="summary"></a>Resumen

Un *generador de números aleatorios* es un objeto que crea una secuencia de valores seudoaleatorios. Un generador que crea valores distribuidos uniformemente en un rango especificado es un *generador de números aleatorios uniformes* (URNG). La clase de plantilla diseñada para actuar como URNG se conoce como *motor* si tal clase tiene determinados rasgos comunes (esto se abordará más adelante en este artículo). Un URNG se puede combinar (de hecho, suele combinarse) con una *distribución* si el URNG se pasa como un argumento al `operator()` de la distribución con el fin de generar valores que se distribuyen de la manera especificada por la distribución.

Estos vínculos llevan a las secciones principales de este artículo:

- [Ejemplos](#code)

- [Lista por categorías](#listing)

- [Motores y distribuciones](#engdist)

- [Comentarios](#comments)

### <a name="quick-tips"></a>Sugerencias

A continuación se muestran algunas sugerencias que deben tenerse en \<cuenta al usar > aleatorios:

- En la mayoría de los casos, los URNG generan bits sin formato a los que las distribuciones deben dar forma. (Una excepción significativa a este respecto es [std::shuffle()](../standard-library/algorithm-functions.md#shuffle), ya que usa un URNG directamente).

- No se puede llamar a una única creación de instancias de un URNG o distribución simultáneamente de forma segura, ya que la ejecución de un URNG o distribución es una operación de modificación. Para obtener más información, vea [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- Se ofrecen [definiciones de tipo predefinidas](#typedefs) de varios motores; esta es la manera preferida de crear un URNG si se usa un motor.

- El emparejamiento más útil en la mayoría de los casos es la del motor `mt19937` con `uniform_int_distribution`, tal y como se muestra en el [código de ejemplo](#code) que aparece más adelante en este artículo.

Hay muchas opciones entre las que elegir en el \<encabezado > aleatorio y cualquiera de ellas es preferible a la función `rand()`de tiempo de ejecución de C obsoleta. Para obtener información sobre qué es el `rand()` problema con \<y cómo el > aleatorio soluciona estas deficiencias, vea [este vídeo](https://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="code"></a> Ejemplos

En el ejemplo de código siguiente, se muestra cómo generar algunos números aleatorios (en este caso, cinco) con un generador creado con valores de inicialización no deterministas.

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

Aunque son números aleatorios de gran calidad y diferentes cada vez que se ejecuta este programa, no están incluidos necesariamente en un intervalo útil. Para controlar el intervalo, utilice una distribución uniforme, como se muestra en el siguiente código:

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

En el ejemplo de código siguiente, se muestra un conjunto más realista de casos de uso con generadores de números aleatorios distribuidos uniformemente que seleccionan aleatoriamente el contenido de un vector y una matriz.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

En este código se muestran dos aleatorizaciones distintas (la aleatorización de un vector de enteros y la selección aleatoria de una matriz de datos indexados) con una función de plantilla de prueba. En la primera llamada a la función de prueba usa el URNG no reiterativo, no propagable, no determinista y criptográficamente seguro `random_device`. En la segunda serie de pruebas se usa `mersenne_twister_engine` como URNG con un valor de inicialización constante de 32 bits, lo que significa que los resultados son reiterativos. En la tercera serie de pruebas se propaga `mersenne_twister_engine` con un resultado no determinista de 32 bits de `random_device`. En la cuarta serie de pruebas esto se expande por medio de una [secuencia de propagación](../standard-library/seed-seq-class.md) rellena con resultados de `random_device`, con lo que se consigue eficazmente una aleatoriedad no determinista de más de 32 bits (aunque sigue sin ser criptográficamente seguro). Siga leyendo para obtener más información.

## <a name="listing"></a> Lista por categorías

###  <a name="urngs"></a> Generadores de números aleatorios uniformes

A menudo, los URNG se describen según los siguientes aspectos:

1. **Duración del período**: número de iteraciones necesario para repetir la secuencia de números generada. Cuanto más largo, mejor.

2. **Rendimiento**: rapidez con que los números se generan y cantidad de memoria empleada. Cuanto menos, mejor.

3. **Calidad**: proximidad de la secuencia generada a números aleatorios auténticos. Esto se suele conocer como "*aleatoriedad*".

En las secciones siguientes se enumeran los generadores de números aleatorios uniformes ( \<URNG) proporcionados en el encabezado > aleatorio.

####  <a name="rd"></a> Generador no determinista

|||
|-|-|
|[random_device (Clase)](../standard-library/random-device-class.md)|Genera una secuencia aleatoria criptográficamente segura y no determinista mediante un dispositivo externo. Se suele usar para propagar un motor. Bajo rendimiento y calidad extremadamente alta. Para obtener más información, vea [Comentarios](#comments).|

####  <a name="typedefs"></a> Definiciones de tipo de motor con parámetros predefinidos

Para crear instancias de motores y adaptadores de motores. Para obtener más información, vea [Motores y distribuciones](#engdist).

- `default_random_engine` El motor predeterminado.

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b` Motor de Knuth.

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0` Motor estándar mínimo 1988 (Lewis, Goodman y Miller, 1969).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand` Motor estándar mínimo `minstd_rand0` actualizado (Park, Miller y Stockmeyer, 1993).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937` Motor de Mersenne twister de 32 bits (Matsumoto y Nishimura, 1998).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64` Motor de Mersenne twister de 64 bits (Matsumoto y Nishimura, 2000).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24` Motor RANLUX de 24 bits (Martin Lüscher y Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base` Usado como base para `ranlux24`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48` Motor RANLUX de 48 bits (Martin Lüscher y Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base` Usado como base para `ranlux48`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

####  <a name="eng"></a> Plantillas de motor

Las plantillas de motor se usan como URNG independientes o como motores base que se pasan a los [adaptadores de motor](#engadapt). Por lo general, se suelen crear instancias de ellas con una [definición de tipo de motor predefinida](#typedefs) y pasarse a una [distribución](#distributions). Para obtener más información, vea la sección [Motores y distribuciones](#engdist).

|||
|-|-|
|[linear_congruential_engine (Clase)](../standard-library/linear-congruential-engine-class.md)|Genera una secuencia aleatoria mediante un algoritmo congruencial lineal. Es la de mayor simpleza y calidad más baja.|
|[mersenne_twister_engine (Clase)](../standard-library/mersenne-twister-engine-class.md)|Genera una secuencia aleatoria mediante un algoritmo Mersenne Twister. La más compleja y de mayor calidad, salvo en el caso de la clase random_device. Rendimiento muy rápido.|
|[subtract_with_carry_engine (Clase)](../standard-library/subtract-with-carry-engine-class.md)|Genera una secuencia aleatoria mediante un algoritmo de resta llevando. Constituye una mejora con respecto a `linear_congruential_engine`, si bien la calidad y rendimiento son muy inferiores a `mersenne_twister_engine`.|

####  <a name="engadapt"></a> Plantillas de adaptador de motor

Los adaptadores de motor son plantillas que adaptan otros motores (base). Por lo general, se suelen crear instancias de ellas con una [definición de tipo de motor predefinida](#typedefs) y pasarse a una [distribución](#distributions). Para obtener más información, vea la sección [Motores y distribuciones](#engdist).

|||
|-|-|
|[discard_block_engine (Clase)](../standard-library/discard-block-engine-class.md)|Genera una secuencia aleatoria descartando valores devueltos por su motor base.|
|[independent_bits_engine (Clase)](../standard-library/independent-bits-engine-class.md)|Genera una secuencia aleatoria con un número específico de bits, para lo cual vuelve a empaquetar los bits de los valores que devuelve su motor base.|
|[shuffle_order_engine (Clase)](../standard-library/shuffle-order-engine-class.md)|Genera una secuencia aleatoria reordenando los valores que devuelve su motor base.|

[[Plantillas de motor](#eng)]

###  <a name="distributions"></a> Distribuciones de números aleatorios

En las secciones siguientes se enumeran las distribuciones proporcionadas en el \<encabezado de > aleatorio. Las distribuciones son un mecanismo de procesamiento posterior que suelen usar una salida de URNG como entrada y distribuir esa salida mediante una función de densidad de probabilidad estadística definida. Para obtener más información, vea la sección [Motores y distribuciones](#engdist).

#### <a name="uniform-distributions"></a>Distribuciones uniformes

|||
|-|-|
|[uniform_int_distribution (Clase)](../standard-library/uniform-int-distribution-class.md)|Genera una distribución uniforme de valores enteros por un rango en el intervalo cerrado \[a, b] (inclusivo-inclusivo).|
|[uniform_real_distribution (Clase)](../standard-library/uniform-real-distribution-class.md)|Genera una distribución uniforme de valores reales (punto flotante) por un rango en el intervalo semiabierto [a, b) (inclusivo-exclusivo).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Genera una distribución uniforme de valores reales (punto flotante) de una determinada precisión a lo largo de [0, 1] (inclusivo-exclusivo).|

[[Distribuciones de números aleatorios](#distributions)]

#### <a name="bernoulli-distributions"></a>Distribuciones de Bernoulli

|||
|-|-|
|[bernoulli_distribution (Clase)](../standard-library/bernoulli-distribution-class.md)|Genera una distribución de Bernoulli de valores **bool** .|
|[binomial_distribution (Clase)](../standard-library/binomial-distribution-class.md)|Genera una distribución binomial de valores enteros.|
|[geometric_distribution (Clase)](../standard-library/geometric-distribution-class.md)|Genera una distribución geométrica de valores enteros.|
|[negative_binomial_distribution (Clase)](../standard-library/negative-binomial-distribution-class.md)|Genera una distribución binomial negativa de valores enteros.|

[[Distribuciones de números aleatorios](#distributions)]

#### <a name="normal-distributions"></a>Distribuciones normales

|||
|-|-|
|[cauchy_distribution (Clase)](../standard-library/cauchy-distribution-class.md)|Genera una distribución de Cauchy de valores reales (punto flotante).|
|[chi_squared_distribution (Clase)](../standard-library/chi-squared-distribution-class.md)|Genera una distribución chi-cuadrado de valores reales (punto flotante).|
|[fisher_f_distribution (Clase)](../standard-library/fisher-f-distribution-class.md)|Genera una distribución F (también conocida como distribución F de Snedecor o la distribución de Fisher-Snedecor) de valores reales (punto flotante).|
|[lognormal_distribution (Clase)](../standard-library/lognormal-distribution-class.md)|Genera una distribución log-normal de valores reales (punto flotante).|
|[normal_distribution (Clase)](../standard-library/normal-distribution-class.md)|Genera una distribución normal (Gaussiana) de valores reales (punto flotante).|
|[student_t_distribution (Clase)](../standard-library/student-t-distribution-class.md)|Genera una distribución *t* de Student de valores reales (punto flotante).|

[[Distribuciones de números aleatorios](#distributions)]

#### <a name="poisson-distributions"></a>Distribuciones de Poisson

|||
|-|-|
|[exponential_distribution (Clase)](../standard-library/exponential-distribution-class.md)|Genera una distribución de exponencial de valores reales (punto flotante).|
|[extreme_value_distribution (Clase)](../standard-library/extreme-value-distribution-class.md)|Genera una distribución de valores extremos de valores reales (punto flotante).|
|[gamma_distribution (Clase)](../standard-library/gamma-distribution-class.md)|Genera una distribución gamma de valores reales (punto flotante).|
|[poisson_distribution (Clase)](../standard-library/poisson-distribution-class.md)|Genera una distribución de Poisson de valores enteros.|
|[weibull_distribution (Clase)](../standard-library/weibull-distribution-class.md)|Genera una distribución de Weibull de valores reales (punto flotante).|

[[Distribuciones de números aleatorios](#distributions)]

#### <a name="sampling-distributions"></a>Distribuciones de muestreo

|||
|-|-|
|[discrete_distribution (Clase)](../standard-library/discrete-distribution-class.md)|Genera una distribución discreta de enteros.|
|[piecewise_constant_distribution (Clase)](../standard-library/piecewise-constant-distribution-class.md)|Genera una distribución constante a trozos de valores reales (punto flotante).|
|[piecewise_linear_distribution (Clase)](../standard-library/piecewise-linear-distribution-class.md)|Genera una distribución lineal a trozos de valores reales (punto flotante).|

[[Distribuciones de números aleatorios](#distributions)]

### <a name="utility-functions"></a>Funciones de utilidad

En esta sección se enumeran las funciones de utilidad \<generales que se proporcionan en el encabezado > aleatorio.

|||
|-|-|
|[seed_seq (Clase)](../standard-library/seed-seq-class.md)|Genera una secuencia de propagación codificada no inclinada. Sirve para evitar la replicación de flujos variados aleatorios. Resulta práctica cuando se crean instancias de muchos URNG desde los motores.|

### <a name="operators"></a>Operadores

En esta sección se enumeran los operadores \<que se proporcionan en el encabezado > aleatorio.

|||
|-|-|
|`operator==`|Comprueba si el URNG en el lado izquierdo del operador es igual al motor en el lado derecho.|
|`operator!=`|Comprueba si el URNG en el lado izquierdo del operador no es igual al motor en el lado derecho.|
|`operator<<`|Escribe información de estado en un flujo.|
|`operator>>`|Extrae información de estado de un flujo.|

## <a name="engdist"></a> Motores y distribuciones

Consulte las secciones siguientes para obtener información sobre cada una de estas categorías de clase de \<plantilla definidas en > aleatorio. Estas dos categorías de clase de plantilla toman un tipo como argumento y usan nombres compartidos de parámetros de plantilla para describir las propiedades del tipo que son posibles como tipo de argumento real, como se indica a continuación:

- `IntType`indica un **Short**, **int**, **Long**, **Long Long**, unsigned **Short**, unsigned **int**, unsigned **Long**o unsigned **Long Long**.

- `UIntType`indica **unsigned short**, **unsigned int**, unsigned **Long**o unsigned **Long Long**.

- `RealType`indica un valor de tipo **float**, **Double**o **Long Double**.

### <a name="engines"></a>Motores

Las [Plantillas de motor](#eng) y las [Plantillas de adaptador de motor](#engadapt) son plantillas cuyos parámetros personalizan el generador que se ha creado.

Un *motor* es una clase o clase de plantilla cuyas instancias (generadores) actúan como origen de números aleatorios distribuidos uniformemente entre un valor máximo y mínimo. Un *adaptador de motor* proporciona una secuencia de valores con distintas propiedades de aleatoriedad, para lo cual toma los valores generados por cualquier otro motor de números aleatorios y aplica a algunos de ellos un algoritmo de un tipo determinado.

Todos los motores y adaptadores de motor tienen los siguientes miembros:

- `typedef` `numeric-type` `result_type` es el tipo que el `operator()` del generador devuelve. El `numeric-type` se pasa como un parámetro de plantilla al crear las instancias.

- `result_type operator()` devuelve valores que se distribuyen de manera uniforme entre `min()` y `max()`.

- `result_type min()` devuelve el valor mínimo que el `operator()` del generador devuelve. Los adaptadores de motor usan el resultado `min()` del motor base.

- `result_type max()` devuelve el valor máximo que el `operator()` del generador devuelve. Cuando `result_type` es un tipo integral (con valor entero), `max()` es el valor máximo (inclusive) que se puede devolver realmente y, cuando `result_type` es un tipo de punto flotante (con valor real), `max()` es el valor más pequeño (ni inclusive) superior a todos los valores que se pueden devolver. Los adaptadores de motor usan el resultado `max()` del motor base.

- `void seed(result_type s)` propaga el generador con el valor de inicialización `s`. En los motores, la signatura es `void seed(result_type s = default_seed)` para la compatibilidad de parámetros predeterminada (los adaptadores de motor definen otro `void seed()`, consulte la siguiente subsección).

- `template <class Seq> void seed(Seq& q)` propaga el generador mediante [seed_seq](../standard-library/seed-seq-class.md)`Seq`.

- Un constructor explícito con el argumento `result_type x` que crea un generador propagado como si se llamara a `seed(x)`.

- Un constructor explícito con el argumento `seed_seq& seq` que crea un generador propagado como si se llamara a `seed(seq)`.

- `void discard(unsigned long long count)` llama eficazmente a `operator()``count` veces y descarta cada valor.

Los **adaptadores de motor** admiten también estos miembros (`Engine` es el primer parámetro de plantilla de un adaptador de motor y designa el tipo del motor base):

- Un constructor predeterminado para inicializar el generador como si se hiciera desde el constructor predeterminado del motor base.

- Un constructor explícito con el argumento `const Engine& eng`. Sirve para admitir una construcción de copia mediante el motor base.

- Un constructor explícito con el argumento `Engine&& eng`. Sirve para admitir una construcción de movimiento mediante el motor base.

- `void seed()` que inicializa el generador con el valor de inicialización predeterminado del motor base.

- Función de propiedad `const Engine& base()` que devuelve el motor base que se usó para construir el generador.

Cada motor mantiene un *estado* que indica la secuencia de valores que se va a generar a partir de las posteriores llamadas a `operator()`. Los estados de dos generadores de los que se crearon instancias desde motores del mismo tipo se pueden comparar mediante `operator==` y `operator!=`. Si dos estados comparados son iguales, generarán la misma secuencia de valores. El estado de un objeto se puede guardar en un flujo como una secuencia de valores sin signo de 32 bits mediante el `operator<<` del generador. El estado no se cambia al guardarlo. Un estado guardado se puede leer en el generador del que se creó la instancia desde un motor del mismo tipo mediante `operator>>`.

### <a name="distributions"></a>Distribuciones

Una [distribución de número aleatorio](#distributions) es una clase o una clase de plantilla cuyas instancias transforman una secuencia de números aleatorios distribuidos uniformemente obtenidos de un motor en una secuencia de números aleatorios que presenta una distribución particular. Todas las distribuciones tienen los siguientes miembros:

- `typedef` `numeric-type` `result_type` es el tipo que el `operator()` de la distribución devuelve. El `numeric-type` se pasa como un parámetro de plantilla al crear las instancias.

- `template <class URNG> result_type operator()(URNG& gen)` devuelve valores que se distribuyen según la definición de la distribución, para lo cual se usa `gen` como origen de los valores aleatorios distribuidos uniformemente y los *parámetros de la distribución* almacenados.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)` devuelve valores que se distribuyen según la definición de la distribución, para lo cual se usa `gen` como origen de los valores aleatorios distribuidos uniformemente y la estructura de parámetros `p`.

- `typedef` `unspecified-type` `param_type` es el paquete de parámetros que se pasa opcionalmente a `operator()` y que se usa en lugar de los parámetros almacenados para generar su valor de retorno.

- Un constructor `const param&` inicializa los parámetros almacenados desde su argumento.

- `param_type param() const` obtiene los parámetros almacenados.

- `void param(const param_type&)` establece los parámetros almacenados desde su argumento.

- `result_type min()` devuelve el valor mínimo que el `operator()` de la distribución devuelve.

- `result_type max()` devuelve el valor máximo que el `operator()` de la distribución devuelve. Cuando `result_type` es un tipo integral (con valor entero), `max()` es el valor máximo (inclusive) que se puede devolver realmente y, cuando `result_type` es un tipo de punto flotante (con valor real), `max()` es el valor más pequeño (ni inclusive) superior a todos los valores que se pueden devolver.

- `void reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.

Una estructura de parámetros es un objeto donde se almacenan todos los parámetros necesarios para una distribución. Contiene lo siguiente:

- `typedef` `distribution-type` `distribution_type`, que es el tipo de su distribución.

- Uno o más constructores que toman las mismas listas de parámetros que los constructores de la distribución.

- Las mismas funciones de acceso a parámetros que la distribución.

- Operadores de comparación de igualdad y desigualdad.

Para más información, vea los subtemas de referencia cuyos vínculos aparecen recogidos anteriormente en este artículo.

## <a name="comments"></a> Comentarios

Visual Studio dispone de dos URNG de extrema utilidad: `mt19937` y `random_device`, comparados en la siguiente tabla:

|URNG|Rápido|Seguro criptográficamente|Propagable|Determinista|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Sí|No|Sí|Sí<sup>*</sup>|
|`random_device`|Sin|Sí|Sin|Sin|

<sup>* Cuando se proporciona con un valor de inicialización conocido.</sup>

En Visual Studio, `random_device` se implementa de forma que es seguro criptográficamente, aunque la norma ISO C++ no lo requiera. (El término “seguro criptográficamente” no implica ninguna garantía, sino que hace referencia al nivel mínimo de entropía —y, por lo tanto, el grado de posibilidad de predicción— que proporciona un algoritmo de aleatorización. Para obtener más información, vea el artículo de la Wikipedia sobre el [generador de números seudoaleatorios seguros criptográficamente](https://go.microsoft.com/fwlink/p/?linkid=398017)). Dado que la norma ISO C++ no requiere esto, puede que otras plataformas implementen `random_device` como un generador de números seudoaleatorios simple (no seguro criptográficamente) que solo sea adecuado como origen de valores de inicialización para otro generador. Consulte la documentación de esas plataformas cuando use `random_device` en código con varias plataformas.

Por definición, los resultados de `random_device` no son reproducibles. Un efecto secundario de esto es que puede que se ejecute de forma significativamente más lenta que otros URNG. La mayoría de las aplicaciones que no tienen que ser seguras criptográficamente usan `mt19937` o un motor similar, aunque probablemente quiera propagarlo con una llamada a `random_device`, como se muestra en el [código de ejemplo](#code).

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
