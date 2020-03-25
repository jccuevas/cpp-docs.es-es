---
title: Información de tipos en tiempo de ejecución
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
ms.openlocfilehash: 195274d7bcef0ff4d82383a8ec828ca9267573b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178943"
---
# <a name="run-time-type-information"></a>Información de tipos en tiempo de ejecución

La información de tipo en tiempo de ejecución (RTTI) es un mecanismo que permite determinar el tipo de un objeto durante la ejecución del programa. RTTI se agregó al lenguaje C++ porque muchos proveedores de bibliotecas de clases implementaban esta funcionalidad por sí mismos. Esto produjo incompatibilidades entre las bibliotecas. Por tanto, se hizo obvio que se necesitaba compatibilidad para información de tipo en tiempo de ejecución en el nivel de lenguaje.

Por razones de claridad, esta discusión de RTTI se limita casi totalmente a punteros. Sin embargo, los conceptos discutidos también se aplican a referencias.

Hay tres elementos principales del lenguaje C++ para la información en tiempo de ejecución:

- El operador [dynamic_cast](../cpp/dynamic-cast-operator.md) .

   Se usa para la conversión de tipos polimórficos.

- El operador [typeid](../cpp/typeid-operator.md) .

   Se utiliza para identificar el tipo exacto de un objeto.

- La clase [type_info](../cpp/type-info-class.md) .

   Se usa para contener la información de tipo devuelta por el operador **typeid** .

## <a name="see-also"></a>Consulte también

[Conversión](../cpp/casting.md)
