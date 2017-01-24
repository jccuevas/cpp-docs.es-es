---
title: "IRowsetIdentityImpl (Clase) | Microsoft Docs"
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
  - "ATL::IRowsetIdentityImpl"
  - "ATL.IRowsetIdentityImpl"
  - "IRowsetIdentityImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetIdentityImpl (clase)"
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetIdentityImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la interfaz OLE DB [IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx) , que habilita la prueba para la identidad de la fila.  
  
## Sintaxis  
  
```  
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
#### Parámetros  
 `T`  
 Una clase derivada de `IRowsetIdentityImpl`.  
  
 `RowClass`  
 La unidad de almacenamiento para **HROW**.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[IsSameRow](../../data/oledb/irowsetidentityimpl-issamerow.md)|Compara dos identificadores de fila para ver si hacen referencia a la misma fila.|  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)