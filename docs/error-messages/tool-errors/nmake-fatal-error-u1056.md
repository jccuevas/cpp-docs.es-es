---
title: "Error grave de NMAKE U1056 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1056"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1056"
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error grave de NMAKE U1056
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede encontrar el procesador de comandos  
  
 El procesador de comandos no se encuentra en la ruta de acceso especificada en las variables de entorno **COMSPEC** o **PATH**.  
  
 NMAKE utiliza COMMAND.COM o CMD.EXE como un procesador de comandos cuando ejecuta comandos.  Primero busca el procesador de comandos en la ruta de acceso definida en **COMSPEC**.  Si no existe **COMSPEC**, NMAKE busca los directorios especificados en **PATH**.