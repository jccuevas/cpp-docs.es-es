---
title: "_com_error::GUID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GUID"
  - "_com_error.GUID"
  - "_com_error::GUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GUID (método)"
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::GUID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Llama a la función **IErrorInfo::GetGUID**.  
  
## Sintaxis  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## Valor devuelto  
 Devuelve el resultado de **IErrorInfo::GetGUID** para el objeto **IErrorInfo** registrado dentro del objeto `_com_error`.  Si no se registra ningún objeto **IErrorInfo**, devuelve `GUID_NULL`.  
  
## Comentarios  
 Cualquier error que se produzca mientras se llama al método **IErrorInfo::GetGUID** se omite.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)