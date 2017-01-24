---
title: "auto (C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto (C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Deduce el tipo de una variable declarada a partir de su expresión de inicialización.  
  
## Sintaxis  
  
```  
auto declarator initializer;  
```  
  
```  
[](auto param1, auto param2) {};  
```  
  
## Comentarios  
 La palabra clave `auto` indica al compilador que utilice la expresión de inicialización de una variable declarada o el parámetro de expresión lambda para deducir su tipo.  
  
 Se recomienda utilizar la palabra clave `auto` para la mayoría de las situaciones, a menos que desee realmente una conversión, porque proporciona estas ventajas:  
  
-   **Solidez**: si el tipo de la expresión cambia \(esto incluye cuando se cambia un tipo de valor devuelto de función\), funciona.  
  
-   **Rendimiento**: se garantiza que no hay ninguna conversión.  
  
-   **Facilidad de uso**: no es necesario preocuparse de las dificultades y los errores tipográficos al escribir los nombres de los tipos.  
  
-   **Eficacia**: la codificación puede ser más eficaz.  
  
 Casos de conversión en los que puede que no desee utilizar `auto`:  
  
-   Cuando se desea un tipo específico y es la única alternativa.  
  
-   Tipo auxiliar de plantilla de expresión \(por ejemplo, `(valarray+valarray)` y listas de inicializadores\), aunque raramente elegiría escribir `auto x = { 1 };` y esperaría obtener realmente un tipo `int`.  
  
 Para utilizar la palabra clave `auto`, úsela en lugar de un tipo para declarar una variable, y especifique una expresión de inicialización.  Además, puede modificar la palabra clave `auto` mediante especificadores y declaradores como `const`, `volatile`, puntero \(`*`\), referencia \(`&`\) y referencia a un valor R `(&&`\).  El compilador evalúa la expresión de inicialización y emplea esa información para deducir el tipo de la variable.  
  
 La expresión de inicialización puede ser una asignación \(sintaxis de signo igual\), una inicialización directa \(sintaxis de estilo de función\), una expresión de [operador new](../Topic/operator%20new%20\(%3Cnew%3E\).md) o el parámetro *for\-range\-declaration* de una instrucción [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md).  Para obtener más información, vea [Inicializadores](../cpp/initializers.md) y los ejemplos de código más adelante en este documento.  
  
 La palabra clave `auto` es un marcador de posición para un tipo, pero no es en sí misma un tipo.  Por tanto, la palabra clave `auto` no se puede utilizar en conversiones o en operadores como [sizeof](../cpp/sizeof-operator.md) y [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md).  
  
## Utilidad  
 La palabra clave `auto` es una manera sencilla de declarar una variable que tiene un tipo complejo.  Por ejemplo, se puede utilizar `auto` para declarar una variable en la que la expresión de inicialización implica plantillas, punteros a funciones o punteros a miembros.  
  
 También se puede utilizar `auto` para declarar e inicializar una variable en una expresión lambda.  No puede declarar el tipo de la variable porque solo el compilador conoce el tipo de una expresión lambda.  Para más información, vea [Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).  
  
## Tipos de valor devuelto finales  
 Se puede utilizar `auto`, junto con el especificador de tipo `decltype`, como ayuda para escribir bibliotecas de plantillas.  Use `auto` y `decltype` para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla.  O bien, utilice `auto` y `decltype` para declarar una función de plantilla que contiene una llamada a otra función y, a continuación, devuelve el tipo de valor devuelto de esa otra función.  Para más información, vea [decltype](../cpp/decltype-cpp.md).  
  
## Referencias y calificadores cv  
 Tenga en cuenta que cuando se utiliza `auto` se quitan las referencias, los calificadores const y los calificadores volatile.  Considere el ejemplo siguiente:  
  
```cpp  
// cl.exe /analyze /EHsc /W4  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
    int count = 10;  
    int& countRef = count;  
    auto myAuto = countRef;  
  
    countRef = 11;  
    cout << count << " ";  
  
    myAuto = 12;  
    cout << count << endl;  
}  
  
```  
  
 Puede creer que myAuto es una referencia int, pero no lo es.  Es simplemente un tipo int, por lo que la salida es `11 11`, no `11 12` como sería si `auto` no hubiera quitado la referencia.  
  
## Restricciones y mensajes de error  
 En la tabla siguiente se enumeran las restricciones de uso de la palabra clave `auto` y el mensaje de error de diagnóstico correspondiente que el compilador emite.  
  
|Número de error|Descripción|  
|---------------------|-----------------|  
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|La palabra clave `auto` no se puede combinar con ningún otro especificador de tipo.|  
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Un símbolo que se declara con la palabra clave `auto` debe tener un inicializador.|  
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Utilizó incorrectamente la palabra clave `auto` para declarar un tipo.  Por ejemplo, declaró un tipo de valor devuelto de método o una matriz.|  
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Un argumento de parámetro o plantilla no se puede declarar con la palabra clave `auto`.|  
|[C3534](../Topic/Compiler%20Error%20C3534.md)|Un símbolo que se declara con la palabra clave `auto` en una expresión `new` debe tener un inicializador.  Para más información, vea [operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md).|  
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Un parámetro de método o plantilla no se puede declarar con la palabra clave `auto`.|  
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|No se puede usar un símbolo antes de inicializarlo.  En la práctica, esto significa que una variable no se puede usar para inicializarse a sí misma.|  
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|No se puede convertir en un tipo que se declara con la palabra clave `auto`.|  
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Todos los símbolos de una lista de declaradores que se declara con la palabra clave `auto` deben resolverse en el mismo tipo.  Para más información, vea [Declaraciones](../misc/declarations.md).|  
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Los operadores [sizeof](../cpp/sizeof-operator.md) y [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) no se pueden aplicar a un símbolo que se declara con la palabra clave `auto`.|  
  
## Ejemplos  
 Estos fragmentos de código muestran algunas de las formas de las que se puede usar la palabra clave `auto`.  
  
 Las declaraciones siguientes son equivalentes.  En la primera instrucción, se declara la variable `j` para que sea de tipo `int`.  En la segunda instrucción, se deduce que la variable `k` es de tipo `int` porque la expresión de inicialización \(0\) es un entero.  
  
```cpp  
  
int j = 0;  // Variable j is explicitly type int.  
auto k = 0; // Variable k is implicitly type int because 0 is an integer.  
```  
  
 Las declaraciones siguientes son equivalentes, pero la segunda declaración es más sencilla que la primera.  Una de las razones de más peso para utilizar la palabra clave `auto` es su sencillez.  
  
```cpp  
  
map<int,list<string>>::iterator i = m.begin();   
auto i = m.begin();   
```  
  
 En el fragmento de código siguiente se declara el tipo de las variables `iter` y `elem` cuando se inician los bucles `for` y `for` de intervalo.  
  
```cpp  
  
// cl /EHsc /nologo /W4  
#include <deque>  
using namespace std;  
  
int main()  
{  
    deque<double> dqDoubleData(10, 0.1);  
  
    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)  
    { /* ... */ }  
  
    // prefer range-for loops with the following information in mind  
    // (this applies to any range-for with auto, not just deque)  
  
    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples  
    { /* ... */ }  
  
    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE  
    { /* ... */ }  
  
    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE  
    { /* ... */ }  
}  
  
```  
  
 En el fragmento de código siguiente se utiliza el operador `new` y la declaración de puntero para declarar punteros.  
  
```cpp  
  
double x = 12.34;  
auto *y = new auto(x), **z = new auto(&x);  
```  
  
 En el fragmento de código siguiente se declaran varios símbolos en cada instrucción de declaración.  Observe que todos los símbolos de cada instrucción se resuelven en el mismo tipo.  
  
```cpp  
  
auto x = 1, *y = &x, **z = &y; // Resolves to int.  
auto a(2.01), *b (&a);         // Resolves to double.  
auto c = 'a', *d(&c);          // Resolves to char.  
auto m = 1, &n = m;            // Resolves to int.  
```  
  
 En este fragmento de código se utiliza el operador condicional \(`?:`\) para declarar la variable `x` como un entero que tiene un valor de 200:  
  
```cpp  
  
int v1 = 100, v2 = 200;  
auto x = v1 > v2 ? v1 : v2;  
```  
  
 En el fragmento de código siguiente se inicializa la `x` en el tipo `int`, la variable `y` en una referencia al tipo `const` `int` y la variable `fp` en un puntero a una función que devuelve el tipo `int`.  
  
```cpp  
  
int f(int x) { return x; }  
int main()  
{  
    auto x = f(0);  
    const auto & y = f(1);  
    int (*p)(int x);  
    p = f;  
    auto fp = p;  
    //...  
}  
  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../cpp/auto-keyword.md)   
 [\(NOTINBUILD\)Storage\-Class Specifiers](http://msdn.microsoft.com/es-es/10b3d22d-cb40-450b-994b-08cf9a211b6c)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [\/Zc:auto \(Deducir tipo de variable\)](../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof \(Operador\)](../cpp/sizeof-operator.md)   
 [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md)   
 [operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md)   
 [Declaraciones](../misc/declarations.md)   
 [Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md)   
 [Inicializadores](../cpp/initializers.md)   
 [decltype](../cpp/decltype-cpp.md)