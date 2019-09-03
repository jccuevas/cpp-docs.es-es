---
title: float_control (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: aa8cdc07953405175c1753791ab53214d73ba516
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218583"
---
# <a name="float_control-pragma"></a>float_control (Pragma)

Especifica el comportamiento de punto flotante de una función.

## <a name="syntax"></a>Sintaxis

> **#pragma float_control**\
> **#pragma float_control (** { | **STRICT STRICT** | Except} **,** { **on** | **OFF** } [ **, inserciones** ] **)** \
> **#pragma float_control (** { | **Pop pop** } **)**

## <a name="options"></a>Opciones

 | **estricta** | precisión excepto, en OFF, de extracción | \
Especifica el comportamiento de punto flotante, que puede ser **preciso**, **estricto**o **Except**. Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](../build/reference/fp-specify-floating-point-behavior.md). La configuración puede estar **activada** o desactivada.

Cuando es **STRICT**, la configuración de **STRICT** y **Except** se especifica mediante el valor **on** u **OFF** . **salvo** que solo se puede establecer en **on** cuando **precise** o **STRICT** también está establecido en **on**.

Si se agrega el token de **inserción** opcional, la configuración actual de **float_control** se inserta en la pila interna del compilador.

**enviar**\
Inserte el valor de **float_control** actual en la pila interna del compilador

**emergente**\
Quita el valor de **float_control** de la parte superior de la pila interna del compilador y lo convierte en el nuevo valor de **float_control** .

## <a name="remarks"></a>Comentarios

No se puede usar **float_control** para desactivar la **precisión** cuando Except está activada. Del mismo modo, no se puede desactivar la **precisión** cuando [fenv_access](../preprocessor/fenv-access.md) está activada. Para pasar de un modelo estricto a un modelo rápido mediante el pragma **float_control** , use el código siguiente:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

Para pasar del modelo rápido a un modelo estricto con la Directiva pragma **float_control** , use el código siguiente:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

Si no se especifica ninguna opción, **float_control** no tiene ningún efecto.

Las directivas pragma de punto flotante incluyen:

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo detectar una excepción de punto flotante de desbordamiento mediante pragma **float_control**.

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

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
