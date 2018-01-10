---
title: Calcular valores necesarios | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d1e51f1a23a81811bdd4aa6c6feec45748ee572
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="calculating-necessary-values"></a>Calcular valores necesarios
Dos partes esenciales de información deben calcularse por la rutina de la aplicación auxiliar de retraso. Para ello, hay dos funciones inline en delayhlp.cpp para calcular esta información.  
  
-   La primera calcula el índice de la importación actual en las tres tablas diferentes (importar la tabla de direcciones (IAT), tabla de direcciones de importación enlazadas (BIAT) y tabla de direcciones de importación independiente (UIAT)).  
  
-   La segunda cuenta el número de importaciones de una IAT válida.  
  
```  
// utility function for calculating the index of the current import  
// for all the tables (INT, BIAT, UIAT, and IAT).  
__inline unsigned  
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {  
    return pitdCur - pitdBase;  
    }  
  
// utility function for calculating the count of imports given the base  
// of the IAT. NB: this only works on a valid IAT!  
__inline unsigned  
CountOfImports(PCImgThunkData pitdBase) {  
    unsigned        cRet = 0;  
    PCImgThunkData  pitd = pitdBase;  
    while (pitd->u1.Function) {  
        pitd++;  
        cRet++;  
        }  
    return cRet;  
    }  
```  
  
## <a name="see-also"></a>Vea también  
 [Descripción de la función auxiliar](understanding-the-helper-function.md)