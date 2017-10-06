---
title: "Conversión de enteros a valores de punto flotante | Microsoft Docs"
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
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 5635ddf0e940e1f374bfd97d7d6f53dc1b57daec
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="casting-integers-to-floating-point-values"></a>Conversión de enteros a valores de punto flotante
**ANSI 3.2.1.3** La dirección de truncamiento cuando un número entero se convierte en un número de punto flotante que no puede representar exactamente el valor original  
  
 Cuando un número entero se convierte en un valor de punto flotante que no puede representar exactamente el valor, el valor se redondea (arriba o abajo) al valor apropiado más próximo.  
  
 Por ejemplo, la conversión de **unsigned long** (con 32 bits de precisión) a **float** (cuya mantisa tiene 23 bits de precisión) redondea el número al múltiplo más próximo de 256. Los valores **long** 4.294.966.913 a 4.294.967.167 se redondean todos al valor **float** 4.294.967.040.  
  
## <a name="see-also"></a>Vea también  
 [Matemáticas de punto flotante](../c-language/floating-point-math.md)
