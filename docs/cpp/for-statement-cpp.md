---
title: for (Instrucción) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: e3dfdb45bdf8a508eca9d29e90b3f7c05e7b147d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179919"
---
# <a name="for-statement-c"></a>for (Instrucción) (C++)

Ejecuta una instrucción repetidamente hasta que la condición es false. Para obtener información sobre la instrucción for basada en intervalo, vea [instrucción for basada en intervaloC++()](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Sintaxis

```
for ( init-expression ; cond-expression ; loop-expression )
    statement;
```

## <a name="remarks"></a>Observaciones

Use la instrucción **for** para construir bucles que deben ejecutar un número especificado de veces.

La instrucción **for** consta de tres partes opcionales, tal como se muestra en la tabla siguiente.

### <a name="for-loop-elements"></a>para los elementos de bucle

|Nombre de la sintaxis|Cuándo se ejecuta|Descripción|
|-----------------|-------------------|-----------------|
|`init-expression`|Antes de cualquier otro elemento de la instrucción **for** , `init-expression` se ejecuta solo una vez. El control pasa entonces a `cond-expression`.|Se suele utilizar para inicializar índices de bucle. Puede contener expresiones o declaraciones.|
|`cond-expression`|Antes de la ejecución de cada iteración de `statement`, incluida la primera iteración. `statement` solo se ejecuta si `cond-expression` se evalúa como true (distinto de cero).|Expresión que se evalúa como un tipo entero o un tipo de clase que tiene una conversión no ambigua a un tipo entero. Se utiliza normalmente para comprobar los criterios de finalización del bucle.|
|`loop-expression`|Al final de cada iteración de `statement`. Después de ejecutarse `loop-expression`, se evalúa `cond-expression`.|Se utiliza normalmente para incrementar índices de bucle.|

En los siguientes ejemplos se muestran distintas formas de usar la instrucción **for** .

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

Un bucle **for** finaliza cuando se ejecuta [break](../cpp/break-statement-cpp.md), [Return](../cpp/return-statement-cpp.md)o [goto](../cpp/goto-statement-cpp.md) (en una instrucción con etiqueta fuera del bucle **for** ) dentro de `statement`. Una instrucción [continue](../cpp/continue-statement-cpp.md) en un bucle **for** finaliza solo la iteración actual.

Si se omite `cond-expression`, se considera true y el bucle **for** no finalizará sin una instrucción **break**, **Return**o **goto** dentro de `statement`.

Aunque los tres campos de la instrucción **for** se utilizan normalmente para la inicialización, las pruebas de terminación y el incremento, no se restringen a estos usos. Por ejemplo, el código siguiente imprime los números de 0 a 4. En este caso, `statement` es la instrucción NULL:

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

El C++ estándar indica que una variable declarada en un bucle **for** debe salir del ámbito después de que finalice el bucle **for** . Por ejemplo:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

De forma predeterminada, en [/ze](../build/reference/za-ze-disable-language-extensions.md), una variable declarada en un bucle **for** permanece en el ámbito hasta que finaliza el ámbito de inclusión del bucle **for** .

[/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) permite el comportamiento estándar de las variables declaradas en bucles for sin necesidad de especificar `/Za`.

También es posible usar las diferencias de ámbito del bucle **for** para volver a declarar variables en `/Ze` como se indica a continuación:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Esto simula de forma más estrecha el comportamiento estándar de una variable declarada en un bucle **for** , que requiere que las variables declaradas en un bucle **for** salgan del ámbito una vez terminado el bucle. Cuando una variable se declara en un bucle **for** , el compilador la promueve internamente a una variable local en el ámbito de inclusión del bucle **for** , incluso si ya existe una variable local con el mismo nombre.

## <a name="see-also"></a>Consulte también

[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[while (Instrucción) (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while (Instrucción) (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)
