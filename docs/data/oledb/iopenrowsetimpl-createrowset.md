---
title: "IOpenRowsetImpl::CreateRowset | Microsoft Docs"
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
  - "IOpenRowsetImpl.CreateRowset"
  - "IOpenRowsetImpl::CreateRowset"
  - "CreateRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRowset (método)"
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOpenRowsetImpl::CreateRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un objeto de conjunto de filas.  No denominado directamente por el usuario.  Vea [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en *la referencia del programador.*  
  
## Sintaxis  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### Parámetros  
 `RowsetClass`  
 Un miembro de la clase de plantilla que representa la clase de conjunto de filas del usuario.  Generado normalmente por el asistente.  
  
 `pRowsetObj`  
 \[out\] Un puntero a un objeto de conjunto de filas.  Este parámetro no se utiliza normalmente, pero se puede utilizar si debe realizar más trabajo en el conjunto de filas antes de pasarla a un objeto COM.  La duración de `pRowsetObj` está enlazado por `ppRowset`.  
  
 Para otros parámetros, vea [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en *la referencia del programador.*  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IOpenRowsetImpl \(Clase\)](../../data/oledb/iopenrowsetimpl-class.md)