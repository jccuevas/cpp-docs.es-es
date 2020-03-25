---
title: Paso de argumentos y convenciones de nomenclatura
ms.date: 12/17/2018
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
ms.openlocfilehash: e621db339102f1f40030bc7826d383d306a39be8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190773"
---
# <a name="argument-passing-and-naming-conventions"></a>Paso de argumentos y convenciones de nomenclatura

**Específicos de Microsoft**

Los compiladores de Microsoft C++ le permiten especificar convenciones para pasar argumentos y valores devueltos entre funciones y llamadores. No todas las convenciones están disponibles en todas las plataformas compatibles y algunas convenciones utilizan implementaciones específicas de la plataforma. En la mayoría de los casos, se omiten palabras clave o modificadores de compilador que especifican una convención no compatible en una plataforma concreta y se usa la convención predeterminada de la plataforma.

En plataformas x86, todos los argumentos se amplían a 32 bits cuando se pasan. Los valores devueltos también se amplían a 32 bits y se devuelven en el registro EAX, salvo las estructuras de 8 bytes, que se devuelven en el par de registros EDX:EAX. Las estructuras de mayor tamaño se devuelven en el registro EAX como punteros a estructuras de devolución ocultas. Los parámetros se insertan en la pila de derecha a izquierda. Las estructuras distintas de POD no se devolverán en registros.

El compilador genera código de prólogo y epílogo para guardar y restaurar los registros ESI, EDI, EBX y EBP, si se usan en la función.

> [!NOTE]
> Cuando se devuelve un struct, una unión o una clase desde una función por valor, todas las definiciones del tipo deben ser iguales; de lo contrario, se puede producir un error en el programa en tiempo de ejecución.

Para obtener información sobre cómo definir su propio código de prólogo y epílogo de la función, vea [llamadas a funciones Naked](../cpp/naked-function-calls.md).

Para obtener información sobre las convenciones de llamada predeterminadas en el código destinado a plataformas x64, vea [Convención de llamada x64](../build/x64-calling-convention.md). Para obtener información sobre problemas de Convención de llamada en código destinado a plataformas ARM, vea [problemas comunes de migración de ARM C++ visual](../build/common-visual-cpp-arm-migration-issues.md).

El compilador de Visual C/C++ admite las siguientes convenciones de llamada.

|Palabra clave|Limpieza de la pila|Paso de parámetros|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Autor de llamada|Inserta parámetros en la pila, en orden inverso (de derecha a izquierda)|
|[__clrcall](../cpp/clrcall.md)|N/D|Carga parámetros en la pila de expresiones CLR en orden (de izquierda a derecha).|
|[__stdcall](../cpp/stdcall.md)|Destinatario|Inserta parámetros en la pila, en orden inverso (de derecha a izquierda)|
|[__fastcall](../cpp/fastcall.md)|Destinatario|Almacenado en los registros y luego insertado en la pila|
|[__thiscall](../cpp/thiscall.md)|Destinatario|Insertado en la pila; **puntero almacenado** en ECX|
|[__vectorcall](../cpp/vectorcall.md)|Destinatario|Almacenado en registros y luego insertado en la pila en orden inverso (de derecha a izquierda)|

Para obtener información relacionada, vea [convenciones de llamada obsoletas](../cpp/obsolete-calling-conventions.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Convenciones de llamada](../cpp/calling-conventions.md)
