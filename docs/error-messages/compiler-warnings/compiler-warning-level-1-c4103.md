---
title: "Advertencia del compilador (nivel 1) C4103 | Microsoft Docs"
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
  - "C4103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4103"
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4103
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre de archivo' : se ha cambiado la alineación después de incluir el encabezado; puede ser que falte \#pragma pack\(pop\)  
  
 El empaquetado afecta al diseño de clases, y normalmente, si el empaquetado cambia de unos archivos de encabezado a otros, puede haber problemas.  
  
 Utilice \#pragma [pack](../../preprocessor/pack.md)\(pop\) antes de salir del archivo de encabezado para solucionar esta advertencia.  
  
 El código siguiente genera el error C4103:  
  
```  
// C4103.h  
#pragma pack(push, 4)  
  
// defintions and declarations  
  
// uncomment the following line to resolve  
// #pragma pack(pop)  
```  
  
 Y, a continuación,  
  
```  
// C4103.cpp  
// compile with: /LD /W1  
#include "c4103.h"   // C4103  
```