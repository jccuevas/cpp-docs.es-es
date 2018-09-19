---
title: Las herramientas del vinculador LNK1237 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9ada38fcf3a706f7852f49f60f677fb5dc10d7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065301"
---
# <a name="linker-tools-error-lnk1237"></a>Error de las herramientas del vinculador LNK1237

durante la generación de código, compilador incluyó una referencia al símbolo 'symbol' definido en el módulo 'module' compilado con/GL

Durante la generación de código, el compilador no debe introducir símbolos que se resuelven más adelante en las definiciones de compilado **/GL**. `symbol` es un símbolo que se introdujo y más tarde se resolvió con una definición compilada con **/GL**.

Para obtener más información, consulte [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).

Para resolver LNK1237, no se compilan con el símbolo de **/GL** o use [/INCLUDE (forzar referencias de símbolos)](../../build/reference/include-force-symbol-references.md) para forzar una referencia al símbolo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error LNK1237. Para resolver este error, no inicialice la matriz en LNK1237_a.cpp y agregue **/ include: __chkstk** al comando de vínculo.

```
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```