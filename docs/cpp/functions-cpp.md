---
title: Funciones (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5fa20f0a2236d6458490784d2fa0f1b53b13241
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="functions-c"></a>Funciones (C++)
Una función es un bloque de código que realiza alguna operación. Una función puede definir opcionalmente parámetros de entrada que permiten a los llamadores pasar argumentos a la función. Una función también puede devolver un valor como salida. Las funciones son útiles para encapsular las operaciones comunes en un solo bloque reutilizable, idealmente con un nombre que describa claramente lo que hace la función. La función siguiente acepta dos enteros de un autor de llamada y devuelve su suma; `a` y `b` son *parámetros* de tipo `int`.  
  
```  
int sum(int a, int b)  
{  
    return a + b;  
}  
```  
  
 La función puede ser ' invoca, o *llama*, de cualquier número de partes del programa. Los valores que se pasan a la función son los *argumentos*, cuyos tipos deben ser compatibles con los tipos de parámetro en la definición de función.  
  
```  
int main()  
{  
    int i = sum(10, 32);  
    int j = sum(i, 66);  
    cout << "The value of j is" << j << endl; // 108  
}  
```  
  
 No hay ningún límite práctico para la longitud de la función, pero un buen diseño tiene como objetivo funciones que realizan una sola tarea bien definida. Los algoritmos complejos deben dividirse en funciones más sencillas y fáciles de comprender siempre que sea posible.  
  
 Las funciones definidas en el ámbito de clase se denominan funciones miembro. En C++, a diferencia de otros lenguajes, una función también pueden definirse en el ámbito de espacio de nombres (incluido el espacio de nombres global implícito). Estas funciones se denominan *funciones libres* o *funciones no miembro*; se usan ampliamente en la biblioteca estándar.  
  
## <a name="parts-of-a-function-declaration"></a>Elementos de una declaración de función  
 Una función mínima *declaración* está formada por el tipo de valor devuelto, el nombre de la función y la lista de parámetros (que puede estar vacía), junto con palabras clave opcionales que se proporcionan instrucciones adicionales para el compilador. El ejemplo siguiente es una declaración de función:

 ```cpp
 int sum(int a, int b);
 ```

 Una definición de función se compone de una declaración, además de la interfaz *cuerpo*, que es todo el código incluido entre llaves:
 
 ```cpp
int sum(int a, int b)  
{  
    return a + b;  
}  
```
 Una declaración de función seguida de un punto y coma puede aparecer en varios lugares de un programa. Debe aparecer antes de cualquier llamada a esa función en cada unidad de traducción. La definición de función debe aparecer solo una vez en el programa, según la regla de una definición (ODR).  
  
 Los elementos necesarios de una declaración de función son los siguientes:  
  
1.  El tipo de valor devuelto, que especifica el tipo del valor que devuelve la función, o `void` si no se devuelve ningún valor. En C ++ 11, `auto` es un tipo de valor devuelto válido que indica al compilador que deduzca el tipo de la instrucción return. En C++14, también se permite decltype(auto). Para obtener más información, consulte más adelante Deducción de tipos en tipos de valor devueltos.  
  
2.  El nombre de función, que debe comenzar con una letra o un carácter de subrayado y no puede contener espacios. En general, un carácter de subrayado inicial en los nombres de función de la biblioteca estándar indica funciones de miembro privado o funciones no miembro que no están pensadas para que las use el código. 
  
3.  La lista de parámetros, que es un conjunto delimitado por llaves y separado por comas de cero o más parámetros que especifican el tipo y, opcionalmente, un nombre local mediante el cual se puede acceder a los valores de dentro del cuerpo de la función. 
  
 Los elementos opcionales de una declaración de función son los siguientes:  
  
1.  `constexpr`, que indica que el valor devuelto de la función es un valor constante que se puede calcular en tiempo de compilación.  
  
    ```  
    constexpr float exp(float x, int n)  
    {  
        return n == 0 ? 1 :  
            n % 2 == 0 ? exp(x * x, n / 2) :  
            exp(x * x, (n - 1) / 2) * x;  
    };  
    ```  
  
2.  Su especificación `linkage`, `extern` o `static`.  
  
    ```  
    Declare printf with C linkage.  
    extern "C" int printf( const char *fmt, ... );  
  
    ```  
  
     Para obtener más información, consulte [programa y vinculación](../cpp/program-and-linkage-cpp.md).  
  
3.  `inline`, que indica al compilador que reemplace todas las llamadas a la función con el propio código de la función. La inserción en línea puede mejorar el rendimiento en escenarios donde una función se ejecuta rápidamente y se invoca varias veces en una sección del código crítica para el rendimiento.  
  
    ```  
    inline double Account::GetBalance()  
    {  
        return balance;  
    }  
    ```  
  
     Para obtener más información, consulte [funciones Inline](../cpp/inline-functions-cpp.md).  
  
4.  Un `noexcept` expresión, que especifica si la función puede producir una excepción. En el ejemplo siguiente, la función no produce una excepción si la expresión `is_pod` se evalúa como `true`.  
  
    ```  
    #include <type_traits>  
  
    template <typename T>  
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}  
    ```  
  
     Para obtener más información, consulte [noexcept](../cpp/noexcept-cpp.md).  
  
5.  (Solo funciones miembro) Los calificadores cv, que especifican si la función es `const` o `volatile`.  
  
6.  (Solo funciones miembro) `virtual`, `override` o `final`. `virtual` especifica que una función se puede reemplazar en una clase derivada. `override` significa que una función de una clase derivada reemplaza una función virtual. `final` significa que una función no se puede reemplazar en ninguna otra clase derivada. Para obtener más información, consulte [funciones virtuales](../cpp/virtual-functions.md).  
  
7.  (Solo funciones miembro) `static` aplicado a una función miembro significa que la función no está asociada con instancias de objeto de la clase.  
  
8.  (Solo funciones miembro no estática) El calificador de referencia, que indica al compilador qué sobrecarga de una función debe elegir cuando el parámetro de objeto implícito (* esto) es una referencia rvalue frente a una referencia lvalue.  
  
 La ilustración siguiente muestra las partes de una definición de función. El área sombreada es el cuerpo de la función.  
  
 ![Partes de una definición de función](../cpp/media/vc38ru1.gif "vc38RU1")  
Elementos de definición de una función  
  
## <a name="function-definitions"></a>Definiciones de función  
 Las variables declaradas dentro del cuerpo se denominan variables locales. Se salen del ámbito cuando finaliza la función; por lo tanto, una función nunca debe devolver una referencia a una variable local.  
  
## <a name="function-templates"></a>Plantillas de función  
 Una plantilla de función es parecida a una plantilla de clase; genera funciones concretas que se basan en los argumentos de plantilla. En muchos casos, la plantilla es capaz de inferir los argumentos de tipo, por lo que no es necesario especificarlos de forma explícita.  
  
```  
template<typename Lhs, typename Rhs>  
auto Add2(const Lhs& lhs, const Rhs& rhs)  
{  
    return lhs + rhs;  
}  
  
auto a = Add2(3.13, 2.895); // a is a double  
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string  
```  
  
 Para obtener más información, vea [plantillas de función](../cpp/function-templates.md)  
  
## <a name="function-parameters-and-arguments"></a>Parámetros de función y argumentos  
 Una función tiene una lista de parámetros separados por comas de cero o más tipos, cada uno de los cuales tiene un nombre mediante el cual se puede acceder a ellos dentro del cuerpo de la función. Una plantilla de función puede especificar parámetros adicionales de tipo de valor. El llamador pasa argumentos, que son valores concretos cuyos tipos son compatibles con la lista de parámetros.  
  
 De forma predeterminada, los argumentos se pasan a la función por valor, lo que significa que la función recibe una copia del objeto que se pasa. En el caso de los objetos grandes, puede resultar costoso realizar una copia y no siempre es necesario. Para hacer que los argumentos se pasen por referencia (en concreto, por la referencia lvalue), agregue un calificador de referencia al parámetro:  
  
```  
void DoSomething(std::string& input){...}  
```  
  
 Cuando una función modifica un argumento que se pasa por referencia, modifica el objeto original, no una copia local. Para evitar que una función modifique dicho argumento, califique el parámetro como const&:  
  
```  
void DoSomething(const std::string& input){...}  
```  
  
 **C++ 11:** para controlar explícitamente los argumentos que se pasan por referencia rvalue o por la referencia lvalue, use una y comercial doble en el parámetro para indicar una referencia universal:  
  
```  
void DoSomething(const std::string&& input){...}  
```  
  
 Una función declarada con la única palabra clave `void` en la lista de declaración de parámetros no toma argumentos mientras la palabra clave `void` sea el primer y único miembro de la lista de declaración de argumentos. Los argumentos de tipo `void` que se encuentran en otro lugar de la lista producen errores. Por ejemplo:  
  
```  
  
// OK same as GetTickCount()  
long GetTickCount( void );   
```  
  
 Observe que, aunque no es válido especificar un argumento `void` excepto como se explica aquí, los tipos derivados de tipo `void` (tales como los punteros a `void` y las matrices de `void`) pueden aparecer en cualquier lugar de la lista de declaración de argumentos.  
  
### <a name="default-arguments"></a>Argumentos predeterminados  
 Es posible asignar un argumento predeterminado al último parámetro o parámetros de una firma de función, lo que significa que el llamador puede omitir el argumento cuando se llama a la función, a menos que desee especificar otro valor.  
  
```  
int DoSomething(int num,   
    string str,   
    Allocator& alloc = defaultAllocator)  
{ ... }  
  
// OK both parameters are at end  
int DoSomethingElse(int num,   
    string str = string{ "Working" },   
    Allocator& alloc = defaultAllocator)  
{ ... }  
  
// C2548: 'DoMore': missing default parameter for parameter 2  
int DoMore(int num = 5, // Not a trailing parameter!  
    string str,  
    Allocator& = defaultAllocator)  
{...}  
```  
  
 Para obtener más información, consulte [argumentos predeterminados](../cpp/default-arguments.md).  
  
## <a name="function-return-types"></a>Tipos de valor devuelto de función  
 Una función no puede devolver otra función o una matriz integrada; Sin embargo, puede devolver punteros a estos tipos, o un *lambda*, lo que genera un objeto de función. Excepto para estos casos, una función puede devolver un valor de cualquier tipo que esté en el ámbito, o puede no devolver ningún valor, en cuyo caso el tipo devuelto es `void`.  
  
### <a name="trailing-return-types"></a>Tipos de valor devueltos finales  
 Un tipo de valor devuelto "normal" se encuentra en el lado izquierdo de la firma de función. A *tipo de valor devuelto final* se encuentra en el extremo derecho de la firma y va precedido por el operador ->. Los tipos de valor devueltos finales son especialmente útiles en plantillas de función cuando el tipo del valor devuelto depende de los parámetros de plantilla.  
  
```  
template<typename Lhs, typename Rhs>  
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)  
{  
    return lhs + rhs;   
}  
```  
  
 Cuando se usa `auto` junto con un tipo de valor devuelto final, simplemente sirve como marcador de posición para el resultado de la expresión decltype y no lleva a cabo una deducción de tipos.  

   
## <a name="function-local-variables"></a>Variables locales de función  
 Una variable que se declara dentro de un cuerpo de la función se denomina un *variable local* o simplemente *local*. Las variables locales no estáticas solo son visibles dentro del cuerpo de función y, si se declaran en la pila, se salen del ámbito cuando finaliza la función. Cuando se crea una variable local y se devuelve por valor, generalmente el compilador puede llevar a cabo la optimización del valor devuelto para evitar las operaciones de copia innecesarias. Si una variable local se devuelve por referencia, el compilador emitirá una advertencia, ya que cualquier intento por parte del llamador de usar esa referencia se producirá después de la destrucción de la variable local.  
  
 Los objetos estáticos locales se destruyen durante la finalización especificada por `atexit`. Si no se crea un objeto estático porque el flujo de control de programa omitió su declaración, no se realiza ningún intento de destruir ese objeto.  
  
### <a name="static-local-variables"></a>Variables locales estáticas  
 En C++, una variable local se puede declarar como estática. La variable solo es visible dentro del cuerpo de la función, pero existe una copia única de la variable para todas las instancias de la función.  
  
###  <a name="type_deduction"></a>Deducción de tipos en tipos de valor devuelto (C ++ 14)  
 En C ++ 14, puede usar `auto` para indicar al compilador que debe inferir el tipo de valor devuelto desde el cuerpo de la función sin tener que proporcionar un tipo de valor devuelto final. Tenga en cuenta que `auto` siempre se deduce como una devolución por valor. Use `auto&&` para indicar al compilador que deduzca una referencia.  
  
 En este ejemplo, `auto` se deduce como una copia del valor no constante de la suma de lhs y rhs.  
  
```  
template<typename Lhs, typename Rhs>  
auto Add2(const Lhs& lhs, const Rhs& rhs)  
{  
    return lhs + rhs; //returns a non-const object by value  
}  
```  
  
 Tenga en cuenta que `auto` no conserva la declaración como constante de tipo deduce. En el caso de las funciones de reenvío cuyo valor devuelto tiene que conservar la declaración como constante o como referencia de sus argumentos, puede usar la palabra clave `decltype(auto)`, que usa las reglas de inferencia de tipos `decltype` y conserva la información de tipo. Puede usar `decltype(auto)` como valor de retorno normal a la izquierda o como valor devuelto final.  
  
 En el siguiente ejemplo (basado en código de [N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html)), se muestra `decltype(auto)` que se usa para habilitar el reenvío directo de argumentos de función en un tipo de valor devuelto que no se conoce hasta que se crea una instancia de la plantilla.  
  
```  
template<typename F, typename Tuple = tuple<T...>, int... I>  
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)   
{  
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);  
}  
  
template<typename F, typename Tuple = tuple<T...>,  
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>  
   decltype( auto)  
    apply(F&& f, Tuple&& args)      
{  
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());  
}  
}  
```  
## <a name="returning-multiple-values-from-a-function"></a>Devolver varios valores de una función
Hay varias maneras de devolver más de un valor de una función:

1. Encapsular los valores de un objeto de clase o un struct con nombre. La definición de clase o struct sea visible para el llamador se necesita:

```cpp
#include <string>
#include <iostream>

using namespace std;

struct S
{
    string name;
    int num;
};

S g()
{
    string t{ "hello" };
    int u{ 42 };
    return { t, u };
}

int main()
{
    S s = g();
    cout << s.name << " " << s.num << endl;
    return 0;
}
```

2. Devolver un objeto std:: Tuple o std:: Pair:

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;


tuple<int, string, double> f()
{
    int i{ 108 };
    string s{ "Some text" };
    double d{ .01 };
    return { i,s,d };
}

int main()
{
    auto t = f();
    cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;
    
    // --or--

    int myval;
    string myname;
    double mydecimal;
    tie(myval, myname, mydecimal) = f();
    cout << myval << " " << myname << " " << mydecimal << endl;

    return 0;
}
```

3. **Visual Studio 2017 15,3 y versiones posteriores** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): Use estructurado enlaces. La ventaja de enlaces estructurados es que las variables que almacenan los valores devueltos se inicializan al mismo tiempo que se declaran, lo que en algunos casos puede ser mucho más eficaz. En esta declaración--`auto[x, y, z] = f();`--los corchetes se presentan e inicializar los nombres que están en ámbito para el bloque de la función completa.  

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;

tuple<int, string, double> f()
{
    int i{ 108 };
    string s{ "Some text" };
    double d{ .01 };
    return { i,s,d };
}
struct S
{
    string name;
    int num;
};

S g()
{
    string t{ "hello" };
    int u{ 42 };
    return { t, u };
}

int main()
{
    auto[x, y, z] = f(); // init from tuple
    cout << x << " " << y << " " << z << endl;

    auto[a, b] = g(); // init from POD struct
    cout << a << " " << b << endl;
    return 0;
}
```

4. Además de utilizar el propio valor devuelto, "volver" valores mediante la definición de cualquier número de parámetros que se usarán pasada por referencia para que la función puede modificar o inicializar los valores de los objetos proporcionados por el llamador. Para obtener más información, consulte [argumentos de función de tipo de referencia](reference-type-function-arguments.md).
  
## <a name="function-pointers"></a>Punteros de función  
 C++ admite punteros de función de la misma manera que el lenguaje C. Sin embargo, una alternativa con mayor seguridad de tipos suele ser usar un objeto de función.  
  
 Se recomienda usar `typedef` para declarar un alias para el tipo de puntero a función si se declara una función que devuelve un tipo de puntero a función.  Por ejemplo  
  
```  
typedef int (*fp)(int);  
fp myFunction(char* s); // function returning function pointer  
```  
  
 Si no es así, la sintaxis correcta para la declaración de la función se puede deducir de la sintaxis de declarador del puntero a función, mediante la sustitución del identificador (`fp` en el ejemplo anterior) por el nombre y la lista de argumentos de las funciones, como sigue:  
  
```  
int (*myFunction(char* s))(int);  
```  
  
 La declaración anterior es equivalente a la otra declaración con typedef.  
  
## <a name="see-also"></a>Vea también  
 [Sobrecarga de funciones](../cpp/function-overloading.md)   
 [Funciones con listas de argumentos variables](../cpp/functions-with-variable-argument-lists-cpp.md)   
 [Funciones establecidas como valor predeterminadas y eliminadas explícitamente](../cpp/explicitly-defaulted-and-deleted-functions.md)   
 [Búsqueda de nombres dependiente de argumentos (Koenig) en las funciones](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)   
 [Argumentos predeterminados](../cpp/default-arguments.md)   
 [Funciones insertadas](../cpp/inline-functions-cpp.md)