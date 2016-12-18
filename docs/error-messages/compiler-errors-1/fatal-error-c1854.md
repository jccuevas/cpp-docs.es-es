---
title: "Error irrecuperable C1854 | Microsoft Docs"
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
  - "C1854"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1854"
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1854
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede sobrescribir la información obtenida durante la creación del encabezado precompilado en el archivo objeto: 'nombrearchivo'  
  
 Se ha especificado la opción **\/Yu** \(utilizar encabezado precompilado\) después de haber especificado la opción **\/Yc** \(crear encabezado precompilado\) para ese mismo archivo.  Para ciertas declaraciones \(como las que incluyen `__declspec` `dllexport`\) lo anterior no es válido.