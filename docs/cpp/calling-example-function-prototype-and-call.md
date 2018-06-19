---
title: 'Ejemplo de llamada: Prototipo de función y llamada | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fcfda308ed3a5723b32729e7986a7063e9928fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409376"
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