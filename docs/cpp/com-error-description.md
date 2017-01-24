---
title: "_com_error::Description | Microsoft Docs"
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
  - "_com_error.Description"
  - "_com_error::Description"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Description (método)"
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::Description
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Llama a la función **IErrorInfo::GetDescription**.  
  
## Sintaxis  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## Valor devuelto  
 Devuelve el resultado de **IErrorInfo::GetDescription** para el objeto **IErrorInfo** grabado dentro del objeto `_com_error`.  El `BSTR` resultante se encapsula en un objeto `_bstr_t`.  Si no se registra ningún objeto **IErrorInfo**, devuelve un `_bstr_t` vacío.  
  
## Comentarios  
 Llama a la función **IErrorInfo::GetDescription** y recupera el objeto **IErrorInfo** grabado dentro del objeto `_com_error`.  Cualquier error que se produzca mientras se llama al método **IErrorInfo::GetDescription** se omite.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)