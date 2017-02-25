---
title: "IDBCreateCommandImpl::CreateCommand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDBCreateCommandImpl.CreateCommand"
  - "CreateCommand"
  - "IDBCreateCommandImpl::CreateCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateCommand (método)"
ms.assetid: 50ffbf8b-2c07-4bcb-96c5-ffce4519c7f7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IDBCreateCommandImpl::CreateCommand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un nuevo comando y devuelve la interfaz solicitada.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(CreateCommand)(   
   IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand    
);  
```  
  
#### Parámetros  
 Vea [IDBCreateCommand::CreateCommand](https://msdn.microsoft.com/en-us/library/ms709772.aspx) en *la referencia del*programador.  
  
 Algunos parámetros corresponden *a OLE DB parámetros de referencia* de nombres diferentes, que se describen en **IDBCreateCommand::CreateCommand**:  
  
|Parámetros de plantilla OLE DB|*Los parámetros de referencia del programador de OLE DB*|  
|------------------------------------|--------------------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IDBCreateCommandImpl \(Clase\)](../../data/oledb/idbcreatecommandimpl-class.md)