---
title: 'Ejemplo de llamada: Prototipo de función y llamada | Microsoft Docs'
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
ms.openlocfilehash: 9f9ee05b55a0945d18e78dc67df5653c06c8a1bc
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404387"
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
  
 Para obtener más información, consulte [los resultados de ejemplo de llamada](../cpp/results-of-calling-example.md).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)