---
title: Advertencia del compilador (niveles 3 y 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: a12bee4591df8a7a952dc741c4b26c637bb5256c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991071"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Advertencia del compilador (niveles 3 y 4) C4244

'conversion': conversión de 'type1' a 'type2', posible pérdida de datos

Un tipo de entero se convierte en un tipo de entero más pequeño. Se trata de una advertencia de nivel 4 Si *tipo1* es `int` y *tipo2* es menor que `int`. De lo contrario, es de nivel 3 (se le asigna un valor de tipo [__int64](../../cpp/int8-int16-int32-int64.md) a una variable de tipo `unsigned int`). Se ha producido una posible pérdida de datos.

Si recibe el error C4244, debe cambiar el programa para que use tipos compatibles o agregar lógica al código, para asegurarse de que el intervalo de valores posibles sea siempre compatible con los tipos que usa.

C4244 también se puede activar en el nivel 2; vea [Advertencia del compilador (nivel 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) para obtener más información.

Puede que la conversión tenga problemas debido a conversiones implícitas.

El siguiente ejemplo genera C4244:

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

Para obtener más información, vea [conversiones aritméticas habituales](../../c-language/usual-arithmetic-conversions.md).

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

La advertencia C4244 puede producirse al generar código para destinos de 64 bits que no genera la advertencia al compilar destinos de 32 bits. Por ejemplo, una diferencia entre punteros es una cantidad de 32 bits en plataformas de 32 bits, pero una cantidad de 64 bits en plataformas de 64 bits.

En el ejemplo siguiente se genera C4244 cuando se compila para destinos de 64 bits:

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```
