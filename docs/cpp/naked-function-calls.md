---
title: Llamadas a función naked | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9d7b42f08d68af9838bf908efdbcc59a0540b91
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="naked-function-calls"></a>Llamadas de función naked
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Las funciones declaradas con el `naked` atributo se emiten sin código de prólogo o epílogo, lo cual permite escribir sus propias secuencias de prólogo/epílogo personalizado mediante la [ensamblador alineado](../assembler/inline/inline-assembler.md). Las funciones naked se proporcionan como una característica avanzada. Permiten declarar una función que se está llamando desde un contexto que no es C/C++, y crear así diferentes suposiciones sobre dónde están los parámetros o qué registros se conservan. Entre los posibles ejemplos, se encuentran rutinas tales como los controladores de interrupción. Esta característica es especialmente útil para quienes escriben controladores de dispositivos virtuales (VxD).  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Reglas y limitaciones de las funciones naked](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [Consideraciones para escribir código de prólogo/epílogo](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)