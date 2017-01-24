---
title: "ICommandTextImpl::GetCommandText | Microsoft Docs"
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
  - "GetCommandText"
  - "ICommandTextImpl.GetCommandText"
  - "ICommandTextImpl::GetCommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCommandText (método)"
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandTextImpl::GetCommandText
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el comando de texto establecido por la última llamada a [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).  
  
## Sintaxis  
  
```  
  
      STDMETHOD(GetCommandText)(   
   GUID * pguidDialect,   
   LPOLESTR * ppwszCommand    
);  
```  
  
#### Parámetros  
 Vea [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) en *la referencia del*programador.  El parámetro *de pguidDialect* se omite de forma predeterminada.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [ICommandTextImpl \(Clase\)](../../data/oledb/icommandtextimpl-class.md)