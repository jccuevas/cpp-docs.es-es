---
title: Conversiones de otros tipos | Microsoft Docs
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
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
caps.latest.revision: 9
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e4a0b8b8a377808a18cc106cd2edeef7ecde4abc
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="conversions-from-other-types"></a>Conversiones de otros tipos
Puesto que un valor `enum` es un valor `int` por definición, las conversiones de y a valores `enum` son iguales que las del tipo `int`. Para el compilador de C de Microsoft, un entero es igual que **long**.  
  
 **Específicos de Microsoft**  
  
 No se permite ninguna conversión entre tipos de estructura o unión.  
  
 Cualquier valor se puede convertir al tipo `void`, pero el resultado de dicha conversión solo se puede utilizar en un contexto donde se descarte un valor de expresión, como una instrucción de expresión.  
  
 El tipo `void` no tiene ningún valor, por definición. Por consiguiente, no se puede convertir en ningún otro tipo, y otros tipos no pueden convertirse en `void` por asignación. Sin embargo, se puede convertir explícitamente un valor al tipo `void`, como se describe en [Conversiones de tipos](../c-language/type-cast-conversions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Conversiones de asignación](../c-language/assignment-conversions.md)
