---
title: "Error del compilador C2393 | Microsoft Docs"
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
  - "C2393"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2393"
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2393
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo': el símbolo por AppDomain no se puede asignar en el segmento 'segmento'  
  
 El uso de variables [appdomain](../../cpp/appdomain.md) implica que se está compilando con **\/clr:pure** o **\/clr:safe**, y una imagen pura o segura no puede contener segmentos de datos.  
  
 Vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2393.  
  
```  
// C2393.cpp  
// compile with: /clr:pure /c  
#pragma data_seg("myseg")  
int n = 0;   // C2393  
```