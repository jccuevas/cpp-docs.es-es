---
title: Conversiones de asignación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 928f80375ecdd33902a0586cf31091d5764ee160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381839"
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