---
title: Compilador advertencia (nivel 4) C4431 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4431
dev_langs:
- C++
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b44cd72548f88d922accfd571bd3ce9734b3a409
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034751"
---
# <a name="compiler-warning-level-4-c4431"></a>Advertencia del compilador (nivel 4) C4431

falta el especificador de tipo; se presupone int. Nota: C no admite default-int

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: Visual C++ ya no crea identificadores sin tipo como int de forma predeterminada. El tipo de un identificador debe especificarse explícitamente.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4431.

```
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```