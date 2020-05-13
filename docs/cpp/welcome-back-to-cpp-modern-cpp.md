---
title: Bienvenido de nuevo a C++ - Modern C++
description: Describe los nuevos modismos de programación en Modern C++ y sus fundamentos.
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 7d0fcb623162713b845107bbf00669af7ae5ca98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369503"
---
# <a name="welcome-back-to-c---modern-c"></a>Bienvenido de nuevo a C++ - Modern C++

Desde su creación, C++ se ha convertido en uno de los lenguajes de programación más utilizados en el mundo. Los programas bien escritos de C++ son rápidos y eficaces. El lenguaje es más flexible que otros idiomas: puede funcionar en los niveles más altos de abstracción, y hacia abajo a nivel del silicio. C++ suministra bibliotecas estándar altamente optimizadas. Permite el acceso a funciones de hardware de bajo nivel, para maximizar la velocidad y minimizar los requisitos de memoria. Con C++, puede crear una amplia gama de aplicaciones. Juegos, controladores de dispositivos y software científico de alto rendimiento. Programas integrados. Aplicaciones cliente de Windows. Incluso las bibliotecas y compiladores para otros lenguajes de programación se escriben en C++.

Uno de los requisitos originales para C++ era la compatibilidad con el lenguaje C. Como resultado, C++ siempre ha permitido la programación de estilo C, con punteros sin procesar, matrices, cadenas de caracteres terminadas en null y otras características. Pueden permitir un gran rendimiento, pero también pueden generar errores y complejidad. La evolución de C++ ha enfatizado características que reducen en gran medida la necesidad de utilizar modismos de estilo C. Las antiguas instalaciones de programación C están ahí cuando las necesita, pero con el código C++ moderno debe necesitarlas cada vez menos. El código C++ moderno es más simple, seguro, más elegante y tan rápido como siempre.

Las secciones siguientes proporcionan una visión general de las principales características de C++. A menos que se indique lo contrario, las características enumeradas aquí están disponibles en C++11 y versiones posteriores. En el compilador de Microsoft C++, puede establecer la opción del compilador [/std](../build/reference/std-specify-language-standard-version.md) para especificar qué versión del estándar se usará para el proyecto.

## <a name="resources-and-smart-pointers"></a>Recursos y punteros inteligentes

Una de las principales clases de errores en la programación de estilo C es la pérdida de *memoria.* Las fugas a menudo se deben a un error al llamar a **delete** para la memoria que se asignó con **new**. Modern C++ enfatiza el principio de adquisición de recursos es la *inicialización* (RAII). La idea es simple. Los recursos (memoria de montón, identificadores de archivo, sockets, etc.) deben *pertenecer* a un objeto. Ese objeto crea o recibe el recurso recién asignado en su constructor y lo elimina en su destructor. El principio de RAII garantiza que todos los recursos se devuelven correctamente al sistema operativo cuando el objeto propietario sale del ámbito.

Para admitir fácilmente los principios RAII, la biblioteca estándar C++ proporciona tres tipos de punteros inteligentes: [std::unique_ptr](../standard-library/unique-ptr-class.md), [std::shared_ptr](../standard-library/shared-ptr-class.md)y [std::weak_ptr](../standard-library/weak-ptr-class.md). Un puntero inteligente controla la asignación y eliminación de la memoria que posee. En el ejemplo siguiente se muestra una clase con un `make_unique()`miembro de matriz que se asigna en el montón en la llamada a . Las llamadas a **new** y `unique_ptr` **delete** se encapsulan mediante la clase. Cuando `widget` un objeto sale del ámbito, se invocará el destructor unique_ptr y liberará la memoria asignada para la matriz.  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Siempre que sea posible, utilice un puntero inteligente al asignar memoria del montón. Si debe utilizar los operadores new y delete explícitamente, siga el principio de RAII. Para obtener más información, consulte Duración de objetos y administración de [recursos (RAII).](object-lifetime-and-resource-management-modern-cpp.md)

## <a name="stdstring-and-stdstring_view"></a>std::string y std::string_view

Las cadenas de estilo C son otra fuente importante de errores. Mediante el uso de [std::string y std::wstring](../standard-library/basic-string-class.md), puede eliminar prácticamente todos los errores asociados con cadenas de estilo C. También obtiene el beneficio de las funciones miembro para buscar, anexar, anteponer, etc. Ambos están altamente optimizados para la velocidad. Al pasar una cadena a una función que solo requiere acceso de solo lectura, en C++17 puede usar [std::string_view](../standard-library/basic-string-view-class.md) para obtener una ventaja de rendimiento aún mayor.

## <a name="stdvector-and-other-standard-library-containers"></a>std::vector y otros contenedores de la Biblioteca Estándar

Todos los contenedores de la Biblioteca Estándar siguen el principio de RAII. Proporcionan iteradores para el recorrido seguro de los elementos. Además, están altamente optimizados para el rendimiento y se han probado a fondo para la corrección. Mediante el uso de estos contenedores, se elimina la posibilidad de errores o ineficiencias que se pueden introducir en estructuras de datos personalizadas. En lugar de matrices sin procesar, utilice [vector](../standard-library/vector-class.md) como contenedor secuencial en C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilice [map](../standard-library/map-class.md) `unordered_map`(not ) como contenedor asociativo predeterminado. Utilice [set](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md)y [multiset](../standard-library/multiset-class.md) para casos degenerados y múltiples.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Cuando la optimización del rendimiento es necesaria, considere utilizar:

- El tipo de [matriz](../standard-library/array-class-stl.md) al incrustar es importante, por ejemplo, como miembro de clase.

- Contenedores asociativos desordenados como [unordered_map](../standard-library/unordered-map-class.md). Estos tienen menor sobrecarga por elemento y búsqueda en tiempo constante, pero pueden ser más difíciles de usar correctamente y eficientemente.

- Ordenado `vector`. Para más información, vea [Algoritmos](../cpp/algorithms-modern-cpp.md).

No utilice matrices de estilo C. Para las API más antiguas que necesitan acceso directo `f(vec.data(), vec.size());` a los datos, utilice métodos de descriptor de acceso como en su lugar. Para obtener más información acerca de los contenedores, vea Contenedores de [biblioteca estándar C++](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algoritmos de la Biblioteca Estándar

Antes de asumir que necesita escribir un algoritmo personalizado para su programa, primero revise los [algoritmos](../standard-library/algorithm.md)de la biblioteca estándar C++ . La biblioteca estándar contiene una variedad cada vez mayor de algoritmos para muchas operaciones comunes, como la búsqueda, la ordenación, el filtrado y la aleatorización. La biblioteca de matemáticas es extensa. A partir de C++17, se proporcionan versiones paralelas de muchos algoritmos.

Estos son algunos ejemplos importantes:

- **for_each**, el algoritmo de recorrido predeterminado (junto con bucles basados en rangos).

- **transformar**, para la modificación in situ de los elementos contenedores

- **find_if**, el algoritmo de búsqueda predeterminado.

- **ordenar**, **lower_bound**, y los otros algoritmos de ordenación y búsqueda predeterminados.

Para escribir un comparador, utilice **<** *lambdas* con nombre estricto y use cuando pueda.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>auto en lugar de nombres de tipo explícitos

C++11 introdujo la palabra clave [auto](auto-cpp.md) para su uso en declaraciones de variables, funciones y plantillas. **auto** indica al compilador que deduzca el tipo del objeto para que no tenga que escribirlo explícitamente. **auto** es especialmente útil cuando el tipo deducido es una plantilla anidada:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Basado en rangos para bucles

La iteración de estilo C sobre matrices y contenedores es propensa a errores de indexación y también es tediosa de escribir. Para eliminar estos errores y hacer que el código sea más legible, use bucles basados en intervalos con contenedores de biblioteca estándar y matrices sin procesar. Para obtener más información, consulte [Range-based for statement](../cpp/range-based-for-statement-cpp.md).

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>expresiones constexpr en lugar de macros

Las macros en C y C++ son tokens procesados por el preprocesador antes de la compilación. Cada instancia de un token de macro se reemplaza por su valor o expresión definida antes de compilar el archivo. Las macros se utilizan normalmente en la programación de estilo C para definir valores constantes en tiempo de compilación. Sin embargo, las macros son propensas a errores y difíciles de depurar. En C+++ moderno, debe preferir las [variables constexpr](constexpr-cpp.md) para las constantes en tiempo de compilación:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Inicialización uniforme

En C+++ moderno, puede utilizar la inicialización de llaves para cualquier tipo. Esta forma de inicialización es especialmente conveniente al inicializar matrices, vectores u otros contenedores. En el ejemplo `v2` siguiente, se inicializa `S`con tres instancias de . `v3`se inicializa con tres `S` instancias de las que se inicializan mediante llaves. El compilador deduce el tipo de cada elemento `v3`en función del tipo declarado de .

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

Para obtener más información, consulte [Inicialización de llaves](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Mover semántica

Modern C++ proporciona semántica de movimiento, que permite eliminar copias de memoria *innecesarias.* En versiones anteriores del idioma, las copias eran inevitables en ciertas situaciones. Una operación de *movimiento* transfiere la propiedad de un recurso de un objeto al siguiente sin realizar una copia. Al implementar una clase que posee un recurso (como memoria de montón, identificadores de archivo, etc.), puede definir un constructor de *movimiento* y mover el operador de *asignación* para él. El compilador elegirá estos miembros especiales durante la resolución de sobrecargas en situaciones en las que no se necesita una copia. Los tipos de contenedor Biblioteca estándar invocan el constructor de movimiento en objetos si se define uno. Para obtener más información, vea [Mover constructores y mover operadores de asignación (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Expresiones lambda

En la programación de estilo C, una función se puede pasar a otra función mediante un puntero de *función*. Los punteros de función son inconvenientes de mantener y comprender. La función a la que se refieren se puede definir en otra parte del código fuente, lejos del punto en el que se invoca. Además, no son seguros para el tipo. C++ moderno proporciona objetos de *función,* clases que invalidan el operador [(),](function-call-operator-parens.md) lo que permite llamarlos como una función. La forma más conveniente de crear objetos de función es con [expresiones lambda](../cpp/lambda-expressions-in-cpp.md)en línea. En el ejemplo siguiente se muestra cómo utilizar una `for_each` expresión lambda para pasar un objeto de función, que la función invocará en cada elemento del vector:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

La expresión `[=](int i) { return i > x && i < y; }` lambda se puede leer como "función que toma un único argumento de tipo `int` y devuelve un booleano que indica si el argumento es mayor `x` y menor que `y`." Observe que las `x` `y` variables y desde el contexto circundante se pueden utilizar en la lambda. Especifica `[=]` que esas variables se *capturan* por valor; en otras palabras, la expresión lambda tiene sus propias copias de esos valores.

## <a name="exceptions"></a>Excepciones

C++ moderno hace hincapié en las excepciones en lugar de los códigos de error como la mejor manera de notificar y controlar las condiciones de error. Para obtener más información, consulte Prácticas recomendadas modernas de [C++ para excepciones y control](errors-and-exception-handling-modern-cpp.md)de errores.

## <a name="stdatomic"></a>std::atomic

Utilice la biblioteca estándar [c++ std::atomic](../standard-library/atomic-structure.md) struct y tipos relacionados para los mecanismos de comunicación entre subprocesos.

## <a name="stdvariant-c17"></a>std::variante (C++17)

Las uniones se utilizan normalmente en la programación de estilo C para conservar la memoria al permitir que los miembros de diferentes tipos ocupen la misma ubicación de memoria. Sin embargo, las uniones no son seguras para tipos y son propensas a errores de programación. C++17 introduce la clase [std::variant](../standard-library/variant-class.md) como una alternativa más robusta y segura a las uniones. La función [std::visit](../standard-library/variant-functions.md#visit) se puede utilizar `variant` para acceder a los miembros de un tipo de forma segura.

## <a name="see-also"></a>Consulte también

[Referencia del idioma C++](../cpp/cpp-language-reference.md)\
[Expresiones Lambda](../cpp/lambda-expressions-in-cpp.md)\
[Biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)\
[Tabla de conformidad de idioma de Microsoft C++](../overview/visual-cpp-language-conformance.md)
