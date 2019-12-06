---
title: Llamadas de función naked
ms.date: 11/04/2016
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
ms.openlocfilehash: 242fe83807c6608a09492d0f1f817e3b6e50e530
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857403"
---
# <a name="naked-function-calls"></a>Llamadas de función naked

**Específicos de Microsoft**

Las funciones declaradas con el atributo **naked** se emiten sin código de prólogo o epílogo, lo que le permite escribir sus propias secuencias de prólogo/epílogo personalizadas mediante el [ensamblador alineado](../assembler/inline/inline-assembler.md). Las funciones naked se proporcionan como una característica avanzada. Permiten declarar una función que se está llamando desde un contexto que no es C/C++, y crear así diferentes suposiciones sobre dónde están los parámetros o qué registros se conservan. Entre los posibles ejemplos, se encuentran rutinas tales como los controladores de interrupción. Esta característica es especialmente útil para quienes escriben controladores de dispositivos virtuales (VxD).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [naked](../cpp/naked-cpp.md)

- [Reglas y limitaciones de las funciones naked](../cpp/rules-and-limitations-for-naked-functions.md)

- [Consideraciones para escribir código de prólogo/epílogo](../cpp/considerations-for-writing-prolog-epilog-code.md)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Convenciones de llamada](../cpp/calling-conventions.md)