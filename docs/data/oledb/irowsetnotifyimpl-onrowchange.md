---
title: "IRowsetNotifyImpl::OnRowChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyImpl::OnRowChange"
  - "IRowsetNotifyImpl.OnRowChange"
  - "OnRowChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnRowChange (método)"
ms.assetid: 148bee03-3707-4bbf-8c51-657efc63645f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# IRowsetNotifyImpl::OnRowChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Notifica al consumidor el primer cambio en una fila o cualquier cambio que afecte a la fila completa.  
  
## Sintaxis  
  
```  
  
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### Parámetros  
 Vea [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) para las descripciones del parámetro.  
  
## Valor devuelto  
 Vea [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) para las descripciones del valor devuelto.  
  
## Comentarios  
 Este método encapsula el método de [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) .  Vea que la descripción del método en la referencia del programador para obtener detalles.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [IRowsetNotifyImpl \(Clase\)](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)