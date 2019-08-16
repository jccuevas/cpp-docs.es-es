---
title: Advertencia del compilador (nivel 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 6a07a9ffa938d9372ebed9676847b3274115d526
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447024"
---
# <a name="compiler-warning-level-4-c4431"></a>Advertencia del compilador (nivel 4) C4431

falta el especificador de tipo; se presupone int. Nota: C ya no admite default-int

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio 2005: Visual C++ ya no crea identificadores sin tipo como int de forma predeterminada. El tipo de un identificador debe especificarse explícitamente.

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