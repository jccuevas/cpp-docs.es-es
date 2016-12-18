---
title: "Error irrecuperable de CVTRES CVT1100 | Microsoft Docs"
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
  - "CVT1100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CVT1100"
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable de CVTRES CVT1100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

recurso duplicado. type:'tipo', name:'nombre', language:'lenguaje', flags:'marcadores', size:'tamaño'  
  
 El recurso dado se ha especificado más de una vez.  
  
 Este error puede aparecer si el vinculador crea una biblioteca de tipos, no ha especificado [\/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) y un recurso del proyecto ya usa 1.  En este caso, especifique \/TLBID e indique otro número, hasta el 65535.