---
title: "ICommandImpl::m_bCancel | Microsoft Docs"
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
  - "ICommandImpl::m_bCancel"
  - "ICommandImpl.m_bCancel"
  - "m_bCancel"
  - "ATL::ICommandImpl::m_bCancel"
  - "ATL.ICommandImpl.m_bCancel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bCancel"
ms.assetid: f3b6fb60-4de4-4d81-a5d2-4052c41be0de
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::m_bCancel
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica si el comando se cancela.  
  
## Sintaxis  
  
```  
  
unsigned m_bCancel:1;  
  
```  
  
## Comentarios  
 Puede recuperar esta variable en el método de **Ejecución** de la clase de comando y cancelar según corresponda.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [ICommandImpl \(Clase\)](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m\_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)