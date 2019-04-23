---
title: Error del compilador C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: c38642d7abd4f2fd50792c548c9a5521b2da10ad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777593"
---
# <a name="compiler-error-c3353"></a>Error del compilador C3353

'delegado': un delegado solo se puede crear desde una función global o una función miembro de un tipo WinRT o administrado

Los delegados, que se declaran con la [delegar](../../extensions/delegate-cpp-component-extensions.md) palabra clave, solo se puede declarar en el ámbito global.

El código siguiente genera el error C3353:

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```