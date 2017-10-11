---
title: Valores | Microsoft Docs
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
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 13f497358ae320263fd7043787abb943f760809b
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="values"></a>Valores
**ANSI 3.1.2.5** Las representaciones y conjuntos de valores de distintos tipos de números de punto flotante  
  
 El tipo **float** contiene 32 bits: 1 para el signo, 8 para el exponente y 23 para la mantisa. El intervalo es +/- 3,4E38 con al menos 7 dígitos de precisión.  
  
 El tipo **double** contiene 64 bits: 1 para el signo, 11 para el exponente y 52 para la mantisa. El intervalo es +/- 1,7E308 con al menos 15 dígitos de precisión.  
  
 El tipo **long double** contiene 80 bits: 1 para el signo, 15 para el exponente y 64 para la mantisa. El intervalo es +/- 1,2E4932 con al menos 19 dígitos de precisión. Observe que, con el compilador de Microsoft C, la representación del tipo **long double** es idéntica al tipo **double**.  
  
## <a name="see-also"></a>Vea también  
 [Matemáticas de punto flotante](../c-language/floating-point-math.md)
