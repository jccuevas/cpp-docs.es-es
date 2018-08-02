---
title: Conversiones estándar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1365e950077a65150d8f71fd640f69d1750068c9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462315"
---
# <a name="standard-conversions"></a>Conversiones estándar
El lenguaje C++ define conversiones entre sus tipos fundamentales. También define conversiones para tipos derivados de puntero, referencia y puntero a miembro. Estas conversiones se denominan "conversiones estándar". (Para obtener más información sobre los tipos, tipos estándar y los tipos derivados, vea [tipos](http://msdn.microsoft.com/6882ee83-ea32-4373-8d57-c3efbbc15af0).)  
  
 Esta sección trata las conversiones estándar siguientes:  
  
-   Promociones de enteros  
  
-   Conversiones de enteros  
  
-   Conversiones de punto flotante  
  
-   Conversiones de punto flotante y de enteros  
  
-   Conversiones aritméticas  
  
-   Conversiones de puntero  
  
-   Conversiones de referencia  
  
-   Conversiones de puntero a miembro  
  
    > [!NOTE]
    >  Los tipos definidos por el usuario pueden especificar sus propias conversiones. Conversión de tipos definidos por el usuario se trata en [constructores](../cpp/constructors-cpp.md) y [conversiones](../cpp/user-defined-type-conversions-cpp.md).  
  
El código siguiente provoca conversiones (en este ejemplo, promociones de enteros):  
  
```cpp 
long  long_num1, long_num2;  
int   int_num;  
  
// int_num promoted to type long prior to assignment.  
long_num1 = int_num;  
  
// int_num promoted to type long prior to multiplication.  
long_num2 = int_num * long_num2;  
```  
  
 El resultado de una conversión solo es un valor L si genera un tipo de referencia. Por ejemplo, una conversión definida por el usuario se declara como `operator int&()` devuelve una referencia y es un valor l. Sin embargo, una conversión declarada como `operator int()`devuelve un objeto y no es un valor l.  
  
## <a name="integral-promotions"></a>Promociones de enteros  
 Los objetos de un tipo entero se pueden convertir a otro tipo entero más amplio (es decir, un tipo que puede representar un conjunto de valores más grande). Este tipo de ampliación de conversión se denomina "promoción de entero". Con la promoción de entero, puede utilizar lo siguiente en una expresión dondequiera que otro tipo entero se pueda utilizar:  
  
-   Objetos, literales y constantes de tipo **char** y **short int**  
  
-   Tipos de enumeración  
  
-   **int** campos de bits  
  
-   Enumeradores  
  
 Las promociones de C++ tienen la cualidad de "conservación de valores". Es decir, se garantiza que el valor después de la promoción es igual que el valor antes de la promoción. En las promociones cualidad de conservación, objetos de tipos enteros más cortos (como campos de bits u objetos de tipo **char**) se promueve al tipo **int** si **int** puede representar el completo intervalo del tipo original. Si **int** no puede representar el intervalo completo de valores, a continuación, el objeto se promueve al tipo **int sin signo**. Aunque esta estrategia es la misma que la utilizada por ANSI C, las conversiones que poseen la cualidad de conservación de valores no conservan el "tipo signed/unsigned" del objeto.  
  
 Las promociones que poseen la cualidad de conservación de valores y las promociones que conservan el tipo signed/unsigned generan normalmente los mismos resultados. Sin embargo, pueden generar resultados diferentes si el objeto que se promueve es uno de los siguientes:  
  
-   Un operando de **/**, `%`, `/=`, `%=`, **<**, **\< =**, **>**, o **>=**  
  
     Estos operadores dependen del signo para determinar el resultado. Por consiguiente, las promociones que poseen la cualidad de conservación de valores y que conservan el tipo signed/unsigned generan resultados diferentes cuando se aplican a estos operandos.  
  
-   El operando izquierdo de **>>** o **>>=**  
  
     Estos operadores tratan las cantidades signed y unsigned de forma diferente cuando realizan una operación de desplazamiento. En el caso de cantidades signed, el desplazamiento de una cantidad a la derecha hace que el bit de signo se propague a las posiciones de bits desocupadas. En el caso de cantidades unsigned, las posiciones de bits desocupadas se rellenan con ceros.  
  
-   Un argumento a una función sobrecargada o un operando de un operador sobrecargado que depende de la condición signed/unsigned de dicho operando para la coincidencia de argumentos. (Consulte [operadores sobrecargados](../cpp/operator-overloading.md) para obtener más información acerca de cómo definir operadores sobrecargados.)  
  
## <a name="integral-conversions"></a>Conversiones de enteros  
 Las conversiones de enteros se realizan entre tipos enteros. Los tipos enteros son **char**, **int**, y **largo** (y el **corto**, **firmado**y **sin signo** versiones de estos tipos).  
  
 **Signed a unsigned**  
  
 Los objetos de tipos enteros con signo se pueden convertir en los tipos sin signo correspondientes. Cuando se produce esta conversión, el patrón de bits real no cambia, pero sí la interpretación de los datos. Considere este código:  
  
```cpp 
#include <iostream>  
  
using namespace std;  
int main()  
{  
    short  i = -3;  
    unsigned short u;  
  
    cout << (u = i) << "\n";  
}  
// Output: 65533  
```  
  
 En el ejemplo anterior, un **firmado resumen**, `i`, se define y se inicializa en un número negativo. La expresión `(u = i)` hace `i` va a convertir en un **entero corto sin signo** antes de la asignación a `u`.  
  
 **Unsigned a signed**  
  
 Los objetos de tipos enteros sin signo se pueden convertir en los tipos con signo correspondientes. Sin embargo, este tipo de conversión puede producir una interpretación incorrecta de los datos si el valor del objeto sin signo está fuera del intervalo que puede representar el tipo con signo, como se muestra en el ejemplo siguiente:  
  
```cpp
#include <iostream>  
  
using namespace std;  
int main()  
{  
 short  i;  
 unsigned short u = 65533;  
  
 cout << (i = u) << "\n";  
}  
//Output: -3  
```  
  
 En el ejemplo anterior, `u` es un **entero corto sin signo** objeto integral que se debe convertir en una cantidad con signo para evaluar la expresión `(i = u)`. Dado que su valor no puede representarse correctamente en un **firmado resumen**, los datos se interprete erróneamente como se muestra.  
  
## <a name="floating-point-conversions"></a>Conversiones de punto flotante  
 Un objeto de tipo flotante se puede convertir de forma segura en un tipo flotante más preciso; es decir, la conversión no provoca ninguna pérdida de significado. Por ejemplo, las conversiones de **float** a **doble** o desde **doble** a **long double** son seguras y el valor no se ha modificado.  
  
 Un objeto de tipo flotante se puede convertir en un tipo menos preciso, si se encuentra en un intervalo representable por ese tipo. (Consulte [límites de punto flotante](../cpp/floating-limits.md) para los intervalos de tipo flotante.) Si el valor original no se puede representar con exactitud, se puede convertir en el siguiente valor representable mayor o menor. Si no existe dicho valor, el resultado es indefinido. Considere el ejemplo siguiente:  
  
```cpp
cout << (float)1E300 << endl;  
```  
  
 El valor máximo que se puede representar por tipo **float** es 3.402823466E38: un número mucho menor que 1E300. Por lo tanto, el número se convierte a infinito y el resultado es "inf".  
  
## <a name="conversions-between-integral-and-floating-point-types"></a>Conversiones entre tipos integrales y de punto flotante  
 Algunas expresiones pueden producir la conversión de objetos de tipo flotante a tipos enteros, o viceversa. Cuando un objeto de tipo entero se convierte a un tipo flotante y el valor original no se puede representar correcta, el resultado es el siguiente valor más alto o más bajo que se puede representar.  
  
 Cuando un objeto de tipo flotante se convierte en un tipo entero, se trunca la parte fraccionaria. No se realiza ningún redondeo en el proceso de conversión. El truncamiento significa que un número como 1,3 se convierte en 1 y-1.3 se convierte en -1.  
  
## <a name="arithmetic-conversions"></a>Conversiones aritméticas  
 Muchos operadores binarios (descritos en [expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)) originan la conversión de operandos y producen resultados de la misma manera. La manera en que estos operadores producen conversiones se denomina “conversiones aritméticas usuales”. Las conversiones aritméticas de operandos de diferentes tipos nativos se realizan como se muestra en la tabla siguiente. Los tipos typedef se comportan de acuerdo con sus tipos nativos subyacentes.  
  
### <a name="conditions-for-type-conversion"></a>Condiciones para la conversión de tipos  
  
|Condiciones satisfechas|Conversión|  
|--------------------|----------------|  
|Uno de los operandos es de tipo **long double**.|Otro operando se convierte al tipo **long double**.|  
|Anterior no se cumplió la condición y alguno de los operandos es de tipo **doble**.|Otro operando se convierte al tipo **doble**.|  
|Anterior condiciones no se cumplen y alguno de los operandos es de tipo **float**.|Otro operando se convierte al tipo **float**.|  
|Las condiciones anteriores no se satisfacen (ninguno de los operandos es de tipo flotante).|Las promociones de entero se realizan en los operandos de la forma siguiente:<br /><br /> -Si alguno de los operandos es de tipo **unsigned long**, el otro operando se convierte al tipo **unsigned long**.<br />-Si la condición anterior no se cumple y si alguno de los operandos es de tipo **largo** y otro de tipo **int sin signo**, ambos operandos se convierten al tipo **unsigned long**.<br />-Si no se cumplen las dos condiciones anteriores, y si alguno de los operandos es de tipo **largo**, el otro operando se convierte al tipo **largo**.<br />-Si no se cumplen las tres condiciones anteriores, y si alguno de los operandos es de tipo **int sin signo**, el otro operando se convierte al tipo **int sin signo**.<br />-Si se cumple ninguna de las condiciones anteriores, ambos operandos se convierten al tipo **int**.|  
  
 En el código siguiente se muestran las reglas de conversión descritas en la tabla:  
  
```cpp 
double dVal;  
float fVal;  
int iVal;  
unsigned long ulVal;  
  
int main() {  
   // iVal converted to unsigned long  
   // result of multiplication converted to double  
   dVal = iVal * ulVal;  
  
   // ulVal converted to float  
   // result of addition converted to double  
   dVal = ulVal + fVal;  
}  
```  
  
 La primera instrucción del ejemplo anterior muestra la multiplicación de dos tipos enteros, `iVal` y `ulVal`. La condición satisfecha es que ninguno de los operandos es de tipo flotante y uno de los operandos es de tipo **int sin signo**. Por lo tanto, el otro operando, `iVal`, se convierte al tipo **int sin signo**. El resultado se asigna a `dVal`. La condición satisfecha es que un operando es de tipo **doble**; por lo tanto, el **int sin signo** resultado de la multiplicación se convierte al tipo **doble**.  
  
 La segunda instrucción en el ejemplo anterior muestra la adición de un **float** y un tipo entero, `fVal` y `ulVal`. El `ulVal` variable se convierte al tipo **float** (la tercera condición en la tabla). El resultado de la suma se convierte al tipo **doble** (la segunda condición en la tabla) y se asigna a `dVal`.  
  
## <a name="pointer-conversions"></a>Conversiones de puntero  
 Los punteros se pueden convertir durante la asignación, inicialización, comparación y en otras expresiones.  
  
### <a name="pointer-to-classes"></a>De puntero a clases  
 Hay dos casos en los que un puntero a una clase se puede convertir en un puntero a una clase base.  
  
 El primer caso es cuando la clase base especificada es accesible y la conversión es inequívoca. (Consulte [varias clases Base](../cpp/multiple-base-classes.md) para obtener más información acerca de las referencias de clase base ambiguas.)  
  
 Si una clase base es accesible depende del tipo de herencia utilizada en la derivación. Considere la herencia que se muestra en la siguiente ilustración.  
  
 ![Gráfico de herencia que muestra base&#45;clase accesibilidad](../cpp/media/vc38xa1.gif "vc38XA1")  
Gráfico de herencia para ilustrar la accesibilidad de clase base  
  
 En la tabla siguiente se muestra la accesibilidad de la clase base para la situación que se muestra en la ilustración.  
  
### <a name="base-class-accessibility"></a>Accesibilidad de la clase base  
  
|Tipo de función|Derivación|Conversión de<br /><br /> ¿B * a un\* Legal?|  
|----------------------|----------------|-------------------------------------------|  
|Función externa (no de ámbito de clase)|Private|No|  
||Protegido|No|  
||Public|Sí|  
|Función miembro B (en ámbito B)|Private|Sí|  
||Protegido|Sí|  
||Público|Sí|  
|Función miembro C (en ámbito C)|Privado|No|  
||Protegido|Sí|  
||Público|Sí|  
  
 El segundo caso en el que un puntero a una clase se puede convertir a un puntero a una clase base es cuando se utiliza una conversión de tipos explícita. (Consulte [expresiones con conversiones de tipo explícitas](http://msdn.microsoft.com/060ad6b4-9592-4f3e-8509-a20ac84a85ae) para obtener más información sobre las conversiones de tipo explícito.)  
  
 El resultado de tal conversión es un puntero al “subobjeto”, la parte del objeto que la clase base describe completamente.  
  
 En el código siguiente se definen dos clases, `A` y `B`, donde `B` se deriva de `A`. (Para obtener más información sobre la herencia, vea [clases derivadas](../cpp/inheritance-cpp.md).) A continuación, define `bObject`, un objeto de tipo `B` y dos punteros (`pA` y `pB`) que apuntan al objeto.  
  
```cpp 
// C2039 expected  
class A  
{  
public:  
    int AComponent;  
    int AMemberFunc();  
};  
  
class B : public A  
{  
public:  
    int BComponent;  
    int BMemberFunc();  
};  
int main()  
{  
   B bObject;  
   A *pA = &bObject;  
   B *pB = &bObject;  
  
   pA->AMemberFunc();   // OK in class A  
   pB->AMemberFunc();   // OK: inherited from class A  
   pA->BMemberFunc();   // Error: not in class A  
}  
```  
  
 El puntero `pA` es de tipo `A *`, los que se puede interpretar como “puntero a un objeto de tipo `A`”. Los miembros de `bObject` `(`como `BComponent` y `BMemberFunc`) son únicos para tipo `B` y, por tanto, son inaccesibles a través de `pA`. El puntero `pA` solo permite el acceso a esas características (funciones de miembro y datos) del objeto que se definen en la clase `A`.  
  
### <a name="pointer-to-function"></a>De puntero a función  
 Un puntero a una función se puede convertir al tipo `void *`si tipo `void *` es lo suficientemente grande como para contener ese puntero.  
  
### <a name="pointer-to-void"></a>De puntero a void  
 Punteros a tipo **void** se puede convertir a punteros a cualquier otro tipo, pero solo con una conversión de tipos explícita (a diferencia de C). (Consulte [expresiones con conversiones de tipo explícitas](http://msdn.microsoft.com/060ad6b4-9592-4f3e-8509-a20ac84a85ae) para obtener más información sobre conversiones de tipo.) Un puntero a cualquier tipo se puede convertir implícitamente a un puntero al tipo **void**. Un puntero a un objeto incompleto de un tipo se puede convertir en un puntero a **void** (implícitamente) y viceversa (explícitamente). El resultado de dicha conversión es igual al valor del puntero original. Un objeto se considera incompleto si se declara, pero no hay suficiente información disponible para determinar su tamaño o clase base.  
  
 Un puntero a cualquier objeto que no es **const** o **volátil** puede convertirse implícitamente a un puntero de tipo `void *`.  
  
### <a name="const-and-volatile-pointers"></a>punteros const y volatile  
 C++ no proporciona una conversión estándar de un **const** o **volátil** tipo a un tipo que no sea **const** o **volátil**. Sin embargo, se puede especificar cualquier tipo de conversión mediante conversiones de tipos explícitas (incluidas las conversiones que no son seguras).  
  
> [!NOTE]
>  Los punteros a miembros de C++, excepto los punteros a miembros estáticos, son diferentes de los punteros normales y no tienen las mismas conversiones estándar. Los punteros a miembros estáticos son punteros normales y tienen las mismas conversiones que los punteros normales.   
  
### <a name="null-pointer-conversions"></a>conversiones de puntero nulo  
 Una expresión constante entera que se evalúa como cero, o una conversión de expresión a un tipo de puntero, se convierte a un puntero denominado “puntero null”. Está garantizado que este puntero será diferente de un puntero a cualquier objeto o función válido (a excepción de punteros a objetos basados, que pueden tener el mismo desplazamiento y seguir señalando a objetos diferentes).  
  
 En C ++ 11 la [nullptr](../cpp/nullptr.md) tipo debe ser el preferido para el puntero nulo de estilo C.  
  
### <a name="pointer-expression-conversions"></a>Conversiones de expresiones de puntero  
 Cualquier expresión con un tipo de matriz se puede convertir a un puntero del mismo tipo. El resultado de la conversión es un puntero al primer elemento de matriz. El ejemplo siguiente muestra este tipo de conversión:  
  
```cpp 
char szPath[_MAX_PATH]; // Array of type char.  
char *pszPath = szPath; // Equals &szPath[0].  
```  
  
 Una expresión que da lugar a una función que devuelve un tipo determinado se convierte a un puntero a una función que devuelve ese tipo, excepto cuando:  
  
-   La expresión se utiliza como operando para el operador address-of (**&**).  
  
-   La expresión se utiliza como operando para el operador de llamada a función.  
  
## <a name="reference-conversions"></a>Conversiones de referencia  
 Una referencia a una clase se puede convertir en una referencia a una clase base en los casos siguientes:  
  
-   La clase base especificada es accesible.  
  
-   La conversión no es ambigua. (Consulte [varias clases Base](../cpp/multiple-base-classes.md) para obtener más información acerca de las referencias de clase base ambiguas.)  
  
 El resultado de la conversión es un puntero al subobjeto que representa la clase base.  
  
## <a name="pointer-to-member"></a>Puntero a miembro  
 Los punteros a miembros de clase se pueden convertir durante la asignación, la inicialización, la comparación y otras expresiones. En esta sección se describen las siguientes conversiones de puntero a miembro:  
  
## <a name="pointer-to-base-class-member"></a>Puntero a miembro de clase base  
 Un puntero a un miembro de una clase base se puede convertir en un puntero a un miembro de una clase derivada de esa clase base cuando se cumplen las condiciones siguientes:  
  
-   Se tiene acceso a la conversión inversa, desde el puntero a la clase derivada al puntero de la clase base.  
  
-   La clase derivada no hereda virtualmente de la clase base.  
  
 Cuando el operando izquierdo es un puntero a miembro, el operando derecho debe ser un tipo de puntero a miembro o una expresión constante que se evalúe como 0. Esta asignación solo es válida en los casos siguientes:  
  
-   El operando derecho es un puntero a un miembro de la misma clase que el operando izquierdo.  
  
-   El operando izquierdo es un puntero a un miembro de una clase que se ha derivado de forma pública e inequívoca de la clase del operando derecho.  
  
## <a name="integral-constant-conversions"></a>Conversiones de constantes integrales  
 Una expresión constante entera que se evalúa como cero se convierte a un puntero denominado "puntero null". Está garantizado que este puntero será diferente de un puntero a cualquier objeto o función válido (a excepción de punteros a objetos basados, que pueden tener el mismo desplazamiento y seguir señalando a objetos diferentes).  
  
 El código siguiente muestra la definición de un puntero al miembro `i` en la clase `A`. El puntero, `pai`, se inicializa en 0, que es el puntero null.  
  
```cpp 
class A  
{  
public:  
 int i;  
};  
  
int A::*pai = 0;  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)