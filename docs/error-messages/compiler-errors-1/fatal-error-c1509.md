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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22cb22ea2186b16fd98d2714779b2475c51d15bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1509"></a>Error irrecuperable C1509
límite del compilador: hay demasiados estados de controlador de excepciones en la función 'function'. Simplifique la función  
  
 El código supera el límite interno de Estados de controlador de excepciones (32.768 estados).  
  
 La causa más común es que la función contiene una expresión compleja de operadores aritméticos y variables de clase definidas por el usuario.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Simplifique las expresiones asignando las subexpresiones comunes a variables temporales.  
  
2.  Divida la función en funciones más pequeñas.