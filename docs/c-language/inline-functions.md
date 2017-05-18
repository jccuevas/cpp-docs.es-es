---
title: Funciones insertadas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
caps.latest.revision: 10
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: cdcf109b76725855aeb6daae1628bbc6a57e6e32
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="inline-functions"></a>Funciones insertadas
**Específicos de Microsoft**  
  
 La palabra clave `__inline` indica al compilador que sustituya el código en la definición de función para cada instancia de una llamada a función. Sin embargo, la sustitución solo se produce a discreción del compilador. Por ejemplo, el compilador no alinea una función si se usa su dirección o si es demasiado grande para alinearla.  
  
 Para que una función se considere candidata para la inserción, debe usar una definición de función nueva.  
  
 Use este formato para especificar una función insertada:  
  
 `__inline` *type*opt*function-definition*`;`  
  
 El uso de funciones insertadas genera código más rápido, e incluso a veces genera código más pequeño que la llamada a función equivalente, por los motivos siguientes:  
  
-   Reduce el tiempo necesario para ejecutar llamadas a función.  
  
-   Las funciones insertadas pequeñas, de quizás tres o menos líneas, generan menos código que la llamada a función equivalente, porque el compilador no genera código para controlar los argumentos y el valor devuelto.  
  
-   Las funciones generadas alineadas están sujetas a optimizaciones de código que no están disponibles para las funciones normales, porque el compilador no realiza optimizaciones entre procedimientos.  
  
 No deben confundirse las funciones que usan `__inline` con el código ensamblador alineado. Vea [Ensamblador en línea](../c-language/inline-assembler-c.md) para obtener más información.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md)


