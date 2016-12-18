---
title: "IRowsetImpl (Clase) | Microsoft Docs"
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
  - "IRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetImpl (clase)"
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz `IRowset`.  
  
## Sintaxis  
  
```  
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*   
   >  
>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### Parámetros  
 `T`  
 La clase, derivada de `IRowsetImpl`.  
  
 `RowsetInterface`  
 Una clase derivada de `IRowsetImpl`.  
  
 `RowClass`  
 Unidad de almacenamiento para **HROW**.  
  
 `MapClass`  
 Unidad de almacenamiento para los identificadores de fila retenidos por el proveedor.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|Agrega un contador de referencias a un identificador de fila existente.|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|Llamado por [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) para asignar nuevo **HROW**.  No denominado directamente por el usuario.|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|Recupera los datos desde la copia del conjunto de filas de la fila.|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|Devuelve el estado del campo especificado.|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|Obtiene las filas de forma secuencial, recordando la posición anterior.|  
|[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)|Constructor.  No denominado directamente por el usuario.|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|Llamado por [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md).  No denominado directamente por el usuario.|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|Libera filas.|  
|[RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|Coloca la búsqueda de nuevo siguiente colocar a su posición inicial; es decir, su posición cuando se creó el conjunto de filas primero.|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|Establece los indicadores de estado para el campo especificado.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|Indica si un proveedor admite obtención hacia atrás.|  
|[m\_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|Indica si un proveedor puede hacer que el cursor desplácese hacia atrás.|  
|[m\_bReset](../../data/oledb/irowsetimpl-m-breset.md)|Indica si un proveedor ha restablecido la posición del cursor.  Esto tiene un significado especial al desplazarse hacia atrás o capturar hacia atrás en [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|  
|[m\_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|Un índice el conjunto de filas, que representa el cursor.|  
|[m\_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|Una lista de identificadores de fila.|  
  
## Comentarios  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) es la interfaz base de conjunto de filas.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)