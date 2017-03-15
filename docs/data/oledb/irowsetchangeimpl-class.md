---
title: "IRowsetChangeImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetChangeImpl"
  - "IRowsetChangeImpl"
  - "ATL.IRowsetChangeImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetChangeImpl (clase)"
  - "proveedores, actualizables"
  - "proveedores actualizables, actualización inmediata"
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# IRowsetChangeImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La implementación de las plantillas OLE DB de la interfaz de [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) en la especificación OLE DB.  
  
## Sintaxis  
  
```  
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >   
>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### Parámetros  
 `T`  
 Una clase derivada de `IRowsetChangeImpl`.  
  
 `Storage`  
 El registro de usuario.  
  
 `BaseInterface`  
 La clase base para la interfaz, como `IRowsetChange`.  
  
 `RowClass`  
 La unidad de almacenamiento para el identificador de fila.  
  
 `MapClass`  
 La unidad de almacenamiento para los identificadores de fila retenidos por el proveedor.  
  
## Miembros  
  
### Métodos de interfaz \(utilizados con IRowsetChange\)  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|Elimina filas del conjunto de filas.|  
|[InsertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|Inserta una fila en el conjunto de filas.|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|Establece valores de datos en una o más columnas.|  
  
### Método de implementación \(devolución\)  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|Overidden por el proveedor para confirmar datos al almacén.|  
  
## Comentarios  
 Esta interfaz es responsable de operaciones de escritura inmediatas a un almacén de datos. “Inmediato” significa que cuando el usuario final \(la persona que utiliza al consumidor\) realiza los cambios, esos cambios inmediatamente se transmitidos al almacén de datos \(y no se puede deshacer\).  
  
 `IRowsetChangeImpl` implementa la interfaz OLE DB `IRowsetChange` , que permite actualizar de valores de columnas en las filas existentes, eliminar filas, e insertar nuevas filas.  
  
 La implementación de las plantillas OLE DB admite todos los métodos base \(`SetData`, `InsertRow`, y `DeleteRows`\).  
  
> [!IMPORTANT]
>  Se recomienda leer la documentación siguiente BEFORE que intentar implementar el proveedor:  
  
-   [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Chapter 6 de *OLE DB Programmer's Reference*  
  
-   También vea cómo la clase de `RUpdateRowset` se utiliza en el ejemplo UpdatePV  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)