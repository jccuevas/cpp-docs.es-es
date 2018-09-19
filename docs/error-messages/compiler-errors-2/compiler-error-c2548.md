---
title: Error del compilador C2548 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2548
dev_langs:
- C++
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4fd5087613466ecb483ad4ec28018c9321453ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050519"
---
# <a name="compiler-error-c2548"></a>Error del compilador C2548

'clase:: miembro': falta el parámetro predeterminado para un parámetro

Falta un parámetro en la lista de parámetros predeterminados. Si se proporciona un parámetro predeterminado en cualquier parte de una lista de parámetros, debe definir los parámetros predeterminados para todos los demás parámetros.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2548:

```
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```