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
ms.openlocfilehash: 2de019f908942a58b232877fcd9eebc4689d8e22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187484"
---
# <a name="void-c"></a>void (C++)

Cuando se usa como un tipo de valor devuelto de función, la palabra clave **void** especifica que la función no devuelve un valor. Cuando se usa para la lista de parámetros de una función, **void** especifica que la función no toma ningún parámetro. Cuando se usa en la declaración de un puntero, **void** especifica que el puntero es "universal".

Si el tipo de un puntero es **void\*** , el puntero puede apuntar a cualquier variable que no esté declarada con la palabra clave **const** o **volatile** . No se puede desreferenciar un puntero **void\*** a menos que se convierta en otro tipo. Un puntero **void\*** se puede convertir en cualquier otro tipo de puntero de datos.

Un puntero **void** puede apuntar a una función, pero no a un miembro de C++clase en.

No se puede declarar una variable de tipo **void**.

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

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Tipos integrados](../cpp/fundamental-types-cpp.md)
