---
title: Compilador advertencia (nivel 1) C4190 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d398331c159c6fc639160dbe54d6ab5f969d3dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063741"
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