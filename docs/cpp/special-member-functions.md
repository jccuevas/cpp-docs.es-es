---
title: Funciones miembro especiales
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: b15a0e50774bbc4e70912a31f9a57ea0439f2c12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178696"
---
# <a name="special-member-functions"></a>Funciones miembro especiales

Las *funciones miembro especiales* son funciones miembro de clase (o struct) que, en ciertos casos, el compilador genera automáticamente. Estas funciones son el [constructor predeterminado](constructors-cpp.md#default_constructors), el [destructor](destructors-cpp.md), el [constructor de copias y el operador de asignación de copia](copy-constructors-and-copy-assignment-operators-cpp.md), y el [constructor de movimiento y el operador de asignación de movimiento](move-constructors-and-move-assignment-operators-cpp.md). Si la clase no define una o varias funciones miembro especiales, el compilador puede declarar implícitamente y definir las funciones que se usan. Las implementaciones generadas por el compilador se denominan funciones miembro especiales *predeterminadas* . El compilador no genera funciones si no son necesarias.

Puede declarar explícitamente una función miembro especial predeterminada mediante la palabra clave **default =** . Esto hace que el compilador defina la función solo si es necesario, de la misma manera que si la función no se declarara en absoluto.

En algunos casos, el compilador puede generar funciones miembro especiales *eliminadas* , que no están definidas y, por lo tanto, no se pueden llamar. Esto puede ocurrir en los casos en los que una llamada a una función miembro especial determinada en una clase no tiene sentido, dadas otras propiedades de la clase. Para evitar explícitamente la generación automática de una función miembro especial, puede declararla como eliminada mediante la palabra clave **= Delete** .

El compilador genera un *constructor predeterminado*, un constructor que no toma ningún argumento, solo cuando no se ha declarado ningún otro constructor. Si ha declarado solo un constructor que toma parámetros, el código que intenta llamar a un constructor predeterminado hace que el compilador genere un mensaje de error. El constructor predeterminado generado por el compilador realiza una [inicialización predeterminada de modo](initializers.md#default_initialization) miembro simple del objeto. La inicialización predeterminada deja todas las variables de miembro en un estado indeterminado.

El destructor predeterminado realiza la destrucción de los miembros del objeto. Solo es virtual si un destructor de clase base es virtual.

Las operaciones de asignación y construcción de copia y movimiento predeterminadas realizan copias de patrón de bits de modo de miembro o movimientos de miembros de datos no estáticos. Las operaciones de movimiento solo se generan cuando no se declaran las operaciones de desplazamiento o de copia. Un constructor de copias predeterminado solo se genera cuando no se declara ningún constructor de copias. Se elimina implícitamente si se declara una operación de movimiento. Un operador de asignación de copia predeterminado solo se genera cuando no se declara explícitamente ningún operador de asignación de copia. Se elimina implícitamente si se declara una operación de movimiento.

## <a name="see-also"></a>Consulte también

[Referencia del lenguaje C++](cpp-language-reference.md)
