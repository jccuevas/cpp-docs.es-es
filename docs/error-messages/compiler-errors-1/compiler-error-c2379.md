---
title: Error del compilador C2379 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec340a5a48705eb91bf5bf72ec20ad382f4b262c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032450"
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