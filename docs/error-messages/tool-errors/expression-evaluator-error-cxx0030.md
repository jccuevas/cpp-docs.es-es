---
title: Error del evaluador de expresiones CXX0030 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 669c585c637129c1fb6a480d91b31e5a1264fd22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298121"
---
# <a name="expression-evaluator-error-cxx0030"></a>Error del evaluador de expresiones CXX0030
expresión no evaluable  
  
 Evaluador de expresiones del depurador no pudo obtener un valor para la expresión tal y como se escribe. Una causa probable es que la expresión hace referencia a la memoria que se encuentra fuera del espacio de direcciones del programa (desreferencia un puntero null es un ejemplo). Windows no permite el acceso a la memoria que se encuentra fuera del espacio de direcciones del programa.  
  
 Puede que desee volver a escribir la expresión con paréntesis para controlar el orden de evaluación.  
  
 Este error es idéntico a CAN0030.