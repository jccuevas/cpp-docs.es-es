---
title: "_com_error::HRESULTToWCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "HRESULTToWCode"
  - "_com_error.HRESULTToWCode"
  - "_com_error::HRESULTToWCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HRESULTToWCode (método)"
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::HRESULTToWCode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Asigna un `HRESULT` de 32 bits a un `wCode` de 16 bits.  
  
## Sintaxis  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### Parámetros  
 `hr`  
 El `HRESULT` de 32 bits que se asignará al `wCode` de 16 bits.  
  
## Valor devuelto  
 `wCode` de 16 bits asignado desde `HRESULT` de 32 bits.  
  
## Comentarios  
 Vea [\_com\_error::WCode](../cpp/com-error-wcode.md) para obtener más información.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error::WCode](../cpp/com-error-wcode.md)   
 [\_com\_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)