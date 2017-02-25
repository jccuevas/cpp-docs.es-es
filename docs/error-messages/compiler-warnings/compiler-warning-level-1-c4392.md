---
title: "Advertencia del compilador (nivel 1) C4392 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4392"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4392"
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4392
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'firma' : número incorrecto de argumentos para la función intrínseca, se esperaban 'número' argumentos  
  
 Una declaración de función para una función intrínseca del compilador tiene el número incorrecto de argumentos.  Por ello, la imagen resultante puede no ejecutarse correctamente.  
  
 Para corregir esta advertencia, corrija la declaración o elimínela e incluya \(con \#include\) el archivo de encabezado apropiado.  
  
 El código siguiente genera el error C4392:  
  
```  
// C4392.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_stream_pd(double *dp);   // C4392  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```