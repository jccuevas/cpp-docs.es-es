---
title: Error del compilador C3919 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3919
dev_langs:
- C++
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 565146e714e0aa9a3598e4fe5fdeea361454ec78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136119"
---
# <a name="compiler-error-c3919"></a>Error del compilador C3919

'método del evento': función debe tener el tipo 'type'

No se declaró correctamente un método de descriptor de acceso de eventos.

Para obtener más información acerca de los eventos, vea [eventos](../../windows/event-cpp-component-extensions.md).

El ejemplo siguiente genera C3919:

```
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```