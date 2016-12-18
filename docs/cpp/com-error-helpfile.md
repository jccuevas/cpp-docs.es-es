---
title: "_com_error::HelpFile | Microsoft Docs"
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
  - "HelpFile"
  - "_com_error::HelpFile"
  - "_com_error.HelpFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HelpFile (método)"
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::HelpFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Llama a la función **IErrorInfo::GetHelpFile**.  
  
## Sintaxis  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## Valor devuelto  
 Devuelve el resultado de **IErrorInfo::GetHelpFile** para el objeto **IErrorInfo** registrado dentro del objeto `_com_error`.  El BSTR resultante se encapsula en un objeto `_bstr_t`.  Si no se registra ningún objeto **IErrorInfo**, devuelve un `_bstr_t` vacío.  
  
## Comentarios  
 Cualquier error que se produzca mientras se llama al método **IErrorInfo::GetHelpFile** se omite.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)