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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94087d5e07765b1052404a4c3e51f37db2a31e3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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