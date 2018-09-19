---
title: Error del compilador C2062 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbda0894b25e09681207d6447bb40727d490fc02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072256"
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