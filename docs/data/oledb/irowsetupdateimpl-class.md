---
title: "IRowsetUpdateImpl (Clase) | Microsoft Docs"
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
  - "IRowsetUpdateImpl"
  - "ATL.IRowsetUpdateImpl"
  - "ATL::IRowsetUpdateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetUpdateImpl (clase)"
  - "proveedores, actualizables"
  - "proveedores actualizables, actualización aplazada"
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La implementación de las plantillas OLE DB de la interfaz de [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) .  
  
## Sintaxis  
  
```  
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  
class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass  
>  
```  
  
#### Parámetros  
 `T`  
 Una clase derivada de `IRowsetUpdateImpl`.  
  
 `Storage`  
 El registro de usuario.  
  
 `UpdateArray`  
 Matriz que contiene los datos almacenados en caché para actualizar el conjunto de filas.  
  
 `RowClass`  
 La unidad de almacenamiento para **HROW**.  
  
 `MapClass`  
 La unidad de almacenamiento para los identificadores de fila retenidos por el proveedor.  
  
## Miembros  
  
### Métodos de interfaz \(utilizados con IRowsetChange\)  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|Establece valores de datos en una o más columnas.|  
  
### Métodos de interfaz \(utilizados con IRowsetUpdate\)  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|Obtiene los datos transmitidos a u recopilados recientemente del origen de datos, omitiendo los cambios pendientes.|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|Devuelve una lista de filas con cambios pendientes.|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|Devuelve el estado de filas especificadas.|  
|[Undo](../../data/oledb/irowsetupdateimpl-undo.md)|Deshace cualquier cambio en la fila desde la búsqueda o la última actualización.|  
|[Actualizar](../../data/oledb/irowsetupdateimpl-update.md)|Transmite cualquier cambio realizado en la fila desde la búsqueda o la última actualización.|  
  
### Métodos de implementación \(devolución\)  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|Se utiliza para comprobar la seguridad, integridad, etc. antes de permitir actualizaciones.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|Contiene los datos originales para la operación diferida.|  
  
## Comentarios  
 Debería leer y entender la documentación para [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx), porque se aplica todo describe allí también aquí.  También debería leer el capítulo 6 de `OLE``DB``Programmer's``Reference` en datos del valor.  
  
 `IRowsetUpdateImpl` implementa la interfaz OLE DB `IRowsetUpdate` , que permite a los consumidores para retrasar la transmisión de los cambios realizados con `IRowsetChange` al origen de datos y deshacer cambia antes de la transmisión.  
  
> [!IMPORTANT]
>  Se recomienda leer la documentación siguiente BEFORE que intentar implementar el proveedor:  
  
-   [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Chapter 6 de `OLE``DB``Programmer's``Reference`  
  
-   También vea cómo la clase de `RUpdateRowset` se utiliza en el ejemplo UpdatePV  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)