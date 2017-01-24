---
title: "IRowsetCreatorImpl::SetSite | Microsoft Docs"
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
  - "IRowsetCreatorImpl.SetSite"
  - "IRowsetCreatorImpl<T>::SetSite"
  - "IRowsetCreatorImpl::SetSite"
  - "SetSite"
  - "ATL.IRowsetCreatorImpl.SetSite"
  - "ATL::IRowsetCreatorImpl<T>::SetSite"
  - "ATL::IRowsetCreatorImpl::SetSite"
  - "ATL.IRowsetCreatorImpl<T>.SetSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetSite (método)"
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetCreatorImpl::SetSite
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el sitio que contiene el objeto de conjunto de filas.  Para obtener más información, vea [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  
  
## Sintaxis  
  
```  
  
      STDMETHOD( SetSite )(  
   IUnknown* pCreator   
);  
```  
  
#### Parámetros  
 `pCreator`  
 \[in\] Puntero al puntero de interfaz de **IUnknown** de sitio que administra el objeto de conjunto de filas.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Además, `IRowsetCreatorImpl::SetSite` habilita las propiedades de OLE DB  **DBPROPCANSCROLLBACKWARDSDBPROPCANFETCHBACKWARDS** .  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetCreatorImpl \(Clase\)](../../data/oledb/irowsetcreatorimpl-class.md)