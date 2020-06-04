---
title: Advertencia del compilador (nivel 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 89156b2f29fd21160e6abddc3ecb21efaee6dde1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175141"
---
# <a name="compiler-warning-level-1-c4772"></a>Advertencia del compilador (nivel 1) C4772

> \#importación hacía referencia a un tipo de una biblioteca de tipos que faltaba; '*Missing-Type*' se usa como marcador de posición

Se hizo referencia a una biblioteca de tipos con la directiva [#import](../../preprocessor/hash-import-directive-cpp.md) . Sin embargo, la biblioteca de tipos contenía una referencia a otra biblioteca de tipos a la que no se hizo referencia con `#import`. El compilador no encontró este archivo. tlb.

Tenga en cuenta que el compilador no encontrará bibliotecas de tipos en directorios diferentes si usa la opción del compilador [/i (directorios de inclusión adicionales)](../../build/reference/i-additional-include-directories.md) para especificar esos directorios. Si desea que el compilador busque bibliotecas de tipos en directorios diferentes, agregue esos directorios a la variable de entorno PATH.

De forma predeterminada, esta advertencia se emite como un error. C4772 no se puede suprimir con/W0.

## <a name="example"></a>Ejemplo

Esta es la primera biblioteca de tipos necesaria para reproducir C4772.

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

Esta es la segunda biblioteca de tipos necesaria para reproducir C4772.

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

En el ejemplo siguiente se genera C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```
