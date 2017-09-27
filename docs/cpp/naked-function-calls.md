---
title: "Llamadas a función naked | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: dcf93756bf4d10feb63238a1ecf3b6d3f8b340f6
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
