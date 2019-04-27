---
title: Error del compilador C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 90016b65d4ddd58da3fb3c5ab6d81322dc0ef394
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187625"
---
# <a name="compiler-error-c2480"></a>Error del compilador C2480

'identifier': 'thread' solo es válido para elementos de datos de extensión estática

No puede usar el `thread` atributo con una variable automática, el miembro de datos no estáticos, el parámetro de función, o en las definiciones o declaraciones de función.

Use el `thread` atributo para las variables globales, los miembros de datos estáticos y locales variables estáticas.

El ejemplo siguiente genera C2480:

```
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```