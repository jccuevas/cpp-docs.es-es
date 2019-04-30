---
title: Error del compilador C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: bd783d9510b1699b33f108a4ce8d8c491028b758
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328710"
---
# <a name="compiler-error-c3387"></a>Error del compilador C3387

'member': __declspec (dllexport) /\__declspec (dllimport) no se puede aplicar a un miembro de una clase administrada o un tipo WinRT

El `dllimport` y [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modificadores no son válidos en los miembros de una clase administrada o tipo en tiempo de ejecución de Windows.

El ejemplo siguiente genera el error C3387 y muestra cómo corregirlo:

```
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```