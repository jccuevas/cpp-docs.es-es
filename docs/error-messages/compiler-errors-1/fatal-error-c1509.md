---
title: Error irrecuperable C1509 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fec83f6b6138eacc613e560b9da4557079d6677d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198799"
---
# <a name="fatal-error-c1509"></a>Error irrecuperable C1509
límite del compilador: hay demasiados estados de controlador de excepciones en la función 'function'. Simplifique la función  
  
 El código supera el límite interno de Estados de controlador de excepciones (32.768 estados).  
  
 La causa más común es que la función contiene una expresión compleja de operadores aritméticos y variables de clase definidas por el usuario.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Simplifique las expresiones asignando las subexpresiones comunes a variables temporales.  
  
2.  Divida la función en funciones más pequeñas.