---
title: Compilador advertencia (nivel 4) C4232 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 450c764cfc130acf28e3edfb40fcd17c8ac3b664
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118291"
---
# <a name="compiler-warning-level-4-c4232"></a>Advertencia del compilador (nivel 4) C4232

ha utilizado una extensión no estándar: 'identifier': la dirección de dllimport 'dllimport' no es estática, no garantiza la identidad

Con las extensiones de Microsoft (/Ze), puede indicar un valor no estático como la dirección de una función declarada con el **dllimport** modificador. La compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), esto produce un error.

El ejemplo siguiente genera C4232:

```
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```