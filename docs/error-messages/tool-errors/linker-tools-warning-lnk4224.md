---
title: Las herramientas del vinculador LNK4224 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bdffdf3469cc3a0e5d41b0504b882513d44b63c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703992"
---
# <a name="linker-tools-warning-lnk4224"></a>Advertencia de las herramientas del vinculador LNK4224

> *opción* ya no se admite; se omite

## <a name="remarks"></a>Comentarios

Se especificó una opción del vinculador no válido, obsoleta y se omitió.

Por ejemplo, LNK4224 puede producirse si una directiva/comment aparece en. obj. La directiva/comment se habría agregado a través de la [comentario) (C/C ++)](../../preprocessor/comment-c-cpp.md) pragma, utilizando la opción exestr en desuso. Utilice dumpbin [/ALL](../../build/reference/all.md) para ver las directivas del vinculador en un archivo .obj.

Si es posible, modifique el origen para el archivo .obj y quite el pragma. Si pasar por alto esta advertencia, es posible que un .executable compilado con **/CLR: pure** no se ejecutará como se esperaba. El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

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