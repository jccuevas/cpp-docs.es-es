---
title: Error del evaluador de expresiones CXX0019 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0019
dev_langs: C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 67fbd43280ad6ffcecdf0532819cd80a0d44b479
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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