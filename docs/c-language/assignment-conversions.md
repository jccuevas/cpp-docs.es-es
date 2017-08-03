---
title: "Conversiones de asignación | Microsoft Docs"
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
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 44b9b5ede24d3b6e44813de46e7507f5d943a78f
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="assignment-conversions"></a>Conversiones de asignación
En las operaciones de asignación, el tipo de valor que se va a asignar se convierte al tipo de la variable que recibe la asignación. C permite realizar conversiones por asignación entre tipos enteros y de punto flotante, aunque se pierda información en la conversión. El método de conversión utilizado depende de los tipos usados en la asignación, como se describe en [Conversiones aritméticas usuales](../c-language/usual-arithmetic-conversions.md) y en las siguientes secciones:  
  
-   [Conversiones de tipos enteros con signo](../c-language/conversions-from-signed-integral-types.md)  
  
-   [Conversiones de tipos enteros sin signo](../c-language/conversions-from-unsigned-integral-types.md)  
  
-   [Conversiones de tipos de punto flotante](../c-language/conversions-from-floating-point-types.md)  
  
-   [Conversiones entre tipos de puntero](../c-language/conversions-to-and-from-pointer-types.md)  
  
-   [Conversiones de otros tipos](../c-language/conversions-from-other-types.md)  
  
 Los calificadores de tipo no afectan a la capacidad de realizar una conversión, pero no se puede usar un valor L **const** en el lado izquierdo de la asignación.  
  
## <a name="see-also"></a>Vea también  
 [Conversiones de tipos](../c-language/type-conversions-c.md)
