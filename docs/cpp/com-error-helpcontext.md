---
title: "_com_error::HelpContext | Microsoft Docs"
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
  - "_com_error::HelpContext"
  - "HelpContext"
  - "_com_error.HelpContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HelpContext (método)"
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::HelpContext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Llama a la función **IErrorInfo::GetHelpContext**.  
  
## Sintaxis  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## Valor devuelto  
 Devuelve el resultado de **IErrorInfo::GetHelpContext** para el objeto **IErrorInfo** registrado dentro del objeto `_com_error`.  Si no se registra ningún objeto **IErrorInfo**, devuelve cero.  
  
## Comentarios  
 Cualquier error que se produzca mientras se llama al método **IErrorInfo::GetHelpContext** se omite.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)