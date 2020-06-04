---
title: ADVERTENCIA del compilador (nivel 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199880"
---
# <a name="compiler-warning-level-1-c4190"></a>ADVERTENCIA del compilador (nivel 1) C4190

' identificador1 ' tiene una vinculación C especificada, pero devuelve el UDT ' identificador2 ', que es incompatible con C

Una función o un puntero a la función tiene un UDT (tipo definido por el usuario, que es una clase, estructura, enumeración o unión) como tipo de valor devuelto y `extern` vinculación "C". Esto es válido si:

- Todas las llamadas a esta función se C++producen desde.

- La definición de la función está en C++.

## <a name="example"></a>Ejemplo

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
