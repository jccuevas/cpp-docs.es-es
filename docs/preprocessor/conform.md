---
title: conform (Pragma)
ms.date: 08/29/2019
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 816ff85bb19f549c6ea072073bd89fcd503545f2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220502"
---
# <a name="conform-pragma"></a>conform (Pragma)

**C++Cuestión**

Especifica el comportamiento en tiempo de ejecución de la opción del compilador [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) .

## <a name="syntax"></a>Sintaxis

> **conformidad #pragma (** *nombre* [ **, Mostrar** ] [ **,** { **on** | **OFF** }] [[ **,** { **inserte** | **pop** }] [ **,** *identificador* [ **,** { **on** **OFF}** ]  |  ] ] **)**

### <a name="parameters"></a>Parámetros

*Name*\
Especifica el nombre de la opción del compilador que se va a modificar. El único *nombre* válido es `forScope`.

**Feria**\
Opta Hace que el valor actual de *Name* (true o false) se muestre por medio de un mensaje de advertencia durante la compilación. Por ejemplo, `#pragma conform(forScope, show)`.

**activado**, desactivado\
Opta Establecer el *nombre* en **on** habilita la opción del compilador [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) . El valor predeterminado es **OFF**.

**enviar**\
Opta Envía el valor actual de *Name* en la pila interna del compilador. Si especifica *Identifier*, puede especificar el valor **on** u **OFF** del *nombre* que se va a insertar en la pila. Por ejemplo, `#pragma conform(forScope, push, myname, on)`.

**emergente**\
Opta Establece el valor de *Name* en el valor de la parte superior de la pila interna del compilador y, a continuación, extrae la pila. Si el identificador se especifica con **pop**, la pila se volverá a extraer hasta que encuentre el registro con el *identificador*, que también se extraerá; el valor actual de *Name* en el siguiente registro de la pila se convierte en el nuevo valor de *Name*. Si especifica **pop** con un *identificador* que no está en un registro de la pila, se omite el **pop** .

*identificador*\
Opta Se puede incluir con un comando de **extracción** o de **pop** . Si se usa *Identifier* , también se puede usar un especificador **on** u **OFF** .

## <a name="example"></a>Ejemplo

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
