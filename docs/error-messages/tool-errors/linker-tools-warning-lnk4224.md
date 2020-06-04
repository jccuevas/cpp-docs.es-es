---
title: Advertencia de las herramientas del vinculador LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: 9e52dd533d897e729aba5f2b43ea6c019a024d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182986"
---
# <a name="linker-tools-warning-lnk4224"></a>Advertencia de las herramientas del vinculador LNK4224

> ya no se admite la *opción* ; tendrán

## <a name="remarks"></a>Observaciones

Se especificó una opción de vinculador no válida, obsoleta y se omitió.

Por ejemplo, LNK4224 puede producirse si aparece una directiva/comment en. obj. La Directiva/comment se habría agregado a través de la pragma [comment (C++C/)](../../preprocessor/comment-c-cpp.md) mediante la opción exestr desusada. Use DUMPBIN [/All](../../build/reference/all.md) para ver las directivas del enlazador en un archivo. obj.

Si es posible, modifique el origen del. obj y quite el pragma. Si omite esta advertencia, es posible que un archivo ejecutable compilado con **/clr: Pure** no se ejecute según lo esperado. La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```
