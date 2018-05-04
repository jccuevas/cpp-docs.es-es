---
title: Convenciones de llamada | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9e65dfd7f7cff25debd8eb0d00a7e3bb0397692
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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