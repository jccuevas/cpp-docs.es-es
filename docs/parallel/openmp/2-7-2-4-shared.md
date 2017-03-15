---
title: "2.7.2.4 shared | Microsoft Docs"
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
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.4 shared
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta cláusula comparte las variables que aparecen en la variable\- *lista* entre todos los subprocesos en un equipo.  Todos los subprocesos de un equipo tienen acceso a la misma área de almacenamiento para las variables de **compartido** .  
  
 La sintaxis de la cláusula de **compartido** es la siguiente:  
  
```  
shared(variable-list)  
```