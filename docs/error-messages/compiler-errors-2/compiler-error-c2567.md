---
title: Error del compilador C2567 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2567
dev_langs:
- C++
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1bbdc535f75230da05a92eb0498176da40e918ea
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2567"></a>Error del compilador C2567
no se puede abrir los metadatos de 'archivo', archivo que se han eliminado o movido  
  
 Un archivo de metadatos que se hace referencia en el origen (con `#using`) no se encontró en el mismo directorio por el proceso de back-end del compilador tal como estaba por el proceso de front-end del compilador. Vea [#using (directiva)](../../preprocessor/hash-using-directive-cpp.md) para obtener más información.  
  
 Se podría producir el error C2567 si se compila con **/c** en uno, del equipo y, a continuación, intente una generación de código en tiempo de vínculo en otro equipo. Para obtener más información, consulte [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md)).  
  
 También puede indicar que el equipo no quedaba memoria.  
  
 Para corregir este error, asegúrese de que el archivo de metadatos está en la misma ubicación del directorio para todas las fases del proceso de compilación.
