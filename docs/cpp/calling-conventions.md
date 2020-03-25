---
title: Convenciones de llamada
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: 432cb1b6910db5ea735288edfbf6aa9e10f0a486
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190292"
---
# <a name="calling-conventions"></a>Convenciones de llamada

El compilador de Visual C/C++ proporciona varias convenciones para llamar a funciones internas y externas. Conocer estos distintos enfoques puede ayudarle a depurar el programa y enlazar el código con rutinas de lenguaje de ensamblado.

Los temas sobre este asunto explican las diferencias entre las convenciones de llamada, cómo se pasan los argumentos y cómo las funciones devuelven valores. También explican las llamadas a función naked, una característica avanzada que permite escribir código de prólogo y epílogo propio.

Para obtener información sobre las convenciones de llamada para procesadores x64, vea [Convención de llamada](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Temas de esta sección

- [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`y otros)

- [Ejemplo de llamada: Prototipo de función y llamada](../cpp/calling-example-function-prototype-and-call.md)

- [Usar llamadas de función Naked para escribir código personalizado de prólogo/epílogo](../cpp/naked-function-calls.md)

- [Coprocesador de punto flotante y convenciones de llamada](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Convenciones de llamada obsoletas](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Consulte también

[Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md)
