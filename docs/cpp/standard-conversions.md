---
title: Conversiones estándar
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: c51a5ea5aaabb27babb9e4cd355721742088d31e
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998901"
---
# <a name="standard-conversions"></a>Conversiones estándar

El lenguaje C++ define conversiones entre sus tipos fundamentales. También define conversiones para tipos derivados de puntero, referencia y puntero a miembro. Estas conversiones se denominan *conversiones estándar*.

Esta sección trata las conversiones estándar siguientes:

- Promociones de enteros

- Conversiones de enteros

- Conversiones de punto flotante

- Conversiones de punto flotante y de enteros

- Conversiones aritméticas

- Conversiones de puntero

- Conversiones de referencia

- Conversiones de puntero a miembro

  > [!NOTE]
  > Los tipos definidos por el usuario pueden especificar sus propias conversiones. La conversión de tipos definidos por el usuario se trata en [constructores](../cpp/constructors-cpp.md) y [conversiones](../cpp/user-defined-type-conversions-cpp.md).

El código siguiente provoca conversiones (en este ejemplo, promociones de enteros):

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

El resultado de una conversión solo es un valor L si genera un tipo de referencia. Por ejemplo, una conversión definida por el usuario declarada como `operator int&()` devuelve una referencia y es un valor l. Sin embargo, una conversión declarada como `operator int()` devuelve un objeto y no es un valor l.

## <a name="integral-promotions"></a>Promociones de enteros

Los objetos de un tipo entero se pueden convertir en otro tipo entero más amplio, es decir, un tipo que puede representar un conjunto mayor de valores. Este tipo de ampliación de conversión se denomina *promoción de entero*. Con la promoción de entero, puede usar los siguientes tipos en una expresión siempre que se pueda usar otro tipo entero:

- Objetos, literales y constantes de tipo **Char** y **Short int**

- Tipos de enumeración

- campos de bits **int**

- Enumeradores

C++las promociones son "conserven los valores", ya que se garantiza que el valor después de la promoción sea el mismo que el valor antes de la promoción. En las promociones de preservación de valores, los objetos de tipos enteros más cortos (como campos de bits u objetos de tipo **Char**) se promueven al tipo **int** si **int** pueden representar el intervalo completo del tipo original. Si **int** no puede representar el intervalo completo de valores, el objeto se promueve al tipo **int sin signo**.  Aunque esta estrategia es la misma que la utilizada por el estándar C, las conversiones de preservación de valores no conservan el "signo" del objeto.

Las promociones que poseen la cualidad de conservación de valores y las promociones que conservan el tipo signed/unsigned generan normalmente los mismos resultados. Sin embargo, pueden generar resultados diferentes si el objeto promocionado aparece como:

- Un operando de `/`, `%`, `/=`, `%=`, `<`, `<=`, `>`o `>=`

   Estos operadores dependen del signo para determinar el resultado. Las promociones de conservación de valores y de conservación de la firma producen resultados diferentes cuando se aplican a estos operandos.

- Operando izquierdo de `>>` o `>>=`

   Estos operadores tratan las cantidades con signo y sin signo de manera diferente en una operación de desplazamiento. En el caso de las cantidades con signo, una operación de desplazamiento a la derecha propaga el bit de signo en las posiciones de bits vacantes, mientras que las posiciones de bits vacantes se rellenan con ceros en cantidades sin signo.

- Un argumento para una función sobrecargada, o el operando de un operador sobrecargado, que depende de la firma del tipo de operando para la coincidencia de argumentos. Para obtener más información sobre cómo definir operadores sobrecargados, vea [operadores sobrecargados](../cpp/operator-overloading.md).

## <a name="integral-conversions"></a>Conversiones de enteros

Las *conversiones de enteros* son conversiones entre tipos enteros. Los tipos enteros son **Char**, **Short** (o **Short int**), **int**, **Long**y Long **Long**. Estos tipos se pueden calificar con **signed** o **unsigned**, y **unsigned** se puede usar como abreviatura para **int sin signo**.

### <a name="signed-to-unsigned"></a>De con signo a sin signo

Los objetos de tipos enteros con signo se pueden convertir en los tipos sin signo correspondientes. Cuando se producen estas conversiones, el patrón de bits real no cambia. Sin embargo, la interpretación de los datos cambia. Considere este código:

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

En el ejemplo anterior, un **signo corto**, `i`, se define y se inicializa en un número negativo. La expresión `(u = i)` hace que `i` se convierta en un **Short sin signo** antes de la asignación que se va a `u`.

### <a name="unsigned-to-signed"></a>De con signo a sin signo

Los objetos de tipos enteros sin signo se pueden convertir en los tipos con signo correspondientes. Sin embargo, si el valor sin signo está fuera del intervalo representable del tipo con signo, el resultado no tendrá el valor correcto, tal y como se muestra en el ejemplo siguiente:

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

En el ejemplo anterior, `u` es un objeto entero **corto sin signo** que se debe convertir en una cantidad firmada para evaluar la `(i = u)`de la expresión. Dado que su valor no se puede representar correctamente en un **Short con signo**, los datos se interpretan erróneamente como se muestra.

## <a name="floating-point-conversions"></a>Conversiones de punto flotante

Un objeto de tipo flotante se puede convertir de forma segura en un tipo flotante más preciso; es decir, la conversión no provoca ninguna pérdida de significado. Por ejemplo, las conversiones de **float** a **Double** o de **Double** a **Long Double** son seguras y el valor no cambia.

Un objeto de un tipo flotante también se puede convertir en un tipo menos preciso, si se encuentra en un intervalo representable por ese tipo. (Vea [límites flotantes](../cpp/floating-limits.md) para los intervalos de tipos flotantes). Si el valor original no se puede representar exactamente, se puede convertir al siguiente valor más alto o al siguiente inferior. El resultado es indefinido si no existe tal valor. Considere el ejemplo siguiente:

```cpp
cout << (float)1E300 << endl;
```

El valor máximo que se represente por el tipo **float** es 3, 402823466e E38, un número mucho menor que 1E300. Por lo tanto, el número se convierte en infinito y el resultado es "inf".

## <a name="conversions-between-integral-and-floating-point-types"></a>Conversiones entre tipos integrales y de punto flotante

Algunas expresiones pueden producir la conversión de objetos de tipo flotante a tipos enteros, o viceversa. Cuando un objeto de tipo entero se convierte en un tipo flotante y el valor original no se puede representar exactamente, el resultado es el siguiente valor más alto o el siguiente valor inferior que se puede representar.

Cuando un objeto de tipo flotante se convierte en un tipo entero, se *trunca*la parte fraccionaria o se redondea hacia cero. Un número como 1,3 se convierte en 1 y-1,3 se convierte en-1. Si el valor truncado es mayor que el valor representable más alto o menor que el valor más bajo que se va a representar, el resultado es indefinido.

## <a name="arithmetic-conversions"></a>Conversiones aritméticas

Muchos operadores binarios (descritos en [expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)) producen conversiones de operandos y producen resultados de la misma manera. La conversión de estos operadores se denomina *conversiones aritméticas habituales*. Las conversiones aritméticas de operandos que tienen tipos nativos diferentes se realizan como se muestra en la tabla siguiente. Los tipos typedef se comportan de acuerdo con sus tipos nativos subyacentes.

### <a name="conditions-for-type-conversion"></a>Condiciones para la conversión de tipos

|Condiciones satisfechas|Conversión|
|--------------------|----------------|
|Uno de los operandos es de tipo **Long Double**.|Otro operando se convierte al tipo **Long Double**.|
|La condición anterior no se cumple y cualquiera de los operandos es de tipo **Double**.|Otro operando se convierte al tipo **Double**.|
|No se cumplen las condiciones anteriores y cualquiera de los operandos es de tipo **float**.|Otro operando se convierte al tipo **float**.|
|Las condiciones anteriores no se satisfacen (ninguno de los operandos es de tipo flotante).|Los operandos obtienen promociones enteras de la siguiente manera:<br /><br />-Si alguno de los operandos es de tipo **unsigned Long**, el otro operando se convierte al tipo **unsigned Long**.<br />-Si no se cumple la condición anterior y si alguno de los operandos es de tipo **Long** y el otro de tipo **int sin signo**, ambos operandos se convierten al tipo **Long sin signo**.<br />-Si no se cumplen las dos condiciones anteriores, y si alguno de los operandos es de tipo **Long**, el otro operando se convierte al tipo **Long**.<br />-Si no se cumplen las tres condiciones anteriores, y si alguno de los operandos es de tipo **int sin signo**, el otro operando se convierte al tipo **int sin signo**.<br />-Si no se cumple ninguna de las condiciones anteriores, ambos operandos se convierten al tipo **int**.|

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

La primera instrucción del ejemplo anterior muestra la multiplicación de dos tipos enteros, `iVal` y `ulVal`. La condición que se cumple es que ninguno de los operandos es de tipo flotante y un operando es de tipo **int sin signo**. Por lo tanto, el otro operando, `iVal`, se convierte al tipo **int sin signo**. A continuación, el resultado se asigna a `dVal`. La condición que se cumple aquí es que un operando es de tipo **Double**, por lo que el resultado **int sin signo** de la multiplicación se convierte al tipo **Double**.

La segunda instrucción del ejemplo anterior muestra la adición de un **float** y un tipo entero: `fVal` y `ulVal`. La variable `ulVal` se convierte al tipo **float** (tercera condición de la tabla). El resultado de la suma se convierte al tipo **Double** (segunda condición de la tabla) y se asigna a `dVal`.

## <a name="pointer-conversions"></a>Conversiones de puntero

Los punteros se pueden convertir durante la asignación, inicialización, comparación y en otras expresiones.

### <a name="pointer-to-classes"></a>De puntero a clases

Hay dos casos en los que un puntero a una clase se puede convertir en un puntero a una clase base.

El primer caso es cuando la clase base especificada es accesible y la conversión es inequívoca. Para obtener más información sobre las referencias de clase base ambiguas, vea [varias clases base](../cpp/multiple-base-classes.md).

Si una clase base es accesible depende del tipo de herencia utilizada en la derivación. Considere la herencia que se muestra en la siguiente ilustración.

![Gráfico de herencia que&#45;muestra]el gráfico de herencia de accesibilidad de clase base(../cpp/media/vc38xa1.gif "que muestra la accesibilidad de la clase base&#45;") <br/>
Gráfico de herencia para ilustrar la accesibilidad de clase base

En la tabla siguiente se muestra la accesibilidad de la clase base para la situación que se muestra en la ilustración.

|Tipo de función|Derivación|Conversión de<br /><br /> B * a una\* legal?|
|----------------------|----------------|-------------------------------------------|
|Función externa (no de ámbito de clase)|Private|No|
||Protegido|No|
||Público|Sí|
|Función miembro B (en ámbito B)|Private|Sí|
||Protegido|Sí|
||Público|Sí|
|Función miembro C (en ámbito C)|Private|No|
||Protegido|Sí|
||Público|Sí|

El segundo caso en el que un puntero a una clase se puede convertir a un puntero a una clase base es cuando se utiliza una conversión de tipos explícita. Para obtener más información sobre las conversiones de tipos explícitas, vea [operador de conversión explícita de tipos](explicit-type-conversion-operator-parens.md).

El resultado de esta conversión es un puntero al *subobjeto*, la parte del objeto que describe completamente la clase base.

En el código siguiente se definen dos clases, `A` y `B`, donde `B` se deriva de `A`. (Para obtener más información sobre la herencia, vea [clases derivadas](../cpp/inheritance-cpp.md)). A continuación, define `bObject`, un objeto de tipo `B`y dos punteros (`pA` y `pB`) que apuntan al objeto.

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

El puntero `pA` es de tipo `A *`, los que se puede interpretar como “puntero a un objeto de tipo `A`”. Los miembros de `bObject` (como `BComponent` y `BMemberFunc`) son únicos para el tipo `B` y, por tanto, son inaccesibles a través de `pA`. El puntero `pA` solo permite el acceso a esas características (funciones de miembro y datos) del objeto que se definen en la clase `A`.

### <a name="pointer-to-function"></a>De puntero a función

Un puntero a una función se puede convertir al tipo `void *`, si el tipo `void *` es lo suficientemente grande como para contener ese puntero.

### <a name="pointer-to-void"></a>De puntero a void

Los punteros al tipo **void** se pueden convertir en punteros a cualquier otro tipo, pero solo con una conversión de tipo explícita (a diferencia de C). Un puntero a cualquier tipo se puede convertir implícitamente en un puntero al tipo **void**. Un puntero a un objeto incompleto de un tipo se puede convertir en un puntero a **void** (implícitamente) y viceversa (explícitamente). El resultado de dicha conversión es igual al valor del puntero original. Un objeto se considera incompleto si se declara, pero no hay suficiente información disponible para determinar su tamaño o clase base.

Un puntero a cualquier objeto que no sea **const** o **volatile** se puede convertir implícitamente en un puntero de tipo `void *`.

### <a name="const-and-volatile-pointers"></a>punteros const y volatile

C++no proporciona una conversión estándar de un tipo **const** o **volatile** a un tipo que no es **const** o **volatile**. Sin embargo, se puede especificar cualquier tipo de conversión mediante conversiones de tipos explícitas (incluidas las conversiones que no son seguras).

> [!NOTE]
> C++los punteros a miembros, excepto los punteros a miembros estáticos, son diferentes de los punteros normales y no tienen las mismas conversiones estándar. Los punteros a miembros estáticos son punteros normales y tienen las mismas conversiones que los punteros normales.

### <a name="null-pointer-conversions"></a>conversiones de puntero nulo

Una expresión constante entera que se evalúa como cero, o tal conversión de expresión a un tipo de puntero, se convierte en un puntero denominado *puntero nulo*. Este puntero siempre compara distinto a un puntero a cualquier objeto o función válidos. Una excepción son los punteros a objetos basados en, que pueden tener el mismo desplazamiento y seguir señalando a objetos diferentes.

En C++ 11, el tipo [nullptr](../cpp/nullptr.md) debe ser preferible al puntero nulo de estilo C.

### <a name="pointer-expression-conversions"></a>Conversiones de expresiones de puntero

Cualquier expresión con un tipo de matriz se puede convertir a un puntero del mismo tipo. El resultado de la conversión es un puntero al primer elemento de matriz. El ejemplo siguiente muestra este tipo de conversión:

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

Una expresión que da lugar a una función que devuelve un tipo determinado se convierte a un puntero a una función que devuelve ese tipo, excepto cuando:

- La expresión se utiliza como operando para el operador Address-of ( **&** ).

- La expresión se utiliza como operando para el operador de llamada a función.

## <a name="reference-conversions"></a>Conversiones de referencia

Una referencia a una clase se puede convertir en una referencia a una clase base en estos casos:

- La clase base especificada es accesible.

- La conversión no es ambigua. (Para obtener más información sobre las referencias de clase base ambiguas, vea [varias clases base](../cpp/multiple-base-classes.md)).

El resultado de la conversión es un puntero al subobjeto que representa la clase base.

## <a name="pointer-to-member"></a>Puntero a miembro

Los punteros a miembros de clase se pueden convertir durante la asignación, la inicialización, la comparación y otras expresiones. En esta sección se describen las siguientes conversiones de puntero a miembro:

### <a name="pointer-to-base-class-member"></a>Puntero a miembro de clase base

Un puntero a un miembro de una clase base se puede convertir en un puntero a un miembro de una clase derivada de esa clase base cuando se cumplen las condiciones siguientes:

- Se tiene acceso a la conversión inversa, desde el puntero a la clase derivada al puntero de la clase base.

- La clase derivada no hereda virtualmente de la clase base.

Cuando el operando izquierdo es un puntero a miembro, el operando derecho debe ser un tipo de puntero a miembro o una expresión constante que se evalúe como 0. Esta asignación solo es válida en los casos siguientes:

- El operando derecho es un puntero a un miembro de la misma clase que el operando izquierdo.

- El operando izquierdo es un puntero a un miembro de una clase que se ha derivado de forma pública e inequívoca de la clase del operando derecho.

### <a name="null-pointer-to-member-conversions"></a>punteros NULL a las conversiones de miembros

Una expresión constante entera que se evalúa como cero se convierte en un puntero nulo. Este puntero siempre compara distinto a un puntero a cualquier objeto o función válidos. Una excepción son los punteros a objetos basados en, que pueden tener el mismo desplazamiento y seguir señalando a objetos diferentes.

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

[C++Referencia del lenguaje](../cpp/cpp-language-reference.md)