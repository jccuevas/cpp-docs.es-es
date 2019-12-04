---
title: Error del compilador C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: 3f9dea77b739aa59474e60cf852fff2577ab6ba9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753632"
---
# <a name="compiler-error-c3510"></a>Error del compilador C3510

no se encuentra la biblioteca de tipos dependiente ' type_lib '

se pasaron [no_registry](../../preprocessor/no-registry.md) y [auto_search](../../preprocessor/auto-search.md) a `#import` pero el compilador no pudo encontrar una biblioteca de tipos a la que se hace referencia.

Para resolver este error, asegúrese de que todas las bibliotecas de tipos y bibliotecas de tipos a las que se hace referencia estén disponibles para el compilador.

En el ejemplo siguiente se genera C3510:

Supongamos que se han creado las dos bibliotecas de tipos siguientes y que C3510a. tlb se ha eliminado o no está en la ruta de acceso.

```
// C3510a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C3510aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C3510
   {
      one, two, three
   };
};
```

Y, a continuación, el código fuente de la segunda biblioteca de tipos:

```
// C3510b.idl
// post-build command: del /f C3510a.tlb
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
library C3510bLib
{
   importlib ("C3510a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
   struct S_C3510 {
      enum E_C3510 e;
   };
};
```

Y, a continuación, el código de cliente:

```cpp
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```
