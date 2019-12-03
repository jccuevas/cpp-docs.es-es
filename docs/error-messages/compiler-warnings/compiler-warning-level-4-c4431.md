---
title: Advertencia del compilador (nivel 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 102e9bdb2804988875d8c535eb8c266bd8fb03df
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683065"
---
# <a name="compiler-warning-level-4-c4431"></a>Advertencia del compilador (nivel 4) C4431

falta el especificador de tipo; se presupone int. Nota: C no admite default-int

Este error se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: visual C++ deja de crear identificadores sin tipo como int de forma predeterminada. El tipo de un identificador se debe especificar explícitamente.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4431.

```c
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```