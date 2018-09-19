---
title: Advertencia del compilador C4867 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b444156ae87e43b068521a3ad6687abe71df293f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074323"
---
# <a name="compiler-warning-c4867"></a>Advertencia del compilador C4867

'function': Falta lista de argumentos; la llamada a función usar 'llamar' para crear un puntero a miembro

Un puntero a función miembro se inicializó incorrectamente.

Esta advertencia puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: conformidad de puntero a miembro mejorada.  El código compilado antes de Visual C++ 2005 ahora generará C4867.

Esta advertencia siempre se emite como error. Para deshabilitar esta advertencia, use la pragma [warning](../../preprocessor/warning.md) . Para obtener más información sobre C4867 y MFC/ATL, vea [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4867.

```
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```