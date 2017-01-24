---
title: "_com_error::Error | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error.Error"
  - "_com_error::Error"
  - "Error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Error (método)"
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::Error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Recupera el `HRESULT` pasado al constructor.  
  
## Sintaxis  
  
```  
  
HRESULT Error( ) const throw( );  
  
```  
  
## Valor devuelto  
 Elemento `HRESULT` sin formato pasado en el constructor.  
  
## Comentarios  
 Recupera el elemento `HRESULT` encapsulado de un objeto `_com_error`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)