---
title: "Funciones insertadas (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__forceinline_cpp"
  - "__inline_cpp"
  - "inline_cpp"
  - "__forceinline"
  - "__inline"
  - "inline"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones inline, miembros de clases"
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones insertadas (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una función definida en el cuerpo de una declaración de clase es una función insertada.  
  
## Ejemplo  
 En la siguiente declaración de clase, el constructor `Account` es una función insertada.  Las funciones miembro `GetBalance`, `Deposit` y `Withdraw` no se especifican como **inline**, pero se puede implementar como funciones insertadas.  
  
```  
// Inline_Member_Functions.cpp  
class Account  
{  
public:  
    Account(double initial_balance) { balance = initial_balance; }  
    double GetBalance();  
    double Deposit( double Amount );  
    double Withdraw( double Amount );  
private:  
    double balance;  
};  
  
inline double Account::GetBalance()  
{  
    return balance;  
}  
  
inline double Account::Deposit( double Amount )  
{  
    return ( balance += Amount );  
}  
  
inline double Account::Withdraw( double Amount )  
{  
    return ( balance -= Amount );  
}  
int main()  
{  
}  
```  
  
> [!NOTE]
>  En la declaración de clase, las funciones se declaran sin la palabra clave **inline**.  La palabra clave **inline** se puede especificar en la declaración de clase; el resultado es el mismo.  
  
 Una función de miembro insertada determinada se debe declarar de la misma manera en cada unidad de compilación.  Esta restricción hace que las funciones insertadas se comporten como si fuesen funciones con instancias creadas.  Además, debe haber exactamente una definición de una función insertada.  
  
 Una función miembro de clase utiliza de manera predeterminada una vinculación externa, a menos que una definición de esa función contenga el especificador **inline**.  En el ejemplo anterior, se muestra que estas funciones no necesitan declararse explícitamente con el especificador **inline**; al usar **inline** en la definición de función, ya se convierte en una función insertada.  Sin embargo, no es válido volver a declarar una función como **inline** después de una llamada a esa función.  
  
## Inline, \_\_inline y \_\_forceinline  
 Los especificadores `inline` e `__inline` indican al compilador que inserte una copia del cuerpo de la función en cada lugar donde se llama a la función.  
  
 La inserción \(denominada expansión alineada o alineación\) solo se realiza si el análisis de costos y beneficios del compilador resulta ser rentable.  La expansión alineada alivia la sobrecarga de las llamadas a función con el costo potencial de un tamaño de código mayor.  
  
 La palabra clave `__forceinline` invalida el análisis de costos y beneficios, y deja la decisión en manos del programador.  Hay que ser prudentes al utilizar `__forceinline`.  El uso indiscriminado de `__forceinline` puede dar lugar a código mayor con unas mejoras de rendimiento mínimas o, en algunos casos, incluso con pérdidas de rendimiento \(debido a la mayor paginación que supone un archivo ejecutable mayor, por ejemplo\).  
  
 El uso de funciones insertadas puede agilizar la ejecución del programa porque eliminan la sobrecarga asociada a las llamadas a función.  Las funciones expandidas insertadas están sujetas a optimizaciones de código que no están disponibles para las funciones normales.  
  
 El compilador trata las opciones de expansión insertada y las palabras clave como sugerencias.  No se garantiza que las funciones se inserten.  No se puede forzar que el compilador inserte una función determinada, incluso con la palabra clave `__forceinline`.  Al compilar con **\/clr**, el compilador no insertará una función si se aplican atributos de seguridad a la función.  
  
 La palabra clave **inline** solo está disponible en C\+\+.  Las palabras clave `__inline` y `__forceinline` están disponibles tanto en C como en C\+\+.  Por compatibilidad con versiones anteriores, **inline** es sinónimo de `__inline`.  
  
 La palabra clave **inline** indica al compilador que se prefiere la expansión alineada.  Sin embargo, el compilador puede crear una instancia independiente de la función y crear vinculaciones de llamada estándar en lugar de insertar el código.  Hay dos casos en los que esto puede ocurrir:  
  
-   Funciones recursivas.  
  
-   Funciones a las que se hace referencia mediante un puntero en otra parte de la unidad de traducción.  
  
 Estos motivos pueden interferir con la alineación, *igual que otros*, a discreción del compilador; no debe depender del especificador **inline** para que se inserte una función.  
  
 Como ocurre con las funciones normales, no hay ningún orden definido de evaluación de los argumentos de una función insertada.  De hecho, podría ser diferente del orden en que se evalúan los argumentos cuando se pasan mediante el protocolo normal de llamadas a función.  
  
 La opción [\/Ob](../build/reference/ob-inline-function-expansion.md) de optimización del compilador ayuda a determinar si la expansión de funciones insertadas se produce realmente.  
  
 [\/LTCG](../build/reference/ltcg-link-time-code-generation.md) realiza la inserción entre módulos independientemente de que se solicitara o no en el código fuente.  
  
### Ejemplo 1  
  
```  
// inline_keyword1.cpp  
// compile with: /c  
inline int max( int a , int b ) {  
   if( a > b )   
      return a;  
   return b;  
}  
```  
  
 Las funciones miembro de una clase se pueden declarar alineadas mediante la palabra clave **inline** o colocando la definición de función dentro de la definición de clase.  
  
### Ejemplo 2  
  
```  
// inline_keyword2.cpp  
// compile with: /EHsc /c  
#include <iostream>  
using namespace std;  
  
class MyClass {  
public:  
   void print() { cout << i << ' '; }   // Implicitly inline  
private:  
   int i;  
};  
```  
  
### Específicos de Microsoft  
 La palabra clave `__inline` es equivalente a **inline**.  
  
 Incluso con `__forceinline`, el compilador no puede insertar código en todas las circunstancias.  El compilador no puede insertar una función si:  
  
-   La función o su llamador se compila con \/Ob0 \(la opción predeterminada para las compilaciones de depuración\).  
  
-   La función y el llamador utilizan tipos diferentes de control de excepciones \(control de excepciones de C\+\+ en uno y control de excepciones estructurado en otro\).  
  
-   La función tiene una lista de argumentos de variable.  
  
-   La función utiliza el ensamblado insertado, a menos que se compile con \/Og, \/Ox, \/O1 o \/O2.  
  
-   La función es recursiva y no va acompañada de la directiva **\#pragma inline\_recursion\(on\)**.  Con la directiva pragma, las funciones recursivas se alinean hasta una profundidad predeterminada de 16 llamadas.  Para reducir la profundidad de inserción, utilice la directiva pragma [inline\_depth](../preprocessor/inline-depth.md).  
  
-   La función es virtual y se llama a la misma de forma virtual.  Se pueden insertar llamadas directas a funciones virtuales.  
  
-   El programa toma la dirección de la función y la llamada se realiza a través del puntero a la función.  Se pueden insertar llamadas directas a funciones cuyas direcciones se han tomado.  
  
-   La función está marcada también con el modificador [naked](../cpp/naked-cpp.md) [\_\_declspec](../cpp/declspec.md).  
  
 Si el compilador no puede insertar una función declarada con `__forceinline`, genera una advertencia de nivel 1.  
  
 Se pueden sustituir las funciones recursivas insertadas hasta una profundidad especificada por la directiva pragma [inline\_depth](../preprocessor/inline-depth.md), hasta un máximo de 16 llamadas.  Después de dicha profundidad, las llamadas a función recursivas se tratan como llamadas a una instancia de la función.  La profundidad a la que la heurística de alineación examina las funciones recursivas no puede ser superior a 16.  La directiva pragma [inline\_recursion](../preprocessor/inline-recursion.md) controla la expansión alineada de una función que se está expandiendo actualmente.  Vea la opción del compilador [Expansión de funciones insertadas](../build/reference/ob-inline-function-expansion.md) \(\/Ob\) para obtener información relacionada.  
  
### FIN de Específicos de Microsoft  
 Para obtener más información sobre cómo utilizar el especificador **inline**, vea:  
  
-   [Funciones insertadas de miembro de clase](../cpp/inline-functions-cpp.md)  
  
-   [Funciones insertadas frente a macros](../misc/inline-functions-versus-macros.md)  
  
-   [Cuándo utilizar funciones insertadas](../misc/when-to-use-inline-functions.md)  
  
-   [Definir funciones insertadas de C\+\+ con dllexport y dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
## Cuándo usar funciones insertadas  
 Las funciones insertadas son útiles para funciones pequeñas, como el acceso a miembros de datos privados.  El propósito principal de estas funciones de "descriptor de acceso" de una o dos líneas es devolver información de estado sobre los objetos; las funciones cortas son sensibles a la sobrecarga de llamadas a función.  Las funciones más largas tardan proporcionalmente menos tiempo en la secuencia de llamada\/devolución y se benefician menos de la inserción.  
  
 La clase `Point`, incluida en [Resultados de llamada de función](../misc/function-call-results.md) se puede optimizar como sigue:  
  
```  
// when_to_use_inline_functions.cpp  
class Point  
{  
public:  
    // Define "accessor" functions as  
    //  reference types.  
    unsigned& x();  
    unsigned& y();  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
inline unsigned& Point::x()  
{  
    return _x;  
}  
inline unsigned& Point::y()  
{  
    return _y;  
}  
int main()  
{  
}  
```  
  
 Si se da por hecho que la manipulación coordinada es una operación relativamente común en un cliente de esta clase, especificar las dos funciones de descriptor de acceso \(`x` y `y` en el ejemplo anterior\) como **inline** normalmente evita la sobrecarga en:  
  
-   Llamadas de función \(incluidos el paso de parámetros y la colocación de la dirección del objeto en la pila\)  
  
-   Conservación del marco de pila del llamador  
  
-   Nueva configuración del marco de pila  
  
-   Comunicación de valor devuelto  
  
-   Restauración del marco de pila antiguo  
  
-   Volver  
  
## Funciones insertadas frente amacros  
 Aunque las funciones insertadas son similares a las macros \(porque el código de función se expande en el momento de la llamada en tiempo de compilación\), el compilador analiza las funciones insertadas, mientras que el preprocesador expande las macros.  Como consecuencia, hay varias diferencias importantes:  
  
-   Las funciones insertadas siguen todos los protocolos de seguridad de tipos exigidos en funciones normales.  
  
-   Las funciones insertadas se especifican utilizando la misma sintaxis que cualquier otra función salvo que incluyen la palabra clave **inline** en la declaración de función.  
  
-   Las expresiones pasadas como argumentos a funciones insertadas se evalúan una vez.  En algunos casos, las expresiones pasadas como argumentos a macros se pueden evaluar más de una vez.  
  
 En el ejemplo siguiente se muestra una macro que convierte las minúsculas en mayúsculas:  
  
```  
// inline_functions_macro.c  
#include <stdio.h>  
#include <conio.h>  
  
#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))  
  
int main() {  
   char ch;  
   printf_s("Enter a character: ");  
   ch = toupper( getc(stdin) );  
   printf_s( "%c", ch );  
}  
//  Sample Input:  xyz  
// Sample Output:  Z  
  
```  
  
 El objeto de la expresión `toupper(getc(stdin))` es que un carácter se deba leer desde el dispositivo de consola \(`stdin`\) y, si es necesario, se convierta a mayúsculas.  
  
 Debido a la implementación de la macro, `getc` se ejecuta una vez para determinar si el carácter es mayor o igual que "a", y una vez para determinar si es menor o igual que "z". Si está en ese intervalo, `getc` se ejecuta de nuevo para convertir el carácter a mayúsculas.  Esto significa que el programa espera dos o tres caracteres cuando, idealmente, debe esperar solo uno.  
  
 Las funciones insertadas solucionan el problema descrito anteriormente:  
  
```  
// inline_functions_inline.cpp  
#include <stdio.h>  
#include <conio.h>  
  
inline char toupper( char a ) {  
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );  
}  
  
int main() {  
   printf_s("Enter a character: ");  
   char ch = toupper( getc(stdin) );  
   printf_s( "%c", ch );  
}  
```  
  
  **Entrada de ejemplo: `a`**   
 **Salida de ejemplo: `A`**    
## Vea también  
 [noinline](../cpp/noinline.md)   
 [auto\_inline](../preprocessor/auto-inline.md)