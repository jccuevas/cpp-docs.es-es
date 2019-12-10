---
title: Error de las herramientas del vinculador LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: c56b2eb86c7605fb3330d7b1bb01e3235466ede6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990963"
---
# <a name="linker-tools-error-lnk1237"></a>Error de las herramientas del vinculador LNK1237

durante la generación de código, el compilador presentó una referencia al símbolo ' Symbol ' definido en el módulo ' module ' compilado con/GL

Durante la generación de código, el compilador no debe introducir símbolos que posteriormente se resuelvan en las definiciones **/GL**compilada. `symbol` es un símbolo que se presentó y se resolvió posteriormente en una definición compilada con **/GL**.

Para obtener más información, consulte [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).

Para resolver LNK1237, no compile el símbolo con **/GL** o use [/include (forzar referencias de símbolos)](../../build/reference/include-force-symbol-references.md) para forzar una referencia al símbolo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK1237. Para resolver este error, no inicialice la matriz en LNK1237_a. cpp y agregue **/include: __chkstk** al comando Link.

```cpp
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```cpp
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```
