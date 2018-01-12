---
title: Error del evaluador de expresiones CXX0015 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0015
dev_langs: C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f671b39fcc0027fdad5308192c5cbd8b8973717
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0015"></a>Error del evaluador de expresiones CXX0015
expresión demasiado compleja (desbordamiento de pila)  
  
 La expresión que ha especificado era demasiado complejo o anidada un nivel demasiado profundo para la cantidad de almacenamiento disponible para el evaluador de expresiones de C.  
  
 Desbordamiento se produce normalmente debido a demasiados cálculos pendientes.  
  
 Reorganice la expresión para que se puede evaluar cada componente de la expresión que se encuentre, en lugar de tener que esperar a otras partes de la expresión que se va a calcular.  
  
 Divida la expresión en varios comandos.  
  
 Este error es idéntico a CAN0015.