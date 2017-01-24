---
title: "_com_error::WCodeToHRESULT | Microsoft Docs"
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
  - "_com_error::WCodeToHRESULT"
  - "_com_error.WCodeToHRESULT"
  - "WCodeToHRESULT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WCodeToHRESULT (método)"
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::WCodeToHRESULT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Asigna un `wCode` de 16 bits a un `HRESULT` de 32 bits.  
  
## Sintaxis  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### Parámetros  
 `wCode`  
 `wCode` de 16 bits que se asignará a `HRESULT` de 32 bits.  
  
## Valor devuelto  
 `HRESULT` de 32 bits asignado desde `wCode` de 16 bits.  
  
## Comentarios  
 Vea la función miembro [WCode](../cpp/com-error-wcode.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error::WCode](../cpp/com-error-wcode.md)   
 [\_com\_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)