---
title: Mejoras de conformidad del compilador de C++ | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: ee7e4f3e09f5b1512182d17fda9033a45ad4aa5b
ms.openlocfilehash: c4bfe76d3b57962fe10df1d55f6ec5b58f70a38a
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
   
# <a name="c-conformance-improvements-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>Mejoras de conformidad de C++ en [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]
Para conocer las mejoras de la versión de actualización 15.3, consulte las [correcciones de errores en la versión de actualización 15.3 de Visual Studio](#update_153).
## <a name="new-language-features"></a>Nuevas características de lenguaje  
Gracias a la compatibilidad de constexpr generalizado y NSDMI con los agregados, el compilador ya tiene la totalidad de las características que se agregaron en el estándar C++14. Tenga en cuenta que al compilador todavía le faltan algunas características de los estándares C++11 y C++98. Consulte [Visual C++ Language Conformance](visual-cpp-language-conformance.md) (Conformidad del lenguaje Visual C++) para ver una tabla que muestra el estado actual del compilador.

### <a name="c11"></a>C++11:
**Compatibilidad con la expresión SFINAE en más bibliotecas** El compilador de Visual C++ sigue mejorando su compatibilidad con la expresión SFINAE, necesaria para la deducción y sustitución de argumentos de plantilla donde las expresiones decltype y constexpr puedan aparecer como parámetros de plantilla. Para más información, vea [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3) (Mejoras de la expresión SFINAE en Visual Studio 2017 RC). 


### <a name="c-14"></a>C++ 14:
**NSDMI para agregados** Un agregado es una matriz o una clase sin ningún constructor proporcionado por el usuario, ningún miembro de datos no estático privado o protegido, ninguna clase base y ninguna función virtual. A partir de C++14, los agregados pueden contener inicializadores de miembro. Para más información, vea [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html) (Inicializadores de miembro y agregados).

**constexpr extendido** Las expresiones declaradas como constexpr ya pueden contener determinados tipos de declaraciones, instrucciones if y switch, instrucciones loop y mutación de objetos cuya duración se haya iniciado durante la evaluación de la expresión constexpr. Además, ya no es necesario que una función miembro no estática constexpr sea const de forma implícita. Para más información, vea [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html) (Relajación de restricciones en funciones constexpr). 

### <a name="c17"></a>C++17:
**static_assert simplificado** (disponible con /std:c++latest) En C++17, el parámetro de mensaje para static_assert es opcional. Para más información, vea [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf) (Extensión de static_assert, v2). 

**atributo [[fallthrough]]** (disponible con /std:c++latest) Se puede usar el atributo [[fallthrough]] en el contexto de las instrucciones switch como una sugerencia al compilador de que se prevé el comportamiento de paso explícito. Esto evita que el compilador emita advertencias en estos casos. Para más información, vea [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf) (Lenguaje para el atributo [[fallthrough]]). 

**Bucles for basados en intervalos generalizados** (ningún modificador de compilador necesario) Los bucles for basados en intervalos ya no necesitan que begin() y end() devuelvan objetos del mismo tipo. Esto permite que end() devuelva un objeto centinela como el usado por los intervalos tal como se define en la propuesta de intervalos V3. Para más información, vea [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) (Generalización del bucle for basado en intervalos) y [range-v3 library](https://github.com/ericniebler/range-v3) (Biblioteca range-v3) en GitHub. 


Para obtener una lista completa de las mejoras de conformidad hasta Visual Studio 2015, Update 3, vea [Visual C++ What's New 2003 through 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx) (Novedades de Visual C++ de 2003 a 2015).

## <a name="bug-fixes"></a>Correcciones de errores
### <a name="copy-list-initialization"></a>Inicialización de lista de copia
Visual Studio 2017 genera correctamente errores del compilador relacionados con la creación de objetos mediante listas del inicializador que en Visual Studio 2015 no se detectaban y podían provocar bloqueos o un comportamiento en tiempo de ejecución no definido.  Conforme a N4594 13.3.1.7p1, en la inicialización de lista de copia el compilador debe tener en cuenta un constructor explícito para la resolución de sobrecarga, pero debe generar un error si se elige realmente esa sobrecarga. 

Los dos ejemplos siguientes se compilan en Visual Studio 2015, pero no en Visual Studio 2017.
```cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```
Para corregir el error, use la inicialización directa:
```cpp  
A a1{ 1 };
const A& a2{ 1 };
```

En Visual Studio 2015, el compilador trataba erróneamente la inicialización de lista de copia como si fuera inicialización de copia regular; solo consideraba la conversión de constructores para la resolución de sobrecarga. En el ejemplo siguiente, Visual Studio 2015 elige MyInt(23), pero Visual Studio 2017 genera correctamente el error. 

```cpp  
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
       explicit MyStore(int initialCapacity);
};

struct MyInt {
       MyInt(int i);
};

struct Printer {
       void operator()(MyStore const& s);
       void operator()(MyInt const& i);
};

void f() {
       Printer p;
       p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

Este ejemplo es similar al anterior, pero genera un error diferente. Se realiza correctamente en Visual Studio 2015 y genera un error en Visual Studio 2017 con C2668. 

```cpp  
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>Definiciones de tipo en desuso
Visual Studio 2017 ahora emite la advertencia correcta para las definiciones de tipo en desuso declaradas en una clase o struct. En el ejemplo siguiente, la compilación se realiza sin advertencias en Visual Studio 2015, pero se genera la advertencia C4996 en Visual Studio 2017.

```cpp  
struct A 
{
    // also for __declspec(deprecated) 
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>constexpr
Visual Studio 2017 genera correctamente un error si el operando izquierdo de una operación de evaluación condicional no es válido en un contexto constexpr. El siguiente código se compila en Visual Studio 2015, pero no en Visual Studio 2017:

```cpp  
template<int N>
struct array 
{
       int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
       return arr.size() == 10 || arr.size() == 11; // error starting in Visual Studio 2017
}
```
Para corregir el error, declare la función array::size() como constexpr o quite el calificador constexpr de f. 

### <a name="class-types-passed-to-variadic-functions"></a>Tipos de clase pasados a funciones variádicas
En Visual Studio 2017, las clases o structs pasados a una función variádica como printf se deben poder copiar trivialmente. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor. 

```cpp  
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called; 
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```
Para corregir el error, puede llamar a una función miembro que devuelva un tipo que se pueda copiar trivialmente 

```cpp  
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```
o bien realizar una conversión estática para convertir el objeto antes de pasarlo:
```cpp  
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```
En el caso de las cadenas compiladas y administradas mediante CStringW, debe usarse el `operator LPCWSTR()` proporcionado para convertir un objeto CStringW en el puntero C esperado por la cadena de formato.

```cpp  
CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Calificadores cv en la construcción de clases
En Visual Studio 2015, el compilador a veces omite incorrectamente al calificador cv al generar un objeto de clase mediante una llamada al constructor. Esto puede causar un bloqueo o un comportamiento inesperado en tiempo de ejecución. En el ejemplo siguiente se compila en Visual Studio 2015, pero se genera un error del compilador en Visual Studio 2017:

```cpp  
struct S 
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```
Para corregir el error, declare el operador int() como const. 

### <a name="access-checking-on-qualified-names-in-templates"></a>Comprobación de acceso en nombres completos en plantillas
Las versiones anteriores del compilador no realizaban la comprobación de acceso en nombres completos en algunos contextos de plantilla. Esto puede interferir con el comportamiento esperado de SFINAE, ya que se espera un error en la sustitución debido a la inaccesibilidad de un nombre. Esto podría haber provocado un bloqueo o un comportamiento inesperado en tiempo de ejecución, ya que el compilador hubiera llamado incorrectamente a la sobrecarga incorrecta del operador. En Visual Studio 2017, se genera un error del compilador. El error concreto puede variar, pero normalmente es "C2672: no se encontró una función sobrecargada que coincida". El siguiente código se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017:

```cpp  
#include <type_traits>

template <class T> class S {
       typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
       f(10); // C2672: No matching overloaded function found. 
}
```

### <a name="missing-template-argument-lists"></a>Listas de argumentos de plantilla que faltan
En Visual Studio 2015 y versiones anteriores, el compilador no diagnosticaba la falta de listas de argumentos de plantilla cuando la plantilla aparecía en una lista de parámetros de plantilla (por ejemplo, como parte de un argumento de plantilla predeterminado o un parámetro de plantilla sin tipo). Esto puede provocar un comportamiento impredecible, como el bloqueo del compilador o un comportamiento inesperado en tiempo de ejecución. El siguiente código se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017.

```cpp  
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;  
```

### <a name="expression-sfinae"></a>Expresión SFINAE
Para admitir la expresión SFINAE, el compilador ahora analiza argumentos decltype cuando las plantillas se declaran en lugar de crear instancias. Por consiguiente, si se detecta una especialización no dependiente en el argumento decltype, no se aplaza hasta el momento de la creación de instancias, sino que se procesa inmediatamente y los errores resultantes se diagnostican en ese momento.  

En el ejemplo siguiente se muestra este tipo de error del compilador que se genera en el punto de declaración:

```cpp  
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
       struct BadType {};
       template <class U>
       static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
       template <class U>
       static BadType Test(...);
       static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```
### <a name="classes-declared-in-anonymous-namespaces"></a>Clases declaradas en espacios de nombres anónimos
Según el estándar de C++, una clase que se declara dentro de un espacio de nombres anónimo tiene vinculación interna y, por lo tanto, no se puede exportar. En Visual Studio 2015 y versiones anteriores no se aplicó esta regla. En Visual Studio 2017 se aplica la regla de forma parcial. En el siguiente ejemplo se genera este error en Visual Studio 2017: "error C2201: ' const `anonymous namespace'::S1::`vftable'': debe tener una vinculación externa para exportarlo o importarlo".

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Inicializadores predeterminados para miembros de clase de valor (C++/CLI)
En Visual Studio 2015 y versiones anteriores, el compilador permitía (aunque omitía) un inicializador de miembro predeterminado para un miembro de una clase de valor.  La inicialización predeterminada de una clase de valor siempre inicializa a cero a los miembros; no se permite un constructor predeterminado.  En Visual Studio 2017, los inicializadores de miembro predeterminados generan un error del compilador, tal como se muestra en este ejemplo:

```cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indizadores predeterminados (C++/CLI)
En Visual Studio 2015 y versiones anteriores, el compilador en algunos casos identificaba incorrectamente una propiedad predeterminada como un indizador predeterminado. Era posible solucionar el problema con el identificador "default" para acceder a la propiedad. La solución en sí misma se volvió problemática después de que se empezara a usar default como palabra clave en C++11. Por lo tanto, en Visual Studio 2017 se corrigieron los errores necesarios para la solución, y el compilador ahora genera un error cuando se usa "default" para acceder a la propiedad predeterminada de una clase.

```cpp  
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

 
// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

En Visual Studio 2017 se puede acceder a ambas propiedades Value por su nombre:

```cpp  
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Versión de actualización 15.3 de Visual Studio 2017
### <a name="calls-to-deleted-member-templates"></a>Llamadas a plantillas de miembro eliminado
En versiones anteriores de Visual Studio, había ocasiones en que el compilador no podía emitir un error en las llamadas con un formato incorrecto a una plantilla de miembro eliminado, lo que podía provocar bloqueos en tiempo de ejecución. El código siguiente produce ahora el error C2280, "'int S<int>:: f<int>(void)': se está intentando hacer referencia a una función eliminada":
```cpp
template<typename T> 
struct S { 
template<typename U> static int f() = delete; 
}; 
 
void g() 
{ 
decltype(S<int>::f<int>()) i; // this should fail 
}
```
Para corregir el error, declare i como `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Comprobaciones de condición previa para type traits
La versión de actualización 15.3 de Visual Studio 2017 mejora las comprobaciones de condición previa para type-traits a fin de seguir el estándar de manera más estricta. Una de estas comprobaciones es para asignable. El código siguiente produce el error C2139 en la versión de actualización 15.3:

```cpp
struct S; 
enum E; 
 
static_assert(!__is_assignable(S, S), "fail"); // this is allowed in VS2017 RTM, but should fail 
static_assert(__is_convertible_to(E, E), "fail"); // this is allowed in VS2017 RTM, but should fail
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nuevas advertencias de compilador y comprobaciones en tiempo de ejecución en la serialización nativa a administrada
Para llamar de funciones administradas a funciones nativas se requiere la serialización. El CLR realiza la serialización, pero no comprende la semántica de C++. Si se pasa un objeto nativo por valor, CLR llama al constructor de copia del objeto o usa BitBlt, lo que puede provocar un comportamiento indefinido en tiempo de ejecución. 
 
Ahora, el compilador emite una advertencia si puede saber en tiempo de compilación que se pasa un objeto nativo con el constructor de copia eliminada entre límites nativos y administrados por valor. En aquellos casos en los que el compilador no lo sepa en tiempo de compilación, se inyectará una comprobación en tiempo de ejecución para que el programa llame a std::terminate inmediatamente cuando se produzca una serialización con un formato incorrecto. En la versión de actualización 15.3, el siguiente código produce C4606 "A": el paso de un argumento por valor entre los límites nativo y administrado requiere un constructor de copia válido. De lo contrario, el comportamiento en tiempo de ejecución es indefinido.
```cpp
class A 
{ 
public: 
A() : p_(new int) {} 
~A() { delete p_; } 
 
A(A const &) = delete; 
A(A &&rhs) { 
p_ = rhs.p_; 
} 
 
private: 
int *p_; 
}; 
 
#pragma unmanaged 
 
void f(A a) 
{ 
} 
 
#pragma managed 
 
int main() 
{ 
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which will result in a double-free later. 
}
```
Para corregir el error, quite la directiva `#pragma managed` para marcar el llamador como nativo y evitar la serialización. 

### <a name="experimental-api-warning-for-winrt"></a>Advertencia de API experimental para WinRT
Las API de WinRT que se publican para experimentación y comentarios se decorarán con `Windows.Foundation.Metadata.ExperimentalAttribute`. En la versión de actualización 15.3, el compilador producirá la advertencia C4698 cuando encuentra el atributo. Algunas API de versiones anteriores del SDK de Windows se han decorado con el atributo, y las llamadas a estas API comenzarán a desencadenar esta advertencia del compilador. Los SDK más recientes de Windows tendrán quitado el atributo de todos los tipos enviados, pero si usa un SDK antiguo, deberá suprimir estas advertencias en todas las llamadas a tipos enviados.
El código siguiente produce la advertencia C4698: "'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' solo se usa con fines de evaluación y está sujeto a cambio o eliminación en futuras actualizaciones":
```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync()
```

Para deshabilitar la advertencia, agregue #pragma:

```cpp
#pragma warning(push) 
#pragma warning(disable:4698) 
 
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() 
 
#pragma warning(pop)
```
### <a name="out-of-line-definition-of-a-template-member-function"></a>Definición fuera de línea de una función de miembro de plantilla 
La versión de actualización 15.3 produce un error cuando encuentra una definición fuera de línea de una función de miembro de plantilla que no se ha declarado en la clase. El código siguiente produce ahora el error C2039: "f": no es miembro de "S":

```cpp
struct S {}; 
 
template <typename T> 
void S::f(T t) {}
```

Para corregir el error, agregue una declaración a la clase:

```cpp
struct S { 
    template <typename T> 
    void f(T t); 
}; 
template <typename T> 
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Intento de tomar la dirección del puntero "this"
En C++ "this" es un prvalue de puntero de tipo a X. No puede tomar la dirección de "this" ni enlazarlo a una referencia lvalue. En versiones anteriores de Visual Studio, el compilador le permitiría eludir esta restricción mediante la realización de una conversión. En la versión de actualización 15.3, el compilador produce el error C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Conversión a una clase base inaccesible
La versión de actualización 15.3 produce un error cuando intenta convertir un tipo a una clase base que es inaccesible. El compilador produce ahora el  
error C2243: "conversión de tipo": la conversión de "D *" a "B *" existe, pero no es accesible. El código siguiente es incorrecto y podría provocar un bloqueo en tiempo de ejecución. El compilador produce ahora el error C2243 cuando encuentra código como este:

```cpp
#include <memory> 
 
class B { }; 
class D : B { }; // should be public B { }; 
 
void f() 
{ 
   std::unique_ptr<B>(new D()); 
}
```
### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>No se permiten argumentos predeterminados en definiciones fuera de línea de funciones miembro
No se permiten argumentos predeterminados en definiciones fuera de línea de funciones miembro de clases de plantilla.  El compilador emite una advertencia en /permissive y un error en /permissive- En versiones anteriores de Visual Studio, el siguiente código de formato incorrecto podía ocasionar un bloqueo en tiempo de ejecución. La versión de actualización 15.3 produce la advertencia C5034: "A<T>::f": una definición fuera de línea de un miembro de una plantilla de clase no puede tener argumentos predeterminados:
```cpp
 
template <typename T> 
struct A { 
    T f(T t, bool b = false); 
}; 
 
template <typename T> 
T A<T>::f(T t, bool b = false) 
{ 
... 
}
```
Para corregir el error, quite el argumento predeterminado "= false". 

### <a name="use-of-offsetof-with-compound-member-designator"></a>Uso de offsetof con el designador de miembro compuesta
En la versión de actualización 15.3, el uso de offsetof(T, m) donde m es un "designador de miembro compuesto" dará lugar a una advertencia al compilar con la opción /Wall. El código siguiente es incorrecto y podría provocar un bloqueo en tiempo de ejecución. La versión de actualización 15.3 produce la "advertencia C4841: extensión no estándar utilizada: designador de miembro compuesto en offseto":

```cpp
  
struct A { 
int arr[10]; 
}; 
 
// warning C4841: non-standard extension used: compound member designator in offsetof 
constexpr auto off = offsetof(A, arr[2]);
```
Para corregir el código, deshabilite la advertencia con una pragma o cambie el código para que no se use offsetof: 

```cpp
#pragma warning(push) 
#pragma warning(disable: 4841) 
constexpr auto off = offsetof(A, arr[2]); 
#pragma warning(pop) 
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Uso de offsetof con un miembro de datos estático o una función miembro
En la versión de actualización 15.3, el uso de offsetof(T, m) donde m hace referencia a un miembro de datos estático o a una función miembro, dará error. El siguiente código genera el "error C4597: comportamiento indefinido: offsetof aplicado a la función de miembro "foo'" y "error C4597: comportamiento indefinido: offsetof aplicado al miembro de datos estático "bar"":
```cpp
 
#include <cstddef> 
 
struct A { 
int foo() { return 10; } 
static constexpr int bar = 0; 
}; 
 
constexpr auto off = offsetof(A, foo); 
Constexpr auto off2 = offsetof(A, bar);
```
 
Este código no tiene un formato correcto y podría ocasionar un bloqueo en tiempo de ejecución. Para corregir el error, cambie el código para que deje de invocar un comportamiento indefinido. Se trata de código no portable que no admite el estándar de C++.

### <a name="new-warning-on-declspec-attributes"></a>Nueva advertencia en los atributos declspec
En la versión de actualización 15.3, el compilador ya no ignora los atributos si se aplica __declspec(…) antes de la especificación de vinculación de "C" externa. Anteriormente, el compilador ignoraría el atributo, lo que podría tener implicaciones para el tiempo de ejecución. Cuando la opción `/Wall /WX` está configurada, el siguiente código produce la "advertencia C4768: los atributos __declspec anteriores a la especificación de la vinculación se ignoran":

```cpp
 
__declspec(noinline) extern "C" HRESULT __stdcall
```

Para corregir la advertencia, coloque primero la "C" externa:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype y llamadas a destructores eliminados
En versiones anteriores de Visual Studio, el compilador no detectaba cuándo se produce una llamada a un destructor eliminado en el contexto de la expresión asociada a "decltype". En la versión de actualización 15.3, el siguiente código produce el error C2280: "A<T>::~A(void)": se está intentando hacer referencia a una función eliminada":

```cpp
template<typename T> 
struct A 
{ 
   ~A() = delete; 
}; 
 
template<typename T> 
auto f() -> A<T>; 
 
template<typename T> 
auto g(T) -> decltype((f<T>())); 
 
void h() 
{ 
   g(42); 
}
```
### <a name="unitialized-const-variables"></a>Variables const no inicializadas
La versión Visual Studio 2017 RTW tenía una regresión en la que el compilador de C++ no emitía un diagnóstico si no se inicializaba una variable "const". Esta regresión se ha corregido en Visual Studio 2017 Update 1. El siguiente código produce ahora la "advertencia C4132: "Valor": se debe inicializar el objeto const:

```cpp
const int Value;
```
Para corregir el error, asigne un valor a `Value`.

### <a name="empty-declarations"></a>Declaraciones vacías
La versión de actualización 15.3 de Visual Studio 2017 ahora advierte sobre declaraciones vacías para todos los tipos, no solo los integrados. El código siguiente produce ahora una advertencia C4091 de nivel 2 para las cuatro declaraciones:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };
 
int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Para quitar las advertencias, simplemente conviértalas en comentario o quite las declaraciones vacías.  En casos donde el objeto sin nombre no tenga que tener un efecto secundario (como RAII), se le debe proporcionar un nombre.
 
La advertencia se excluye en /Wv:18 y está activada de forma predeterminada en el nivel de advertencia W2.


## <a name="see-also"></a>Vea también  
[Conformidad del lenguaje Visual C++](visual-cpp-language-conformance.md)  

