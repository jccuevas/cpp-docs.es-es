---
title: Compilador advertencia (nivel 1) C4772 | Documentos de Microsoft
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4772
dev_langs:
- C++
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbdcfec8d36568c31c291a9de8f9af3aac821fc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4772"></a>Advertencia del compilador (nivel 1) C4772

> \#importación hace referencia a un tipo de una biblioteca de tipos que falta; '*tipo falta*' como un marcador de posición

Se hizo referencia a una biblioteca de tipos con el [#import](../../preprocessor/hash-import-directive-cpp.md) directiva. Sin embargo, la biblioteca de tipos contiene una referencia a otra biblioteca de tipos que no se hace referencia con `#import`. No se encontró este otro archivo TLB por el compilador.

Tenga en cuenta que el compilador no encontrará las bibliotecas de tipos en directorios diferentes si usa el [/I (directorios de inclusión adicionales)](../../build/reference/i-additional-include-directories.md) opción del compilador para especificar esos directorios. Si desea que el compilador para buscar las bibliotecas de tipos en directorios diferentes, agregue esos directorios a la variable de entorno PATH.

De forma predeterminada, esta advertencia se emite como un error. No se puede suprimir la advertencia C4772 con/W0.

## <a name="example"></a>Ejemplo

Se trata de la primera biblioteca de tipos necesaria para reproducir la advertencia C4772.

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

Se trata de la segunda biblioteca de tipos necesaria para reproducir la advertencia C4772.

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

El ejemplo siguiente genera la advertencia C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```