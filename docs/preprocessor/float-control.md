---
title: float_control
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 63e27e992778776e186345da07937d1a88844e5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611021"
---
# <a name="floatcontrol"></a>float_control

Especifica el comportamiento de punto flotante de una función.

## <a name="syntax"></a>Sintaxis

> **#pragma float_control** [ **(** [ *valor* **,** *configuración* [ **, inserción** ]] | [ **inserción** | **pop** ] **)** ]

## <a name="options"></a>Opciones

*valor*, *configuración* [, **inserción**]<br/>
Especifica un comportamiento en punto flotante. *valor* puede ser **precisa**, **strict**, o **excepto**. Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md). El *configuración* puede estar **en** o **desactivar**.

Si *valor* es **strict**, la configuración de las opciones **strict** y **excepto** especificados por *configuración* . **excepto** sólo se puede establecer en **en** cuando **precisa** o **strict** también se establece en **en**.

Si el elemento opcional **inserción** token se agrega actual para *valor* se inserta en la pila interna del compilador.

**push**<br/>
Insertar actual **float_control** configuración de sesión en la pila interna del compilador

**pop**<br/>
Quita el **float_control** de la parte superior de la pila interna del compilador y hace que el nuevo **float_control** configuración.

## <a name="remarks"></a>Comentarios

No puede usar **float_control** para activar **precisa** cuando **excepto** está activado. De forma similar, **precisa** no puede desactivarse cuando [fenv_access](../preprocessor/fenv-access.md) está activado. Para pasar del modelo estricto a un modelo rápido mediante el uso de la **float_control** pragma, use el código siguiente:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Para pasar del modelo rápido a un modelo estricto con la **float_control** pragma, use el código siguiente:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Si se especifica ninguna opción, **float_control** no tiene ningún efecto.

Las directivas pragma de punto flotante incluyen:

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo detectar una excepción de punto flotante de desbordamiento mediante la instrucción pragma **float_control**.

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
