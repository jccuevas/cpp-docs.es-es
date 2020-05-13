---
title: for (Instrucción) (C++)
description: Referencia a la instrucción Standard C++ para en Microsoft Visual Studio C++.
f1_keywords:
- for_cpp
ms.date: 04/14/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: 92f7ae4b1f2fbaaf710cd5a8739b78cb98a0accb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375382"
---
# <a name="for-statement-c"></a>for (Instrucción) (C++)

Ejecuta una instrucción repetidamente hasta que la condición es false. Para obtener información sobre la instrucción para la instrucción basada en rangos, vea [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Sintaxis

> **`for (`***init-expression* **`;`** *cond-expression* **`;`** *loop-expression***`)`**\
> &nbsp;&nbsp;&nbsp;&nbsp;_Declaración_**`;`**

## <a name="remarks"></a>Observaciones

Utilice la instrucción **for** para construir bucles que deben ejecutar un número especificado de veces.

La instrucción **for** consta de tres partes opcionales, como se muestra en la tabla siguiente.

### <a name="for-loop-elements"></a>para los elementos de bucle

|Nombre de la sintaxis|Cuándo se ejecuta|Descripción|
|-----------------|-------------------|-----------------|
|`init-expression`|Antes de cualquier otro elemento `init-expression` de la instrucción **for,** se ejecuta una sola vez. El control pasa entonces a `cond-expression`.|Se suele utilizar para inicializar índices de bucle. Puede contener expresiones o declaraciones.|
|`cond-expression`|Antes de la ejecución de cada iteración de `statement`, incluida la primera iteración. `statement` solo se ejecuta si `cond-expression` se evalúa como true (distinto de cero).|Expresión que se evalúa como un tipo entero o un tipo de clase que tiene una conversión no ambigua a un tipo entero. Se utiliza normalmente para comprobar los criterios de finalización del bucle.|
|`loop-expression`|Al final de cada iteración de `statement`. Después de ejecutarse `loop-expression`, se evalúa `cond-expression`.|Se utiliza normalmente para incrementar índices de bucle.|

En los ejemplos siguientes se muestran diferentes formas de usar la instrucción **for.**

```cpp
#include <iostream>
using namespace std;

int main() {
    // The counter variable can be declared in the init-expression.
    for (int i = 0; i < 2; i++ ){
       cout << i;
    }
    // Output: 01
    // The counter variable can be declared outside the for loop.
    int i;
    for (i = 0; i < 2; i++){
        cout << i;
    }
    // Output: 01
    // These for loops are the equivalent of a while loop.
    i = 0;
    while (i < 2){
        cout << i++;
    }
}
    // Output: 012
```

`init-expression` y `loop-expression` pueden contener varias instrucciones separadas por comas. Por ejemplo:

```cpp
#include <iostream>
using namespace std;

int main(){
    int i, j;
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {
        cout << "i + j = " << (i + j) << '\n';
    }
}
    // Output:
    i + j = 15
    i + j = 17
    i + j = 19
```

`loop-expression` se puede aumentar o reducir, o modificar de otras maneras.

```cpp
#include <iostream>
using namespace std;

int main(){
for (int i = 10; i > 0; i--) {
        cout << i << ' ';
    }
    // Output: 10 9 8 7 6 5 4 3 2 1
    for (int i = 10; i < 20; i = i+2) {
        cout << i << ' ';
    }
    // Output: 10 12 14 16 18
```

Un bucle **for** finaliza cuando `statement` se ejecuta un [break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md)o [goto](../cpp/goto-statement-cpp.md) (a una instrucción etiquetada fuera del bucle **for).** Una instrucción [continue](../cpp/continue-statement-cpp.md) en un bucle **for** finaliza solo la iteración actual.

Si `cond-expression` se omite, se `true`considera , y el bucle **for** no terminará sin `statement`un **break**, **return**o **goto** dentro de .

Aunque los tres campos de la instrucción **for** se usan normalmente para la inicialización, las pruebas de terminación e incremento, no están restringidos a estos usos. Por ejemplo, el código siguiente imprime los números de 0 a 4. En este caso, `statement` es la instrucción NULL:

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i;
    for( i = 0; i < 5; cout << i << '\n', i++){
        ;
    }
}
```

## <a name="for-loops-and-the-c-standard"></a>Bucles for y el estándar de C++

El estándar C++ indica que una variable declarada en un bucle **for** saldrá del ámbito después de que finalice el bucle **for.** Por ejemplo:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

De forma predeterminada, en [/Ze](../build/reference/za-ze-disable-language-extensions.md), una variable declarada en un bucle **for** permanece en el ámbito hasta que finaliza el ámbito envolvente del bucle **for.**

[/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) habilita el comportamiento estándar de las variables `/Za`declaradas en bucles for sin necesidad de especificar .

También es posible utilizar las diferencias de ámbito del bucle **for** `/Ze` para volver a declarar las variables de la siguiente manera:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Este comportamiento imita más de cerca el comportamiento estándar de una variable declarada en un bucle **for,** que requiere que las variables declaradas en un bucle **for** salgan del ámbito una vez finalizado el bucle. Cuando una variable se declara en un bucle **for,** el compilador la promueve internamente a una variable local en el ámbito envolvente del bucle **for.** Se promueve incluso si ya hay una variable local con el mismo nombre.

## <a name="see-also"></a>Consulte también

[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[mientras que la declaración (C++)](../cpp/while-statement-cpp.md)<br/>
[Do-while (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)
