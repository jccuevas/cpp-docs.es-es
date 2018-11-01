---
title: fenv_access
ms.date: 03/12/2018
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: 507e78dd9f9571cc9ce44d7fd91e78b1c955ba73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664040"
---
# <a name="fenvaccess"></a>fenv_access
Deshabilita (**en**) o habilita (**desactivar**) las optimizaciones que pudieran cambiar el entorno de punto flotante marcar las pruebas y los cambios de modo.

## <a name="syntax"></a>Sintaxis

> **#pragma fenv_access (** { **en** | **desactivar** } **)**

## <a name="remarks"></a>Comentarios

De forma predeterminada, **fenv_access** es **desactivar**. Si el compilador puede suponer el código de no tener acceso o manipular el entorno de punto flotante, que puede realizar muchas optimizaciones de código de punto flotante. Establecer **fenv_access** a **en** para informar al compilador que el código tiene acceso a la del entorno de punto flotante para probar las marcas de estado, excepciones, o para establecer las marcas de modo de control. El compilador deshabilita estas optimizaciones para que el código puede acceder al entorno de punto flotante constantemente.

Para obtener más información sobre el comportamiento de punto flotante, vea [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).

Los tipos de optimizaciones que están sujetos a **fenv_access** son:

- Eliminación común global de la subexpresión

- Movimiento de código

- Plegamiento constante

Las directivas pragma de punto flotante incluyen:

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>Ejemplos

Este ejemplo se establece **fenv_access** a **en** para establecer el registro de control de punto flotante de precisión de 24 bits:

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2
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
out=9.999999776482582e-003
```

Si marque como comentario `#pragma fenv_access (on)` respecto al ejemplo anterior, tenga en cuenta que el resultado es diferente porque el compilador realiza la evaluación de tiempo de compilación, que no utiliza el modo de control.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2
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
out=1.000000000000000e-002
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
