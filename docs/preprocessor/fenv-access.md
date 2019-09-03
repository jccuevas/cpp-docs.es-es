---
title: fenv_access (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: c8e66881bde12df28bf24e18230471cb4caca792
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218596"
---
# <a name="fenv_access-pragma"></a>fenv_access (Pragma)

Deshabilita (**activado**) o habilita lasoptimizaciones (desactivadas) que podrían cambiar las pruebas de marcas de entorno de punto flotante y los cambios de modo.

## <a name="syntax"></a>Sintaxis

> **#pragma fenv_access (** { **on** | **OFF** } **)**

## <a name="remarks"></a>Comentarios

De forma predeterminada, **fenv_access** es **OFF**. Si el compilador puede suponer que el código no tiene acceso o manipula el entorno de punto flotante, puede realizar muchas optimizaciones del código de punto flotante. Establezca **fenv_access** en **on** para informar al compilador de que el código tiene acceso al entorno de punto flotante para probar marcas de estado, excepciones o establecer marcas de modo de control. El compilador deshabilita estas optimizaciones para que el código pueda tener acceso al entorno de punto flotante de forma coherente.

Para obtener más información sobre el comportamiento de punto flotante, consulte [/FP (especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).

Los tipos de optimizaciones que están sujetos a **fenv_access** son:

- Eliminación común global de la subexpresión

- Movimiento de código

- Plegamiento constante

Las directivas pragma de punto flotante incluyen:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Ejemplos

En este ejemplo se establece **fenv_access** en **on** para establecer el registro de control de punto flotante para la precisión de 24 bits:

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-03
```

Si comenta `#pragma fenv_access (on)` el ejemplo anterior, tenga en cuenta que la salida es diferente porque el compilador realiza la evaluación en tiempo de compilación, que no utiliza el modo de control.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-02
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
