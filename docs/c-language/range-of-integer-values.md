---
title: Intervalo de valores enteros | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
caps.latest.revision: 6
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: ac6e1783714c0aef62acecad24d345225a65e67e
ms.lasthandoff: 04/01/2017

---
# <a name="range-of-integer-values"></a>Intervalo de valores enteros
**ANSI 3.1.2.5** Las representaciones y los conjuntos de valores de los distintos tipos de enteros  
  
 Los enteros contienen 32 bits (cuatro bytes). Los enteros con signo se representan en forma de complemento de dos. El bit más significativo contiene el signo: 1 si es negativo y 0 si es positivo o cero. Los valores se muestran a continuación:  
  
|Tipo|Mínimo y máximo|  
|----------|-------------------------|  
|**unsigned short**|De 0 a 65535|  
|`signed short`|De -32768 a 32767|  
|`unsigned long`|De 0 a 4294967295|  
|**signed long**|De -2147483648 a 2147483647|  
  
## <a name="see-also"></a>Vea también  
 [Enteros](../c-language/integers.md)
