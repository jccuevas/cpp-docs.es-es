---
title: Error de las herramientas del vinculador LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 380df2bff305acc47e423d69ea702d77c4eafdfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160437"
---
# <a name="linker-tools-error-lnk1313"></a>Error de las herramientas del vinculador LNK1313

> módulo ijw/native detectado; no se puede vincular con módulos puros

## <a name="remarks"></a>Comentarios

La versión actual de Visual C++ no admite la vinculación de archivos .obj administrados/nativos nativo o mixto con archivos .obj compilados con **/CLR: pure**.

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

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