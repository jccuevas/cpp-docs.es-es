---
title: "IRowsetLocateImpl (Clase) | Microsoft Docs"
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
  - "IRowsetLocateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marcadores, OLE DB"
  - "IRowsetLocateImpl (clase)"
  - "proveedores, marcadores"
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetLocateImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la interfaz OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) , que captura filas arbitrarias de un conjunto de filas.  
  
## Sintaxis  
  
```  
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >  
>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
   T,   
   RowsetInterface,   
   RowClass,   
   MapClass  
>  
```  
  
#### Parámetros  
 `T`  
 Una clase derivada de `IRowsetLocateImpl`.  
  
 `RowsetInterface`  
 Una clase derivada de `IRowsetImpl`.  
  
 `RowClass`  
 La unidad de almacenamiento para **HROW**.  
  
 `MapClass`  
 La unidad de almacenamiento para los identificadores de fila retenidos por el proveedor.  
  
 `BookmarkKeyType`  
 El tipo de marcador de posición, como un LONG o una cadena.  Los marcadores normales deben tener una longitud por lo menos de dos bytes. \(la longitud de Solo\- byte se reserva para OLE DB [marcadores estándar](https://msdn.microsoft.com/en-us/library/ms712954.aspx)**DBBMK\_FIRST**, **DBBMK\_LAST**, y **DBBMK\_INVALID**.\)  
  
 `BookmarkType`  
 El mecanismo de asignación para las relaciones de los marcador\-a\- datos que mantienen.  
  
 `BookmarkMapClass`  
 La unidad de almacenamiento para los identificadores de fila retenidos por el marcador.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[Comparar](../../data/oledb/irowsetlocateimpl-compare.md)|Compara dos marcadores.|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|Obtiene las filas que comienzan con la fila especificada por un desplazamiento de un marcador.|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|Obtiene las filas que coinciden con los marcadores especificados.|  
|[Hash](../../data/oledb/irowsetlocateimpl-hash.md)|Devuelve los valores hash para los marcadores especificados.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|Una matriz de marcadores.|  
  
## Comentarios  
 `IRowsetLocateImpl` es la implementación de las plantillas OLE DB de la interfaz de [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) .  `IRowsetLocate` se utiliza para capturar filas arbitrarias de un conjunto de filas.  Un conjunto de filas que no implementa esta interfaz es un conjunto de filas de `sequential` .  Cuando `IRowsetLocate` está presente en un conjunto de filas, la columna 0 es el marcador para las filas; leer esta columna obtendrá un valor de marcador de posición que se puede utilizar para colocar de nuevo a la misma fila.  
  
 `IRowsetLocateImpl` se utiliza para implementar la compatibilidad con marcadores en proveedores.  Los marcadores son marcadores \(índices en un conjunto de filas\) que permite al consumidor para volver rápidamente a una fila, permitiendo acceso a los datos de alta velocidad.  El proveedor determina qué marcadores pueden identificar de forma única una fila.  Mediante los métodos de `IRowsetLocateImpl` , puede comparar los marcadores, capturar filas por el desplazamiento, capturar filas por el marcador de posición, y devolver valores hash para los marcadores.  
  
 Para admitir los marcadores de OLE DB en un conjunto de filas, haga que el conjunto de filas heredan de esta clase.  
  
 Para obtener información sobre cómo implementar la compatibilidad con marcadores, vea [Compatibilidad del proveedor con los marcadores](../../data/oledb/provider-support-for-bookmarks.md) en *Visual C\+\+ Programmer's Guide* y [Marcadores](https://msdn.microsoft.com/en-us/library/ms709728.aspx) en *OLE DB Programmer's Reference* en `Platform``SDK`.  
  
## Requisitos  
 **Encabezado**: atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [Compatibilidad del proveedor con los marcadores](../../data/oledb/provider-support-for-bookmarks.md)   
 [Bookmarks](https://msdn.microsoft.com/en-us/library/ms709728.aspx)