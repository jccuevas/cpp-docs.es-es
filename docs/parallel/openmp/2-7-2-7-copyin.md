---
title: "2.7.2.7 copyin | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.7 copyin
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La cláusula de **copyin** proporciona un mecanismo para asignar el mismo valor a variables de **threadprivate** para cada subproceso del equipo que ejecuta la región paralela.  Para cada variable especificada en una cláusula de **copyin** , el valor de la variable en el subproceso principal del equipo se copia, como si por asignación, las copias de subproceso\-soldado al principio de la región paralela.  La sintaxis de la cláusula de **copyin** es la siguiente:  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 Restricciones de la cláusula de **copyin** son los siguientes:  
  
-   Una variable que se especifica en la cláusula de **copyin** debe tener un operador de asignación accesible, inequívoca de copia.  
  
-   una variable que se especifica en la cláusula de **copyin** debe ser una variable de **threadprivate** .