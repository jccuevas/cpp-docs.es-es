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
ms.openlocfilehash: 14bc64314cf64e7d13c076c314419e3d636432d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177942"
---
# <a name="naked-function-calls"></a>Llamadas de función naked

**Específicos de Microsoft**

Las funciones declaradas con el atributo **naked** se emiten sin código de prólogo o epílogo, lo que le permite escribir sus propias secuencias de prólogo/epílogo personalizadas mediante el [ensamblador alineado](../assembler/inline/inline-assembler.md). Las funciones naked se proporcionan como una característica avanzada. Permiten declarar una función que se está llamando desde un contexto que no es C/C++, y crear así diferentes suposiciones sobre dónde están los parámetros o qué registros se conservan. Entre los posibles ejemplos, se encuentran rutinas tales como los controladores de interrupción. Esta característica es especialmente útil para quienes escriben controladores de dispositivos virtuales (VxD).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [naked](../cpp/naked-cpp.md)

- [Reglas y limitaciones de las funciones naked](../cpp/rules-and-limitations-for-naked-functions.md)

- [Consideraciones para escribir código de prólogo/epílogo](../cpp/considerations-for-writing-prolog-epilog-code.md)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Convenciones de llamada](../cpp/calling-conventions.md)
