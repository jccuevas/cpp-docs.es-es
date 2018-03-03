---
title: Error del evaluador de expresiones CXX0065 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db01baa10191df50c1f319bf8320263657088d75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0065"></a>Error del evaluador de expresiones CXX0065
variable de marco de pila es necesario  
  
 Una expresión contiene una variable que existe dentro del ámbito actual, pero no se ha creado aún.  
  
 Este error puede producirse cuando se ha ejecutado en el prólogo de una función, pero aún no configurar el marco de pila para la función, o si se ha ejecutado en el código de salida para la función.  
  
 Paso a paso el código de prólogo hasta que se ha configurado el marco de pila antes de evaluar la expresión.  
  
 Este error es idéntico a CAN0065.