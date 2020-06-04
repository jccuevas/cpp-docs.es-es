---
title: Error del compilador C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 3e495a8019405a558511637467133877dae1183e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743528"
---
# <a name="compiler-error-c2480"></a>Error del compilador C2480

' Identifier ': ' Thread ' solo es válido para elementos de datos de extensión estática

No se puede usar el atributo `thread` con una variable automática, un miembro de datos no estático, un parámetro de función o en declaraciones o definiciones de función.

Utilice el atributo `thread` para las variables globales, los miembros de datos estáticos y las variables estáticas locales únicamente.

En el ejemplo siguiente se genera C2480:

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
