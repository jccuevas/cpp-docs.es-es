---
title: "IRowsetNotifyImpl::OnRowsetChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnRowsetChange"
  - "IRowsetNotifyImpl::OnRowsetChange"
  - "IRowsetNotifyImpl.OnRowsetChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnRowsetChange (método)"
ms.assetid: 5125b0c8-f175-4ee6-befa-8df2c904d5e0
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# IRowsetNotifyImpl::OnRowsetChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Notifica al consumidor cualquier cambio que afecte al conjunto de filas completo.  
  
## Sintaxis  
  
```  
  
   STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### Parámetros  
 Vea [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) para las descripciones del parámetro.  
  
## Valor devuelto  
 Vea [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) para las descripciones del valor devuelto.  
  
## Comentarios  
 Este método encapsula el método de [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) .  Vea que la descripción del método en la referencia del programador para obtener detalles.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [IRowsetNotifyImpl \(Clase\)](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)