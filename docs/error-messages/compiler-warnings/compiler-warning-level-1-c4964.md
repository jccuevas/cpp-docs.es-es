---
title: Advertencia del compilador (nivel 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 556c6e0963fc41d76cd123373cc4cd85edc66962
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492066"
---
# <a name="compiler-warning-level-1-c4964"></a>Advertencia del compilador (nivel 1) C4964

Se especificó ninguna opción de optimización; no se recopilará la información de perfil

[/ GL](../../build/reference/gl-whole-program-optimization.md) y [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) se han especificado, pero no las optimizaciones se han solicitado, por lo que no se generará ningún archivo .pgc y, por lo tanto, no será posibles optimizaciones guiadas por perfil.

Si desea que los archivos .pgc que se genere cuando ejecute la aplicación, especifique uno de los [/O](../../build/reference/o-options-optimize-code.md) opciones del compilador.

El ejemplo siguiente genera C4964:

```
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```