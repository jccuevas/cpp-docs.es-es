---
title: "Expresiones lambda en C++ | Microsoft Docs"
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
helpviewer_keywords: 
  - "expresiones lambda [C++]"
  - "expresiones lambda [C++], información general"
  - "expresiones lambda [C++], frente a objetos de función"
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Expresiones lambda en C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En C\+\+11, una expresión lambda \(a menudo llamada *lambda*\) es una forma adecuada de definir un objeto de función anónima en la ubicación donde se invoca o se pasa como argumento a una función.  Normalmente, las lambdas se usan para encapsular unas líneas de código que se pasan a algoritmos o métodos asincrónicos.  En este artículo se define qué son las expresiones lambda, se comparan con otras técnicas de programación, se describen sus ventajas y se proporciona un ejemplo básico.  
  
## Partes de una expresión lambda  
 La norma ISO de C\+\+ muestra una expresión lambda sencilla que se pasa como tercer argumento a la función `std::sort()`:  
  
```cpp  
#include <algorithm>  
#include <cmath>  
  
void abssort(float* x, unsigned n) {  
    std::sort(x, x + n,  
        // Lambda expression begins  
        [](float a, float b) {  
            return (std::abs(a) < std::abs(b));  
        } // end of lambda expression  
    );  
}  
  
```  
  
 En esta ilustración se muestran las partes de una expresión lambda:  
  
 ![Elementos estructurales de una expresión lambda](../cpp/media/lambdaexpsyntax.png "LambdaExpSyntax")  
  
1.  *cláusula de captura* \(también conocida como *iniciador de expresión lambda* en la especificación de C\+\+\)  
  
2.  *lista de parámetros* Opcional  \(también conocida como *declarador de expresión lambda*\)  
  
3.  *especificación mutable* Opcional  
  
4.  *especificación de excepción* Opcional  
  
5.  *tipo de valor devuelto final* Opcional  
  
6.  *cuerpo de la expresión lambda*  
  
### Cláusula capture  
 Una expresión lambda puede introducir variables nuevas en el cuerpo \(en **C\+\+14**\) y también puede acceder a variables \(o *capturarlas*\) del ámbito circundante.  Una expresión lambda comienza con la cláusula de captura \(*iniciador de expresión lambda* en la sintaxis estándar\), que especifica las variables que se capturan y si la captura se efectúa por valor o por referencia.  A las variables que tienen como prefijo una y comercial \(`&`\) se accede mediante referencia y a las variables que no tienen el prefijo se accede por valor.  
  
 Una cláusula de captura vacía, `[ ]`, indica que el cuerpo de la expresión lambda no tiene acceso a ninguna variable en el ámbito de inclusión.  
  
 Puede usar el modo de captura predeterminado \(`capture-default` en la sintaxis estándar\) para indicar cómo se debe capturar cualquier variable exterior a la que se haga referencia en la expresión lambda: \[&\] significa que todas las variables a las que hace referencia se capturan por referencia, mientras que \[\=\] significa que se capturan por valor.  Puede usar un modo de captura predeterminado y, después, especificar el modo opuesto de forma explícita para unas variables específicas.  Por ejemplo, si el cuerpo de una expresión lambda accede a la variable externa `total` por referencia y a la variable externa `factor` por valor, las siguientes cláusulas capture serán equivalentes:  
  
```cpp  
  
[&total, factor]  
[factor, &total]  
[&, factor]  
[factor, &]  
[=, &total]  
[&total, =]  
```  
  
 Solo se capturan las variables que se mencionan en la expresión lambda cuando se usa una `capture-default`.  
  
 Si una cláusula de captura incluye `capture-default` `&`, ningún `identifier` de `capture` de la cláusula de captura puede tener el formato `& identifier`.  Del mismo modo, si la cláusula de captura incluye `capture-default` `=`, ningún `capture` de la cláusula de captura puede tener el formato `= identifier`.  Un identificador o `this` no puede aparecer más de una vez en una cláusula capture.  En el fragmento de código siguiente se muestran algunos ejemplos.  
  
```cpp  
struct S { void f(int i); };  
  
void S::f(int i) {  
    [&, i]{};    // OK  
    [&, &i]{};   // ERROR: i preceded by & when & is the default  
    [=, this]{}; // ERROR: this when = is the default  
    [i, i]{};    // ERROR: i repeated  
}  
```  
  
 Un `capture` seguido de puntos suspensivos es una expansión del paquete, como se muestra en el siguiente ejemplo de [plantilla variádica](../cpp/ellipses-and-variadic-templates.md):  
  
```cpp  
template<class... Args>  
void f(Args... args) {  
    auto x = [args...] { return g(args...); };  
    x();  
}  
```  
  
 Para usar expresiones lambda en el cuerpo de un método de clase, pase el puntero `this` a la cláusula de captura para proporcionar acceso a los métodos y miembros de datos de la clase contenedora.  Para obtener un ejemplo en el que se muestra cómo usar expresiones lambda con métodos de clase, vea "Ejemplo: usar una expresión lambda expresión en un método" en [Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).  
  
 Al usar la cláusula de captura, se recomienda tener en cuenta estos aspectos importantes, especialmente cuando se usan expresiones lambda con multithreading:  
  
-   Se pueden usar capturas por referencia para modificar variables externas, pero no se pueden usar capturas por valor.  \(`mutable` permite modificar las copias, pero no los originales\).  
  
-   Las capturas por referencia reflejan actualizaciones en variables externas, pero las capturas por valor no.  
  
-   Las capturas por referencia presentan una dependencia de la duración, pero las capturas por valor no tienen ninguna dependencia de la duración.  Esto es muy importante cuando la expresión lambda se inicia de forma asincrónica.  Si captura una variable local por referencia en una expresión lambda asincrónica, es muy probable que dicha variable desaparezca en cuanto se inicie la expresión lambda, lo que provocará una infracción de acceso en tiempo de ejecución.  
  
 **Captura generalizada \(C\+\+ 14\)**  
  
 En C\+\+14 puede introducir e inicializar nuevas variables en la cláusula de captura sin necesidad de que dichas variables existan en el ámbito de inclusión de la función lambda.  La inicialización se puede expresar como cualquier expresión arbitraria; el tipo de la variable nueva se deduce del tipo producido por la expresión.  Una ventaja de esta característica es que en C\+\+14 puede capturar variables solo de movimiento \(por ejemplo, std::unique\_ptr\) del ámbito circundante y usarlas en una expresión lambda.  
  
```  
pNums = make_unique<vector<int>>(nums);  
//...  
      auto a = [ptr = move(pNums)]()  
        {  
           // use ptr  
        };  
```  
  
### Lista de parámetros  
 Además de capturar variables, una expresión lambda puede aceptar parámetros de entrada.  La lista de parámetros \(*declarador de expresión lambda* en la sintaxis estándar\) es opcional y, en la mayoría de los aspectos, es similar a la lista de parámetros de una función.  
  
```  
int y = [] (int first, int second)  
{  
    return first + second;  
};  
  
```  
  
 En **C\+\+ 14**, si el tipo de parámetro es genérico, puede usar la palabra clave "auto" como especificador de tipo.  Esto indica al compilador que debe crear el operador de llamada de función como plantilla.  Cada instancia de "auto" en una lista de parámetros es equivalente a un parámetro de tipo distinto.  
  
```  
auto y = [] (auto first, auto second)  
{  
    return first + second;  
};  
```  
  
 Una expresión lambda puede tomar otra expresión lambda como argumento.  Para más información, vea "Expresiones lambda de orden superior" en el tema [Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).  
  
 La lista de parámetros es opcional, por lo que puede omitir los paréntesis vacíos si no pasa argumentos a la expresión lambda y su `lambda-declarator:` no contiene *exception\-specification*, *trailing\-return\-type* o `mutable`.  
  
### Especificación mutable  
 Normalmente, el operador de llamada a función de una expresión lambda es const\-by\-value, pero `mutable` lo cancela.  No genera miembros de datos mutable.  La especificación mutable permite al cuerpo de una expresión lambda modificar las variables que se capturan por valor.  Algunos de los ejemplos que se incluyen más adelante en este artículo muestran el uso de la palabra clave `mutable`.  
  
### Especificación de la excepción  
 Puede utilizar la especificación de excepción `throw()` para indicar que la expresión lambda no produce ninguna excepción.  Como con las funciones normales, el compilador de Visual C\+\+ genera la advertencia [C4297](../Topic/Compiler%20Warning%20\(level%201\)%20C4297.md) si una expresión lambda declara la especificación de excepción `throw()` y el cuerpo de la expresión lambda produce una excepción, como se muestra aquí:  
  
```cpp  
// throw_lambda_expression.cpp  
// compile with: /W4 /EHsc   
int main() // C4297 expected  
{  
   []() throw() { throw 5; }();  
}  
```  
  
 Para más información, vea [Especificaciones de excepciones \(throw\)](../cpp/exception-specifications-throw-cpp.md).  
  
### Tipo devuelto  
 El tipo de valor devuelto de una expresión lambda se deduce automáticamente.  No es necesario usar la palabra clave [auto](../cpp/auto-cpp.md) a menos que se especifique un *trailing\-return\-type*.  El *trailing\-return\-type* es similar a la parte del tipo de valor devuelto de un método o función normal.  Pero el tipo de valor devuelto debe seguir la lista de parámetros y debe incluir la palabra clave trailing\-return\-type `->` antes del tipo de valor devuelto.  
  
 Puede omitir la parte return\-type de una expresión lambda si el cuerpo de la expresión lambda contiene una sola instrucción return o si la expresión lambda no devuelve un valor.  Si el cuerpo de la expresión lambda contiene una instrucción return, el compilador deduce el tipo de valor devuelto del tipo de expresión return.  En caso contrario, el compilador deduce que el tipo de valor devuelto es `void`.  Vea los fragmentos de código de ejemplo siguientes que muestran este principio.  
  
```cpp  
auto x1 = [](int i){ return i; }; // OK: return type is int  
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing   
                                  // return type from braced-init-list is not valid  
  
```  
  
 Una expresión lambda puede generar otra expresión lambda como valor devuelto.  Para más información, vea "Expresiones lambda de orden superior" en [Ejemplos de expresiones lambda](../cpp/examples-of-lambda-expressions.md).  
  
### Cuerpo lambda  
 La parte del cuerpo lambda \(*compound\-statement* en la sintaxis estándar\) de una expresión lambda puede contener todos los elementos que puede tener el cuerpo de un método o función normal.  El cuerpo de una función normal y de una expresión lambda puede tener acceso a estos tipos de variables:  
  
-   variables capturadas en el ámbito de inclusión, tal como se describió anteriormente.  
  
-   Parámetros  
  
-   Variables declaradas localmente  
  
-   Miembros de datos de la clase \(cuando se declara dentro de una clase y se captura `this`\)  
  
-   Cualquier variable que tenga duración de almacenamiento estática \(por ejemplo, las variables globales\)  
  
 El ejemplo siguiente contiene una expresión lambda que captura explícitamente la variable `n` por valor y captura implícitamente la variable `m` por referencia:  
  
```cpp  
// captures_lambda_expression.cpp  
// compile with: /W4 /EHsc   
#include <iostream>  
using namespace std;  
  
int main()  
{  
   int m = 0;  
   int n = 0;  
   [&, n] (int a) mutable { m = ++n + a; }(4);  
   cout << m << endl << n << endl;  
}  
```  
  
 **Resultado:**  
  
  **5**  
**0** Como la variable `n` se captura por valor, el valor sigue siendo `0` después de la llamada a la expresión lambda.  La especificación `mutable` permite modificar `n` dentro de la expresión lambda.  
  
 Aunque una expresión lambda solo puede capturar variables que tengan duración de almacenamiento automática, puede utilizar variables que tengan duración de almacenamiento estática en el cuerpo de una expresión lambda.  En el ejemplo siguiente se utiliza la función `generate` y una expresión lambda para asignar un valor a cada elemento de un objeto `vector`.  La expresión lambda modifica la variable estática para generar el valor del elemento siguiente.  
  
```cpp  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });   
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
```  
  
 Para más información, vea [generar](../Topic/generate.md).  
  
 En el ejemplo de código siguiente se usa la función del ejemplo anterior y se agrega un ejemplo de una expresión lambda que usa el algoritmo `generate_n` de STL.  Esta expresión lambda asigna un elemento de un objeto `vector` a la suma de los dos elementos anteriores.  Se usa la palabra clave `mutable` de modo que el cuerpo de la expresión lambda pueda modificar sus copias de las variables externas `x` e `y`, que la expresión lambda captura por valor.  Como la expresión lambda captura las variables originales `x` e `y` por valor, sus valores siguen siendo `1` después de la ejecución de la expresión.  
  
```cpp  
// compile with: /W4 /EHsc  
#include <algorithm>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });  
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
  
int main()  
{  
    // The number of elements in the vector.  
    const int elementCount = 9;  
  
    // Create a vector object with each element set to 1.  
    vector<int> v(elementCount, 1);  
  
    // These variables hold the previous two elements of the vector.  
    int x = 1;  
    int y = 1;  
  
    // Sets each element in the vector to the sum of the   
    // previous two elements.  
    generate_n(v.begin() + 2,  
        elementCount - 2,  
        [=]() mutable throw() -> int { // lambda is the 3rd parameter  
        // Generate current value.  
        int n = x + y;  
        // Update previous two values.  
        x = y;  
        y = n;  
        return n;  
    });  
    print("vector v after call to generate_n() with lambda: ", v);  
  
    // Print the local variables x and y.  
    // The values of x and y hold their initial values because   
    // they are captured by value.  
    cout << "x: " << x << " y: " << y << endl;  
  
    // Fill the vector with a sequence of numbers  
    fillVector(v);  
    print("vector v after 1st call to fillVector(): ", v);  
    // Fill the vector with the next sequence of numbers  
    fillVector(v);  
    print("vector v after 2nd call to fillVector(): ", v);  
}  
  
```  
  
 **Resultado:**  
  
  **vector v after call to generate\_n\(\) with lambda: 1 1 2 3 5 8 13 21 34**  
**x: 1 y: 1**  
**vector v after 1st call to fillVector\(\): 1 2 3 4 5 6 7 8 9**  
**vector v after 2nd call to fillVector\(\): 10 11 12 13 14 15 16 17 18** Para más información, vea [generate\_n](../Topic/generate_n.md).  
  
## Específico de Microsoft  
 Las expresiones lambda no se admite en las entidades administradas siguientes de Common Language Runtime \(CLR\): `ref class`, `ref struct`, `value class` o `value struct`.  
  
 Si usa un modificador específico de Microsoft, como [\_\_declspec](../cpp/declspec.md), puede insertarlo en una expresión lambda inmediatamente después de `parameter-declaration-clause`, como en el ejemplo siguiente:  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
  
```  
  
 Para determinar si un modificador es compatible con las expresiones lambda, consulte el artículo correspondiente en la sección [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md) de la documentación.  
  
 Visual Studio la sintaxis de expresiones lambda y las funciones del estándar C\+\+11, con las siguientes excepciones:  
  
-   Al igual que el resto de clases, las expresiones lambda no obtienen constructores de movimiento ni operadores de asignación de movimiento generados automáticamente.  Para más información sobre la compatibilidad con los comportamientos de referencia a un valor R, vea la sección "Referencias a valores R" de [Compatibilidad con las características de C\+\+11\/14\/17](../cpp/support-for-cpp11-14-17-features-modern-cpp.md).  
  
-   El elemento *attribute\-specifier\-seq* no se admite en esta versión.  
  
 Visual Studio incluye estas características además de la función de expresiones lambda del estándar C\+\+11:  
  
-   Las expresiones lambda sin estado, que se pueden convertir a punteros de función con convenciones de llamada arbitrarias.  
  
-   Tipos de valores devueltos deducidos automáticamente para cuerpos lambda que son más complicados que `{ return expression; }`, si todas las instrucciones de valor devuelto tienen el mismo tipo  \(esta función forma parte del estándar C\+\+14 propuesto\).  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Objetos de función en STL](../standard-library/function-objects-in-the-stl.md)   
 [Llamada de función](../cpp/function-call-cpp.md)   
 [for\_each](../Topic/for_each.md)