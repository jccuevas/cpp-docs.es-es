---
title: "Error de las herramientas del vinculador LNK2023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2023"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2023"
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK2023
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

DLL de erróneo o DLL de punto \<de entrada o punto de entrada\>  
  
 El vinculador está cargando una versión incorrecta de msobj90.dll.  Asegúrese de que los archivos link.exe y msobj90.dll en la ruta de acceso son de la misma versión.  
  
 Es posible que falte una dependencia de msobj90.dll.  La lista de dependencias para msobj90.dll es la siguiente:  
  
-   Msvcr90.dll  
  
-   Kernel32.dll  
  
 Busque en el equipo otras copias de msobj90.dll que puedan estar obsoletas.