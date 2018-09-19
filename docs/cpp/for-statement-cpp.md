---
title: para (instrucción) (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a845fde2010f17d4d92be0d8ed0d4cce0bdb070
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061507"
---
# <a name="for-statement-c"></a>for (Instrucción) (C++)

Ejecuta una instrucción repetidamente hasta que la condición es false. Para obtener información sobre la basada en intervalo para la instrucción, consulte [basada en intervalo para la instrucción (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Sintaxis

```
for ( init-expression ; cond-expression ; loop-expression )
    statement;
```

## <a name="remarks"></a>Comentarios

Use la **para** instrucción para construir bucles que deben ejecutarse un número especificado de veces.

El **para** instrucción consta de tres partes opcionales, como se muestra en la tabla siguiente.

### <a name="for-loop-elements"></a>para los elementos de bucle

|Nombre de la sintaxis|Cuándo se ejecuta|Descripción|
|-----------------|-------------------|-----------------|
|`init-expression`|Antes de cualquier otro elemento de la **para** instrucción `init-expression` se ejecuta solo una vez. El control pasa entonces a `cond-expression`.|Se suele utilizar para inicializar índices de bucle. Puede contener expresiones o declaraciones.|
|`cond-expression`|Antes de la ejecución de cada iteración de `statement`, incluida la primera iteración. `statement` solo se ejecuta si `cond-expression` se evalúa como true (distinto de cero).|Expresión que se evalúa como un tipo entero o un tipo de clase que tiene una conversión no ambigua a un tipo entero. Se utiliza normalmente para comprobar los criterios de finalización del bucle.|
|`loop-expression`|Al final de cada iteración de `statement`. Después de ejecutarse `loop-expression`, se evalúa `cond-expression`.|Se utiliza normalmente para incrementar índices de bucle.|

Los ejemplos siguientes muestran distintas formas de usar el **para** instrucción.

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

Un **para** bucle finaliza cuando un [salto](../cpp/break-statement-cpp.md), [devolver](../cpp/return-statement-cpp.md), o [goto](../cpp/goto-statement-cpp.md) (en una instrucción con etiqueta fuera del **para**bucle) dentro de `statement` se ejecuta. Un [continuar](../cpp/continue-statement-cpp.md) instrucción en un **para** bucle finaliza solo la iteración actual.

Si `cond-expression` es se omite, se considera true y el **para** bucle no finaliza sin una **salto**, **devolver**, o **goto** dentro de `statement`.

Aunque los tres campos de la **para** instrucción normalmente se usan para la inicialización, comprobar la finalización y el incremento, no se limitan a estos usos. Por ejemplo, el código siguiente imprime los números de 0 a 4. En este caso, `statement` es la instrucción NULL:

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

El estándar de C++ indica que una variable declarada en un **para** bucle saldrá del ámbito después de la **para** termina un bucle. Por ejemplo:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

De forma predeterminada, en [/Ze](../build/reference/za-ze-disable-language-extensions.md), una variable declarada en un **para** bucle permanece dentro del ámbito hasta que el **para** finaliza el ámbito de inclusión del bucle.

[/ Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) habilita el comportamiento estándar de las variables declaradas en bucles for sin necesidad de especificar `/Za`.

También es posible usar las diferencias de ámbito el **para** bucle para declarar variables en `/Ze` como sigue:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Esto imita mejor el comportamiento estándar de una variable declarada en un **para** bucle, lo que requiere que las variables declaradas en un **para** bucle salga del ámbito después de realiza el bucle. Cuando se declara una variable en un **para** bucle, el compilador la promueve internamente a una variable local en el **para** de inclusión del bucle ámbito incluso si ya hay una variable local con el mismo nombre.

## <a name="see-also"></a>Vea también

[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[while (Instrucción) (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while (Instrucción) (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)