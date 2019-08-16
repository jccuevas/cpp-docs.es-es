---
title: Error del compilador C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 1b3256efb6c0ff8236ba80a9ac681780f34fa8dd
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345650"
---
# <a name="compiler-error-c2379"></a>Error del compilador C2379

número de parámetros formales tiene tipo diferente tras promoverlo

El tipo del parámetro especificado no es compatible mediante promociones predeterminadas con el tipo de una declaración anterior. Se trata de un error en ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) y una advertencia con las extensiones de Microsoft (**/Ze**).

El ejemplo siguiente genera C2379:

```
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```