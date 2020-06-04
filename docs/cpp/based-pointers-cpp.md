---
title: Punteros con base (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: 24c3a7f85c4ea05c38f3ab1d3f637ea0ab24d4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363757"
---
# <a name="based-pointers-c"></a>Punteros con base (C++)

La palabra clave **__based** permite declarar punteros basados en punteros (punteros que son desplazamientos de punteros existentes). La palabra clave **__based** es específica de Microsoft.

## <a name="syntax"></a>Sintaxis

```
type __based( base ) declarator
```

## <a name="remarks"></a>Observaciones

Los punteros basados en direcciones de puntero son la única forma de la palabra clave **__based** válida en compilaciones de 32 bits o 64 bits. Para el compilador de 32 bits de Microsoft C/C++, un puntero basado es un desplazamiento de 32 bits desde una base de puntero de 32 bits. Se aplica una restricción similar a los entornos de 64 bits, donde un puntero basado es un desplazamiento de 64 bits de la base de 64 bits.

Uno de los usos de los punteros basados en punteros son los identificadores persistentes que contienen punteros. Una lista vinculada formada por punteros basados en un puntero se puede guardar en el disco y recargar en otro lugar de la memoria; los punteros seguirán siendo válidos. Por ejemplo:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

Al puntero `vpBuffer` se le asigna la dirección de memoria asignada posteriormente en el programa. La lista vinculada se reubica en relación con el valor de `vpBuffer`.

> [!NOTE]
> Los identificadores persistentes que contienen punteros también se pueden realizar mediante el uso [de archivos asignados a memoria.](/windows/win32/Memory/file-mapping)

Cuando se desreferencia un puntero basado, la base se debe especificar explícitamente o se debe conocer implícitamente con la declaración.

Por compatibilidad con versiones anteriores, **_based** es un sinónimo de **__based** a menos que se especifique la opción del compilador [/Za \(Disable language extensions).](../build/reference/za-ze-disable-language-extensions.md)

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo se cambia un puntero basado mediante el cambio de su base.

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
