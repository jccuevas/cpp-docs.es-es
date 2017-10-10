---
title: Error irrecuperable C1054 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d02d8eb05633d7250dc3f7ee85dd78ccf4153052
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1054"></a>Error irrecuperable C1054
límite del compilador: los inicializadores están demasiado anidados  
  
 El código supera el límite de anidamiento para inicializadores (de 10 a 15 niveles, dependiendo de la combinación de tipos que se está inicializando).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones  
  
1.  Simplificar los tipos de datos que se va a inicializar para reducir el anidamiento.  
  
2.  Inicialice las variables en instrucciones independientes después de la declaración.
