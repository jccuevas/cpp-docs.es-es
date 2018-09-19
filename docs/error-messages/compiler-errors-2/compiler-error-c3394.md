---
title: Error del compilador C3394 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3394
dev_langs:
- C++
helpviewer_keywords:
- C3394
ms.assetid: 4e025d79-27ba-43c8-b0d9-839ecef98126
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7a7f66d437158504b3ca4c8dccaf3c35d2c1ae4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096423"
---
# <a name="compiler-error-c3394"></a>Error del compilador C3394

error de sintaxis en la cláusula de restricciones: el 'identifier' encontrado esperaba un tipo

Había una restricción mal formada.  Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3394:

```
// C3394.cpp
// compile with: /clr /c
ref class MyClass {};
ref class R {
   generic<typename T>
   where T : static   // C3394
   // try the following line instead
   // where T : MyClass
   void f() {}
};
```