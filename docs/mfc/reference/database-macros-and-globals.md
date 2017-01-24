---
title: "Macros y variables globales de base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "globales de base de datos [C++]"
  - "macros de base de datos [C++]"
  - "funciones de base de datos globales [C++]"
  - "funciones globales [C++], funciones de base de datos"
  - "macros [C++], base de datos de MFC"
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Macros y variables globales de base de datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las macros y los globals enumerados a continuación se aplican a las aplicaciones de base de datos ODBC\- basadas en.  No se utilizan con aplicaciones DAO\- basadas en.  
  
 Antes de MFC 4,2, las macros `AFX_SQL_ASYNC` y `AFX_SQL_SYNC` dieron a operaciones asincrónicas una oportunidad de producir tiempo a otros procesos.  Empezando por MFC 4,2, la implementación de estas macros modificadas porque las clases ODBC de MFC utilizan sólo operaciones síncronas.  `AFX_ODBC_CALL` macro era nuevo a MFC 4,2.  
  
### Macros de base de datos  
  
|||  
|-|-|  
|[AFX\_ODBC\_CALL](../Topic/AFX_ODBC_CALL.md)|Llama a una función API de ODBC que devuelve `SQL_STILL_EXECUTING`.  `AFX_ODBC_CALL` llama repetidamente la función hasta que devuelva ya no `SQL_STILL_EXECUTING`.|  
|[AFX\_SQL\_ASYNC](../Topic/AFX_SQL_ASYNC.md)|Llama a `AFX_ODBC_CALL`.|  
|[AFX\_SQL\_SYNCHRONIZATION](../Topic/AFX_SQL_SYNC.md)|Llama a una función API de ODBC que no devuelve `SQL_STILL_EXECUTING`.|  
  
### Base de datos Globals  
  
|||  
|-|-|  
|[AfxGetHENV](../Topic/AfxGetHENV.md)|Recupera un identificador al entorno de ODBC en uso actualmente por MFC.  Puede utilizar este identificador en llamadas directas de ODBC.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)