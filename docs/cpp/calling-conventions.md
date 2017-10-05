---
title: Convenciones de llamada | Documentos de Microsoft
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
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
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
ms.openlocfilehash: bbdee0427dcefc019214e7f9af16831f162cef83
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="calling-conventions"></a>Convenciones de llamada
El compilador de Visual C/C++ proporciona varias convenciones para llamar a funciones internas y externas. Conocer estos distintos enfoques puede ayudarle a depurar el programa y enlazar el código con rutinas de lenguaje de ensamblado.  
  
 Los temas sobre este asunto explican las diferencias entre las convenciones de llamada, cómo se pasan los argumentos y cómo las funciones devuelven valores. También explican las llamadas a función naked, una característica avanzada que permite escribir código de prólogo y epílogo propio.  
  
 Para obtener información sobre convenciones de llamada de x64 procesadores, consulte [la convención de llamada](../build/calling-convention.md).  
  
## <a name="topics-in-this-section"></a>Temas de esta sección  
  
-   [Pasar argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`etc.)  
  
-   [Ejemplo de llamada: Prototipo de función y llamada](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [Uso de llamadas a función naked para escribir código de prólogo/epílogo personalizado](../cpp/naked-function-calls.md)  
  
-   [Coprocesador de punto flotante y convenciones de llamada](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [Convenciones de llamada obsoletas](../cpp/obsolete-calling-conventions.md)  
  
## <a name="see-also"></a>Vea también  
 [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md)
