---
title: Error del compilador C2348
ms.date: 11/04/2016
f1_keywords:
- C2348
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
ms.openlocfilehash: 7bded618c481e59f60c5528510c757dec7226acc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760002"
---
# <a name="compiler-error-c2348"></a>Error del compilador C2348

' nombre de tipo ': no es un agregado de estilo C, no se puede exportar en Embedded-IDL

Para colocar una `struct` en un archivo. idl con el atributo [Export](../../windows/export.md) , el `struct` debe contener solo datos.

En el ejemplo siguiente se genera C2348:

```cpp
// C2348.cpp
// C2348 error expected
[ module(name="SimpleMidlTest") ];

[export]
struct Point {
   // Delete the following two lines to resolve.
   Point() : m_i(0), m_j(0) {}
   Point(int i, int j) : m_i(i), m_j(j) {}

   int m_i;
   int m_j;
};
```
