---
title: "3.1.10 omp_get_nested (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0447fd872a44d2c1eefb751e501eba4df5ec8b8f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested (Función)
El `omp_get_nested` función devuelve un valor distinto de cero si se habilita el paralelismo anidado y 0 si no lo está. Para obtener más información sobre paralelismo anidado, vea la sección 3.1.9 en la página 40. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Si una implementación no implementa paralelismo anidado, esta función siempre devuelve 0.