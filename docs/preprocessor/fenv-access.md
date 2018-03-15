---
title: fenv_access | Microsoft Docs
ms.custom: 
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e19b4b3f1fd71d61609648f587dee9aac31e6f6
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="fenvaccess"></a>fenv_access

Deshabilita (**en**) o habilita (**desactivar*) las optimizaciones que podrían cambiar el entorno de punto flotante marca pruebas y los cambios de modo.

## <a name="syntax"></a>Sintaxis

> **#pragma fenv_access (** { **en** | **desactivar** } **)**  

## <a name="remarks"></a>Comentarios

De forma predeterminada, **fenv_access** es **desactivar**. Si el compilador puede suponer el código no tener acceso o manipular el entorno de punto flotante, entonces pueden realizar muchas de las optimizaciones de código de punto flotante. Establecer **fenv_access** a **en** para informar al compilador que el código tiene acceso el entorno de punto flotante para probar los indicadores de estado, excepciones, o para establecer marcadores de modo de control. El compilador deshabilita estas optimizaciones para que el código pueda acceder el entorno de punto flotante de forma coherente. 

Para obtener más información sobre el comportamiento de punto flotante, consulte [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md).

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

Si marca como comentario `#pragma fenv_access (on)` del ejemplo anterior, observe que el resultado es diferente porque el compilador realiza la evaluación en tiempo de compilación, que no utiliza el modo de control.

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
