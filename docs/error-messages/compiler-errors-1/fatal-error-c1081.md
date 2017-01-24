---
title: "Error irrecuperable C1081 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1081"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1081"
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1081
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo': nombre de archivo demasiado largo  
  
 La longitud de un nombre de ruta de acceso a un archivo supera el valor `_MAX_PATH` \(fijado por STDLIB.h en 260 caracteres\).  Reduzca el nombre del archivo.  
  
 Si llama a CL.exe con un nombre de archivo corto, el compilador puede generar un nombre completo con ruta de acceso.  Por ejemplo, `cl -c myfile.cpp` puede hacer que el compilador genere:  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```