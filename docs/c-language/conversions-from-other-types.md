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
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: ed56c0c9ab3186200d3cbb47224dedc60adddb2f
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

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
