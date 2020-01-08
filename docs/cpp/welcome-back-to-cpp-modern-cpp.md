---
title: Aquí está otra vez C++ (C++ moderno)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 4dee4779e941c66af1c23f62a88cecec4916a475
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301748"
---
# <a name="welcome-back-to-c-modern-c"></a>Aquí está otra vez C++ (C++ moderno)

En los últimos 25 años, C++ ha sido uno de los lenguajes de programación más utilizados en el mundo. Los programas bien escritos de C++ son rápidos y eficaces. El lenguaje es más flexible que otros lenguajes, ya que permite tener acceso a las características de hardware de bajo nivel para maximizar la velocidad y minimizar los requisitos de memoria. Puede usarlo para crear una amplia gama de aplicaciones, desde juegos, hasta software científico de alto rendimiento, controladores de dispositivos, programas incrustados, bibliotecas y compiladores para otros lenguajes de programación, aplicaciones cliente de Windows y mucho más.

Uno de los requisitos originales para C++ era la compatibilidad con el lenguaje C. Como resultado C++ , siempre ha permitido la programación de estilo C con punteros sin formato, matrices, cadenas de caracteres terminadas en null, estructuras de datos personalizadas y otras características que pueden permitir un gran rendimiento, pero también pueden generar errores y complejidad. La evolución de C++ tiene características destacadas que reducen en gran medida la necesidad de utilizar expresiones de estilo C. Los antiguos recursos de programación de C están allí cuando los necesita, pero con código C++ moderno debe necesitarlos menos y menos. El C++ código moderno es más sencillo, más seguro, más elegante y aún más rápido que nunca.

En las secciones siguientes se proporciona información general sobre las características principales C++de moderno. A menos que se indique lo contrario, las características que se enumeran aquí están disponibles en C++ 11 y versiones posteriores. En el compilador de Microsoft C++ , puede establecer la opción del compilador [/STD](../build/reference/std-specify-language-standard-version.md) para especificar la versión del estándar que se va a usar para el proyecto.

## <a name="raii-and-smart-pointers"></a>RAII y punteros inteligentes

Una de las clases principales de errores en la programación de estilo C es la *pérdida de memoria* debido a un error al llamar a **Delete** para la memoria asignada con **New**. Modern C++ destaca que el principio de *adquisición de recursos es la inicialización* , que indica que cualquier recurso (memoria del montón, identificadores de archivo, sockets, etc.) debe *pertenecer* a un objeto que crea o recibe el recurso que se acaba de asignar en su constructor y lo elimina en su destructor. Al cumplir el principio de RAII, garantiza que todos los recursos se devolverán correctamente al sistema operativo cuando el objeto propietario salga del ámbito. Para admitir la adopción sencilla de los principios de C++ RAII, la biblioteca estándar proporciona tres tipos de puntero inteligente: [std:: unique_ptr](../standard-library/unique-ptr-class.md), [STD:: shared_ptr](../standard-library/shared-ptr-class.md)y [STD:: weak_ptr](../standard-library/weak-ptr-class.md). Un puntero inteligente controla la asignación y eliminación de la memoria que posee. En el ejemplo siguiente se muestra una clase con un miembro de matriz que se asigna en el montón en la llamada a `make_unique()`. La clase `unique_ptr` encapsula las llamadas a **New** y **Delete** . Cuando un objeto `widget` sale del ámbito, se invocará el destructor unique_ptr y liberará la memoria asignada para la matriz.  

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

Siempre que sea posible, use un puntero inteligente al asignar memoria de montón. Si debe usar los operadores New y DELETE explícitamente, siga el principio de RAII. Para obtener más información, consulte [duración de objetos y administración de recursos (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>STD:: String y STD:: string_view

Las cadenas de estilo C son otra fuente principal de errores. Mediante [STD:: String y STD:: wstring](../standard-library/basic-string-class.md) , puede eliminar prácticamente todos los errores asociados a las cadenas de estilo C y beneficiarse de las funciones miembro para buscar, anexar, anteponer, etc. Ambos están muy optimizados para la velocidad. Al pasar una cadena a una función que solo requiere acceso de solo lectura, en C++ 17 puede usar [STD:: string_view](../standard-library/basic-string-view-class.md) para obtener una ventaja de rendimiento aún mayor.

## <a name="stdvector-and-other-standard-library-containers"></a>STD:: Vector y otros contenedores de la biblioteca estándar

Todos los contenedores de la biblioteca estándar siguen el principio de RAII, proporcionan iteradores para el recorrido seguro de los elementos, están optimizados para el rendimiento y se han probado exhaustivamente para comprobar su exactitud. Si se usan estos contenedores siempre que sea posible, se elimina la posibilidad de errores o ineficiencias que podrían introducirse en estructuras de datos personalizadas. De forma predeterminada, utilice [Vector](../standard-library/vector-class.md) como contenedor secuencial preferido en C++. Esto es equivalente a `List<T>` en lenguajes .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilice [map](../standard-library/map-class.md) (no `unordered_map`) como contenedor asociativo predeterminado. Utilice [set](../standard-library/set-class.md), [Multimap](../standard-library/multimap-class.md)y [MultiSet](../standard-library/multiset-class.md) para los casos degenerados y múltiples.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Cuando la optimización del rendimiento es necesaria, considere utilizar:

- El tipo de [matriz](../standard-library/array-class-stl.md) cuando la incrustación es importante, por ejemplo, como un miembro de clase.

- Contenedores asociativos desordenados como [unordered_map](../standard-library/unordered-map-class.md). Estos tienen menor sobrecarga por elemento y búsqueda de tiempo constante, pero pueden ser más difíciles de usar de forma correcta y eficaz.

- `vector`ordenadas. Para más información, vea [Algoritmos](../cpp/algorithms-modern-cpp.md).

No utilice matrices de estilo C. En el caso de las API más antiguas que necesiten acceso directo a los datos, use métodos de descriptor de acceso como `f(vec.data(), vec.size());` en su lugar. Para obtener más información acerca de los contenedores, vea [ C++ contenedores de la biblioteca estándar](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algoritmos de la biblioteca estándar

Antes de suponer que necesita escribir un algoritmo personalizado para el programa, revise primero los C++ [algoritmos](../standard-library/algorithm.md)de la biblioteca estándar. La biblioteca estándar contiene una serie de algoritmos en constante crecimiento para muchas operaciones comunes, como búsqueda, ordenación, filtrado y aleatoriedad. La biblioteca matemática es extensa. A partir de C++ 17, se proporcionan versiones paralelas de muchos algoritmos.

Estos son algunos ejemplos importantes:

- **for_each**, el algoritmo de recorrido predeterminado (junto con bucles for basados en intervalos). 

- **transformación**, para la modificación no en contexto de los elementos de contenedor

- **find_if**, el algoritmo de búsqueda predeterminado.

- **ordenar**, **lower_bound**y otros algoritmos de ordenación y búsqueda predeterminados.

Para escribir un comparador, utilice STRICT **<** y use *expresiones lambda con nombre* cuando sea posible.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>auto en lugar de nombres de tipo explícitos

C++ 11 presentó la palabra clave [auto](auto-cpp.md) para su uso en declaraciones de variables, funciones y plantillas. **auto** indica al compilador que deduzca el tipo del objeto para que no tenga que escribirlo explícitamente. **auto** es especialmente útil cuando el tipo deducido es una plantilla anidada:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Bucles for basados en intervalos

La iteración de estilo C sobre matrices y contenedores es propenso a la indexación de errores y también es tedioso de escribir. Para eliminar estos errores y hacer que el código sea más legible, use bucles for basados en intervalos con contenedores de la biblioteca estándar, así como matrices sin formato. Para obtener más información, vea [instrucción for basada en intervalo](../cpp/range-based-for-statement-cpp.md).

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

## <a name="constexpr-expressions-instead-of-macros"></a>Expresiones constexpr en lugar de macros

Las macros de C C++ y son tokens procesados por el preprocesador antes de la compilación. Cada instancia de un token de macro se reemplaza por su valor o expresión definido antes de que se compile el archivo. Las macros se utilizan normalmente en la programación de estilo C para definir valores constantes en tiempo de compilación. Sin embargo, las macros son propensas a errores y difíciles de depurar. En moderno C++, debería preferir variables [constexpr](constexpr-cpp.md) para constantes en tiempo de compilación:

```cpp
#define SIZE 10 / C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Inicialización uniforme

En moderno C++, puede usar la inicialización de llaves para cualquier tipo. Esta forma de inicialización es especialmente útil al inicializar matrices, vectores u otros contenedores. En el ejemplo siguiente, `v2` se inicializa con tres instancias de `S`. `v3` se inicializa con 3 instancias de `S` que se inicializan con llaves. El compilador deduce el tipo de cada elemento basándose en el tipo declarado de `v3`.

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

Para obtener más información, consulte [inicialización de llaves](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Semántica de transferencia de movimiento

Moderno C++ proporciona *semántica de movimiento* que permite eliminar las copias de memoria innecesarias que en versiones anteriores del lenguaje eran desevitables en determinadas situaciones. Una operación de *movimiento* transfiere la propiedad de un recurso de un objeto a la siguiente sin hacer una copia. Al implementar una clase que posee un recurso como memoria del montón, identificadores de archivo, etc., puede definir un *constructor de movimiento* y un *operador de asignación de movimiento* para él. El compilador elegirá estos miembros especiales durante la resolución de sobrecarga en situaciones en las que no es necesario realizar una copia. Los tipos de contenedor de la biblioteca estándar invocan al constructor de movimiento en objetos si se define uno. Para obtener más información, vea [constructores de movimiento y operadores deC++asignación de movimiento ()](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Expresiones lambda

En la programación de estilo C, una función se puede pasar a otra función por medio de un *puntero de función*. Los punteros de función no son adecuados para el mantenimiento y la comprensión porque la función a la que hacen referencia se puede definir en cualquier parte del código fuente, lejos del punto en el que se invoca. Además, no tienen seguridad de tipos. Modern C++ proporciona objetos de función, clases que invalidan el operador [()](function-call-operator-parens.md) , lo que permite que se llamen como una función. La manera más cómoda de crear objetos de función es con [expresiones lambda](../cpp/lambda-expressions-in-cpp.md)en línea. En el ejemplo siguiente se muestra cómo usar una expresión lambda para pasar un objeto de función, que la función `for_each` invocará en cada elemento del vector:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

La expresión lambda `[=](int i) { return i > x && i < y; }` se puede leer como "función que toma un único argumento de tipo `int` y devuelve un valor booleano que indica si la expresión es verdadera. Observe que las variables `x` y `y` del contexto circundante se pueden usar en la expresión lambda. La `[=]` especifica que esas variables se *capturan* por valor. en otras palabras, la expresión lambda tiene sus propias copias de esos valores.

## <a name="exceptions"></a>Excepciones

Como norma general, moderno C++ destaca las excepciones en lugar de los códigos de error como la mejor manera de notificar y controlar las condiciones de error. Para obtener más información, [vea C++ prácticas recomendadas modernas para excepciones y control de errores](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>STD:: Atomic

Use la C++ biblioteca estándar [STD:: Atomic](../standard-library/atomic-structure.md) struct y los tipos relacionados para los mecanismos de comunicación entre subprocesos.

## <a name="stdvariant-c17"></a>STD:: Variant (C++ 17)

Las uniones se suelen usar en la programación de estilo C para conservar memoria al permitir que los miembros de tipos diferentes ocupen la misma ubicación de memoria. Sin embargo, las uniones no tienen seguridad de tipos y son propensos a errores de programación. C++ 17 presenta la clase [STD:: Variant](../standard-library/variant-class.md) como una alternativa más sólida y segura a las uniones. La función [STD:: Visit](../standard-library/variant-functions.md#visit) se puede usar para tener acceso a los miembros de un tipo de `variant` de una manera con seguridad de tipos.

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Tabla de conformidad del lenguaje Microsoft C++](../overview/visual-cpp-language-conformance.md)