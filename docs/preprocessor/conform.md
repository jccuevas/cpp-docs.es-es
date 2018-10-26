---
title: se ajustan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs:
- C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05b1f9fef458b8c21de9eb3942730ff901d3922e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071237"
---
# <a name="conform"></a>conform
**Específicos de C++**

Especifica el comportamiento de tiempo de ejecución de la [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) opción del compilador.

## <a name="syntax"></a>Sintaxis

> **se ajustan #pragma (** *nombre* [**, mostrar** ] [**,** { **en** | **desactivar** }] [[**,** { **inserción** | **pop** }] [**,** *identificador* ]] **)**

### <a name="parameters"></a>Parámetros

*name*<br/>
Especifica el nombre de la opción del compilador que se va a modificar. El único valor válido *nombre* es `forScope`.

**Show**<br/>
(Opcional) Hace que la configuración actual de *nombre* (true o false) que se mostrará por medio de un mensaje de advertencia durante la compilación. Por ejemplo: `#pragma conform(forScope, show)`.

**en**, **desactivado**<br/>
(Opcional) Establecer *nombre* a **en** permite la [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) opción del compilador. El valor predeterminado es **desactivar**.

**push**<br/>
(Opcional) Inserta el valor actual de *nombre* en la pila interna del compilador. Si especifica *identificador*, puede especificar el **en** o **desactivar** valor *nombre* se inserte en la pila. Por ejemplo: `#pragma conform(forScope, push, myname, on)`.

**pop**<br/>
(Opcional) Establece el valor de *nombre* en el valor en la parte superior de la pila interna del compilador y, a continuación, extrae la pila. Si se especifica el identificador con **pop**, se extrae la pila hasta que encuentra el registro con *identificador*, que también se extrae; el valor actual de *nombre* en el registro siguiente en la pila se convierte en el nuevo valor de *nombre*. Si especifica **pop** con un *identificador* que no está en un registro en la pila, el **pop** se omite.

*identifier*<br/>
(Opcional) Se pueden incluir con un **inserción** o **pop** comando. Si *identificador* sirve, una **en** o **desactivar** también se puede utilizar el especificador.

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

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)