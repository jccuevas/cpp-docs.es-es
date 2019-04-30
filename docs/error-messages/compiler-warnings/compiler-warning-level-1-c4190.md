---
title: Compilador advertencia (nivel 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386504"
---
# <a name="compiler-warning-level-1-c4190"></a>Compilador advertencia (nivel 1) C4190

'identificador1' tiene una vinculación C especificada, pero devuelve UDT 'identificador2', que es incompatible con C

Una función o un puntero a función tiene un tipo definido por (definido por el usuario, que es una clase, estructura, enum o union) como tipo de valor devuelto y `extern` vinculación "C". Esto es legal si:

- Todas las llamadas a esta función se producen desde C++.

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