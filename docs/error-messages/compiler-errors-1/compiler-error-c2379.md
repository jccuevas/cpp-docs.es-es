---
title: Error del compilador C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: f096791a6120023e079b93452a4b35c669db2139
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302112"
---
# <a name="compiler-error-c2379"></a>Error del compilador C2379

el número de parámetro formal tiene un tipo diferente cuando se promueve

El tipo del parámetro especificado no es compatible, a través de promociones predeterminadas, con el tipo en una declaración anterior. Se trata de un error en ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md)) y una advertencia con las extensiones de Microsoft ( **/ze**).

En el ejemplo siguiente se genera C2379:

```c
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```
