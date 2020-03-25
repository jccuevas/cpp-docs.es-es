---
title: Error de las herramientas del vinculador LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: a2314f160dc6add45547082c7804ec5e2c8f2349
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194868"
---
# <a name="linker-tools-error-lnk1313"></a>Error de las herramientas del vinculador LNK1313

> módulo ijw/native detectado; no se puede vincular con módulos puros

## <a name="remarks"></a>Observaciones

La versión actual de Visual C++ no admite la vinculación de archivos. obj nativos o administrados mixtos o nativos con archivos. obj compilados con **/clr: Pure**.

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

## <a name="example"></a>Ejemplo

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>Ejemplo

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente generará el error LNK1313.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
