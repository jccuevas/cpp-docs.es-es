---
title: Advertencia del compilador (nivel 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 7852340bc056e126238a2d9c7493887ef3caf93e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174497"
---
# <a name="compiler-warning-level-1-c4964"></a>Advertencia del compilador (nivel 1) C4964

No se especificaron opciones de optimización; no se recopilará la información de perfil

Se especificaron [/GL](../../build/reference/gl-whole-program-optimization.md) y [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) , pero no se solicitaron optimizaciones, por lo que no se generarán archivos. PGC y, por lo tanto, no se podrá realizar ninguna optimización guiada por perfiles.

Si desea que se generen archivos. PGC al ejecutar la aplicación, especifique una de las opciones del compilador [/o](../../build/reference/o-options-optimize-code.md) .

En el ejemplo siguiente se genera C4964:

```cpp
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```
