---
title: __thiscall
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: b9edc2cd8caa5fd5458f6a53c5fdb1f8a5e69914
ms.sourcegitcommit: 5bb421fdf61d290cac93a03e16a6a80959accf6d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83854819"
---
# `__thiscall`

La Convención de llamada **específica de Microsoft** **`__thiscall`** se usa en las funciones miembro de clase de C++ en la arquitectura x86. Es la Convención de llamada predeterminada utilizada por las funciones miembro que no usan argumentos variables ( `vararg` funciones).

En **`__thiscall`** , el destinatario limpia la pila, lo que es imposible para `vararg` las funciones. Los argumentos se insertan en la pila de derecha a izquierda. El **`this`** puntero se pasa a través de la ECx de registro y no en la pila.

En las máquinas ARM, ARM64 y x64, **`__thiscall`** el compilador acepta y omite. Esto se debe a que usa de forma predeterminada una Convención de llamada basada en registros.

Una razón para usar **`__thiscall`** es en las clases cuyas funciones miembro usan **`__clrcall`** de forma predeterminada. En ese caso, puede usar para hacer que se pueda **`__thiscall`** llamar a funciones de miembro individuales desde código nativo.

Al compilar con [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) , todas las funciones y los punteros a función son **`__clrcall`** a menos que se especifique lo contrario. Las **`/clr:pure`** **`/clr:safe`** Opciones del compilador y están en desuso en visual Studio 2015 y no se admiten en visual Studio 2017.

`vararg`las funciones miembro usan la **`__cdecl`** Convención de llamada. Todos los argumentos de función se insertan en la pila, y el **`this`** puntero se coloca en la pila en último lugar.

Dado que esta Convención de llamada solo se aplica a C++, no tiene un esquema de decoración de nombres de C.

Al definir una función miembro de clase no estática fuera de línea, especifique el modificador de Convención de llamada solo en la declaración. No tiene que volver a especificarla en la definición fuera de línea. El compilador usa la Convención de llamada especificada durante la declaración en el punto de definición.

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)
