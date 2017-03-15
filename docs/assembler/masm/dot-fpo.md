---
title: ".FPO | Microsoft Docs"
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
  - ".FPO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".FPO directive"
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .FPO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de .FPO controla la emisión de los registros de depuración al segmento o a la sección de .debug$F.  
  
## Sintaxis  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### Parámetros  
 `cdwLocals`  
 número de variables locales, un valor de bit sin signo 32.  
  
 `cdwParams`  
 Tamaño de los parámetros en DWORD, un valor de bit sin signo 16.  
  
 *cbProlog*  
 Número de bytes del código de prólogo de función, un valor de bit sin signo 8.  
  
 `cbRegs`  
 Registros de número guardados.  
  
 `fUseBP`  
 Indica si se ha asignado el registro EBP.  0 o 1.  
  
 *cbFrame*  
 Indica el tipo de fotograma.  Para obtener más información, consulte [FPO\_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)