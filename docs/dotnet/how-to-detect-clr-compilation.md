---
title: 'Filtrar Detectar la compilación de clr:'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 0b02be1bcd0afc9fd857e689ceafdcab5eaf05d1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746518"
---
# <a name="how-to-detect-clr-compilation"></a>Procedimiento Detectar compilación de /clr

Use la `_MANAGED` o `_M_CEE` macro para ver si se compila un módulo con **/CLR**. Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

Para obtener más información acerca de las macros, vea [Predefined Macros](../preprocessor/predefined-macros.md).

## <a name="example"></a>Ejemplo

```
// detect_CLR_compilation.cpp
// compile with: /clr
#include <stdio.h>

int main() {
   #if (_MANAGED == 1) || (_M_CEE == 1)
      printf_s("compiling with /clr\n");
   #else
      printf_s("compiling without /clr\n");
   #endif
}
```

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
