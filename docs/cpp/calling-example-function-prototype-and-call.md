---
title: "Ejemplo de llamada: Prototipo de función y llamada | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: afdc7d91e11936ebfd1775477f8c684ae4ff6d62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="calling-example-function-prototype-and-call"></a>Ejemplo de llamada: Prototipo de función y llamada
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 En el ejemplo siguiente se muestran los resultados de realizar una llamada de función mediante diversas convenciones de llamada.  
  
 Este ejemplo está basado en el esqueleto de función siguiente. Reemplace `calltype` por la convención de llamada adecuada.  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 Para obtener más información, consulte [resultados de ejemplo de llamada](../cpp/results-of-calling-example.md).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)