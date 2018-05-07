---
title: Error del evaluador de expresiones CXX0015 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 945dbda4759fa2989acb0411d1a3216a5e9a036c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0015"></a>Error del evaluador de expresiones CXX0015
expresión demasiado compleja (desbordamiento de pila)  
  
 La expresión que ha especificado era demasiado complejo o anidada un nivel demasiado profundo para la cantidad de almacenamiento disponible para el evaluador de expresiones de C.  
  
 Desbordamiento se produce normalmente debido a demasiados cálculos pendientes.  
  
 Reorganice la expresión para que se puede evaluar cada componente de la expresión que se encuentre, en lugar de tener que esperar a otras partes de la expresión que se va a calcular.  
  
 Divida la expresión en varios comandos.  
  
 Este error es idéntico a CAN0015.