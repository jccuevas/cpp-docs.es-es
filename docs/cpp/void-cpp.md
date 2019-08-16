---
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: cb4be000c3c41862d5b4df766d21ae1cddeb6838
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243996"
---
# <a name="void-c"></a>void (C++)

Cuando se usa como un tipo de valor devuelto de función, el **void** palabra clave especifica que la función no devuelve un valor. Cuando se utiliza para la lista de parámetros de una función, void especifica que la función no toma ningún parámetro. Cuando se utiliza en la declaración de un puntero, void especifica que el puntero es "universal".

Si es de tipo de puntero `void *`, el puntero puede señalar a cualquier variable que no se ha declarado con el **const** o **volátil** palabra clave. Un puntero void no se puede desreferenciar a menos que se convierta en otro tipo. Un puntero void se puede convertir en cualquier otro tipo de puntero de datos.

Un puntero void puede señalar a una función, pero no a un miembro de clase en C++.

No se puede declarar una variable de tipo void.

## <a name="example"></a>Ejemplo

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Tipos fundamentales](../cpp/fundamental-types-cpp.md)