---
title: Error del compilador C3209 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3209
dev_langs:
- C++
helpviewer_keywords:
- C3209
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5df31170578c2462c3e437d6eb7f65d6b76af8b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048414"
---
# <a name="compiler-error-c3209"></a>Error del compilador C3209

'class': clase genérica debe ser administrado o WinRTclass

Una clase genérica debe ser una clase administrada o una clase de Windows Runtime.

En el siguiente ejemplo se genera el error C3209 y se muestra cómo corregirlo:

```
// C3209.cpp
// compile with: /clr
generic <class T>
class C {};   // C3209

// OK - ref class can be generic
generic <class T>
ref class D {};
```