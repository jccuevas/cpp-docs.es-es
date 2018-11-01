---
title: Error del compilador C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 7d3b8297c5f5da29b99abe78999396e8c44df0fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667511"
---
# <a name="compiler-error-c2286"></a>Error del compilador C2286

punteros a miembros de la representación 'identificador' ya está establecido en 'herencia': se omite la declaración

Existen dos representaciones diferentes de miembros de puntero para la clase.

Para obtener más información, consulte [palabras clave de herencia](../../cpp/inheritance-keywords.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2286:

```
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```