---
title: Advertencia de las herramientas del vinculador LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: eb0a019cc80e5218a52697b8bcd5e91b811d04d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160398"
---
# <a name="linker-tools-warning-lnk4224"></a>Advertencia de las herramientas del vinculador LNK4224

> *opción* ya no se admite; se omite

## <a name="remarks"></a>Comentarios

Se ha especificado una opción del vinculador no válido, obsoleto y se omite.

Por ejemplo, LNK4224 puede producirse si una directiva /comment aparece en. obj. La directiva /comment se habría agregado a través de la [comment (C/C ++)](../../preprocessor/comment-c-cpp.md) pragma, utilizando la opción exestr en desuso. Utilizar dumpbin [/ALL](../../build/reference/all.md) para ver las directivas del vinculador en un archivo .obj.

Si es posible, modifique el origen para el archivo .obj y quite la directiva pragma. Si omite esta advertencia, es posible que un .executable compilado con **/CLR: pure** no se ejecutará según lo previsto. El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```