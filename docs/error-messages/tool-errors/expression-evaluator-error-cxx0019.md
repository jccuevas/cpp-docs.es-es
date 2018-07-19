---
title: Error del evaluador de expresiones CXX0019 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52e1679374e105ab06ce245ba68cfe92706689e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302495"
---
# <a name="expression-evaluator-error-cxx0019"></a>Error del evaluador de expresiones CXX0019
conversión de tipo errónea  
  
 El evaluador de expresiones de C no puede realizar la conversión cuando escriben de tipos.  
  
 Este error es idéntico a CAN0019.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El tipo especificado es desconocido.  
  
2.  Se han producido demasiados niveles de tipos de puntero. Por ejemplo, la conversión de tipos  
  
    ```  
    (char **)h_message  
    ```  
  
     no se puede evaluar mediante el evaluador de expresiones de C.