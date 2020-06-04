---
title: fenv_access (pragma)
description: Describe el uso y los efectos de la Directiva pragma fenv_access. La Directiva fenv_access controla el acceso al entorno de punto flotante en tiempo de ejecución.
ms.date: 11/19/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: e03eb404f2805a4f7c96509600c063c1b1acf629
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305858"
---
# <a name="fenv_access-pragma"></a>fenv_access (pragma)

Deshabilita (**activado**) o habilita las optimizaciones (**desactivadas**) que podrían cambiar las pruebas de marcas de entorno de punto flotante y los cambios de modo.

## <a name="syntax"></a>Sintaxis

> **#pragma fenv_access (** { **on** | **OFF** } **)**

## <a name="remarks"></a>Comentarios

De forma predeterminada, **fenv_access** está **desactivado**. El compilador supone que el código no tiene acceso ni manipula el entorno de punto flotante. Si el acceso al entorno no es necesario, el compilador puede hacer más para optimizar el código de punto flotante.

Habilite **fenv_access** si el código comprueba las marcas de estado de punto flotante, las excepciones o los conjuntos de modos de control. El compilador deshabilita las optimizaciones de punto flotante, por lo que el código puede tener acceso al entorno de punto flotante de forma coherente.

La opción de línea de comandos [/FP: STRICT] habilita automáticamente **fenv_access**. Para obtener más información sobre este y otros comportamientos de punto flotante, consulte [/FP (especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).

Existen restricciones en cuanto a cómo se puede utilizar el pragma **fenv_access** en combinación con otros valores de punto flotante:

- No se puede habilitar **fenv_access** a menos que se habilite la semántica precisa. La semántica precisa se puede habilitar mediante el [float_control](float-control.md) pragma o mediante las opciones de compilador [/FP: precise](../build/reference/fp-specify-floating-point-behavior.md) o [/FP: STRICT](../build/reference/fp-specify-floating-point-behavior.md) . El compilador tiene como valor predeterminado **/FP: precise** si no se especifica ninguna otra opción de línea de comandos de punto flotante.

- No se puede usar **float_control** para deshabilitar la semántica precisa cuando se establece **fenv_access (ON)** .

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

Si comenta `#pragma fenv_access (on)` del ejemplo anterior, el resultado es diferente. Se debe a que el compilador realiza la evaluación en tiempo de compilación, que no utiliza el modo de control.

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
