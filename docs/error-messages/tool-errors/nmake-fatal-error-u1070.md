---
title: Error grave de NMAKE U1070 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1070
dev_langs: C++
helpviewer_keywords: U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5adf5321c96341cfce633a2329a52360be8a45da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1070"></a>Error grave de NMAKE U1070
desplazarse en la definición de macro 'nombredemacro'  
  
 La definición de macro dada contiene una macro cuya definición contiene la macro dada. Las definiciones de macro circulares no son válidas.  
  
## <a name="example"></a>Ejemplo  
 Las siguientes definiciones de macro  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 Provoca el error siguiente:  
  
```  
cycle in macro definition 'TWO'  
```