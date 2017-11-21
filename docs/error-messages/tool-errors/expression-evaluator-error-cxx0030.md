---
title: Error del evaluador de expresiones CXX0030 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0030
dev_langs: C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffa1dd85419943ede6a13d61cb82924c32b5e80a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0030"></a>Error del evaluador de expresiones CXX0030
expresión no evaluable  
  
 Evaluador de expresiones del depurador no pudo obtener un valor para la expresión tal y como se escribe. Una causa probable es que la expresión hace referencia a la memoria que se encuentra fuera del espacio de direcciones del programa (desreferencia un puntero null es un ejemplo). Windows no permite el acceso a la memoria que se encuentra fuera del espacio de direcciones del programa.  
  
 Puede que desee volver a escribir la expresión con paréntesis para controlar el orden de evaluación.  
  
 Este error es idéntico a CAN0030.