---
title: ADVERTENCIA del compilador (nivel 4) C4121
ms.date: 11/04/2016
f1_keywords:
- C4121
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
ms.openlocfilehash: 5bfe2ce5742c250f5f69c59d03888acb155e37a3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991589"
---
# <a name="compiler-warning-level-4-c4121"></a>ADVERTENCIA del compilador (nivel 4) C4121

'symbol': la alineación de un miembro se realizó en función del empaquetado.

El compilador agregó relleno para alinear una estructura de miembro en el límite de empaquetado, pero el valor de empaquetado es menor que el tamaño del miembro. Por ejemplo, en el siguiente fragmento de código se genera C4121:

```cpp
// C4121.cpp
// compile with: /W4 /c
#pragma pack(2)
struct s
{
   char a;
   int b; // C4121
   long long c;
};
```

Para corregir este problema, realice uno de los cambios siguientes:

- Cambie el tamaño de empaquetado al tamaño del miembro que produjo la advertencia o a un tamaño mayor. Por ejemplo, en este fragmento, cambie `pack(2)` a `pack(4)` o `pack(8)`.

- Reordene las declaraciones de miembro por tamaño, de mayor a menor. En el fragmento de código, invierta el orden de los miembros de la estructura de tal manera que el miembro `long long` vaya delante de `int` y que `int` vaya delante de `char`.

Esta advertencia solo se produce cuando el compilador agrega relleno antes que los miembros de datos. No ocurre cuando el empaquetado ha colocado datos en una ubicación de memoria que no está alineada con el tipo de datos pero no se agregó el relleno antes que el miembro de datos. Cuando los datos no están alineados en límites que son múltiplos del tamaño de los datos, el rendimiento puede disminuir. La lectura y escritura de datos no alineados genera errores del procesador en algunas arquitecturas y los errores pueden tardar dos o tres veces más en resolverse. Los accesos a los datos sin alinear no se pueden trasladar a algunas arquitecturas RISC.

Puede usar [#pragma Pack](../../preprocessor/pack.md) o [/ZP](../../build/reference/zp-struct-member-alignment.md) para especificar la alineación de la estructura. (El compilador no genera esta advertencia cuando se especifica **/Zp1** ).
