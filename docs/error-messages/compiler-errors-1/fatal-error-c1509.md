---
title: Error irrecuperable C1509 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3d3fc7a7be867a7137dab4155984cf1844b661ea
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1509"></a>Error irrecuperable C1509
límite del compilador: hay demasiados estados de controlador de excepciones en la función 'function'. Simplifique la función  
  
 El código supera el límite interno de Estados de controlador de excepciones (32.768 estados).  
  
 La causa más común es que la función contiene una expresión compleja de operadores aritméticos y variables de clase definidas por el usuario.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones  
  
1.  Simplifique las expresiones asignando las subexpresiones comunes a variables temporales.  
  
2.  Divida la función en funciones más pequeñas.
