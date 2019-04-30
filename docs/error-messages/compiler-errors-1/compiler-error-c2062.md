---
title: Error del compilador C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: dcfac9629a90b82744f87ec105c30301b2102cdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408750"
---
# <a name="compiler-error-c2062"></a>Error del compilador C2062

tipo 'type' inesperado

El compilador no esperaba un nombre de tipo.

El ejemplo siguiente genera el error C2062:

```
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

Error C2062 también puede producirse debido a la manera en que el compilador controla los tipos indefinidos en la lista de parámetros de constructor. Si el compilador encuentra un tipo indefinido (o mal escrito), se supone que el constructor es una expresión y emite el error C2062. Para resolverlo, utilice sólo tipos definidos en una lista de parámetros de constructor.