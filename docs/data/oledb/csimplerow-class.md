---
title: "CSimpleRow (Clase) | Microsoft Docs"
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
  - "CSimpleRow"
  - "ATL::CSimpleRow"
  - "ATL.CSimpleRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleRow (clase)"
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleRow (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación predeterminada para el identificador de fila, que se utiliza en la clase de [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) .  
  
## Sintaxis  
  
```  
class CSimpleRow  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddRefRow](../../data/oledb/csimplerow-addrefrow.md)|Agrega un contador de referencias a un identificador de fila existente.|  
|[Comparar](../../data/oledb/csimplerow-compare.md)|Compara dos filas para ver si hacen referencia a la misma instancia de fila.|  
|[CSimpleRow](../../data/oledb/csimplerow-csimplerow.md)|Constructor.|  
|[ReleaseRow](../../data/oledb/csimplerow-releaserow.md)|Libera filas.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_dwRef](../../data/oledb/csimplerow-m-dwref.md)|Recuento de referencias en un identificador de fila existente.|  
|[m\_iRowset](../../data/oledb/csimplerow-m-irowset.md)|Un índice el conjunto de filas que representa el cursor.|  
  
## Comentarios  
 Un identificador de fila es lógicamente etiqueta única para una fila de resultados.  `IRowsetImpl` crea nuevo `CSimpleRow` para cada fila solicitada en [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).  `CSimpleRow` también se puede reemplazar con dispone de la implementación del identificador de fila, porque es un argumento de plantilla predeterminado a `IRowsetImpl`.  El único requisito a reemplazar esta clase es que la clase de reemplazo proporcione un constructor que acepte un solo parámetro de **LONG**escrito.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)