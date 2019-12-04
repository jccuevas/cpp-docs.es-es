---
title: Error del compilador C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735975"
---
# <a name="compiler-error-c2062"></a>Error del compilador C2062

tipo ' tipo ' inesperado

El compilador no esperaba un nombre de tipo.

En el ejemplo siguiente se genera C2062:

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 también puede producirse debido a la manera en que el compilador controla los tipos no definidos en la lista de parámetros de un constructor. Si el compilador encuentra un tipo no definido (mal escrito?), se supone que el constructor es una expresión y emite C2062. Para resolverlo, utilice solo tipos definidos en una lista de parámetros de constructor.
