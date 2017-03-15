---
title: "CRowset (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset<TAccessor>"
  - "CRowset"
  - "ATL::CRowset"
  - "ATL::CRowset<TAccessor>"
  - "ATL.CRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRowset (clase)"
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# CRowset (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula un conjunto de filas de OLE DB y las interfaces relacionadas y proporciona los métodos de manipulación para los datos del conjunto de filas.  
  
## Sintaxis  
  
```  
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  El valor predeterminado es `CAccessorBase`.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|Incrementa el recuento de referencias asociado a la fila actual.|  
|[Cerrar](../../data/oledb/crowset-close.md)|Filas de versiones y la interfaz actual de `IRowset` .|  
|[Comparar](../../data/oledb/crowset-compare.md)|Compara dos marcadores mediante [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).|  
|[CRowset](../../data/oledb/crowset-crowset.md)|Crea un nuevo objeto de `CRowset` y \(opcionalmente\) se asocia a una interfaz de **IRowset** proporcionada como parámetro.|  
|[Delete](../../data/oledb/crowset-delete.md)|Elimina filas del conjunto de filas con [IRowsetChange: DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx).|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|Encuentra la fila coincidente siguiente después del marcador especificado.|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|Devuelve la posición aproximada de una fila correspondiente a un marcador.|  
|[GetData](../../data/oledb/crowset-getdata.md)|Recupera los datos desde la copia del conjunto de filas de la fila.|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|Recupera datos del búfer especificado.|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|Recupera los datos obtenidos de o transmitidos recientemente al origen de datos, omitiendo los cambios pendientes.|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|Devuelve el estado de todas las filas.|  
|[Insertar](../../data/oledb/crowset-insert.md)|Crea e inserta una nueva fila con [IRowsetChange: InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx).|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|Compara la fila especificada con la fila actual.|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|Coloca la ubicación de la NeXT\-búsqueda de nuevo a la posición inicial.|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|Se desplaza al último registro.|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|Datos de las búsquedas de fila secuencial siguiente o un número especificado de posiciones más allá de la fila siguiente.|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|Se desplaza al registro anterior.|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|Captura la fila marcada por un marcador o una fila de un desplazamiento especificado del marcador.|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|Captura filas de una posición fraccionarios en el conjunto de filas.|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|Llama a [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) para liberar el identificador de fila actual.|  
|[SetData](../../data/oledb/crowset-setdata.md)|Establece valores de datos en una o más columnas de una fila mediante [IRowsetChange: SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx).|  
|[Undo](../../data/oledb/crowset-undo.md)|Deshace los cambios realizados en una fila desde la última búsqueda o [Actualización](../../data/oledb/crowset-update.md).|  
|[Actualizar](../../data/oledb/crowset-update.md)|Transmite los cambios pendientes realizados en la fila actual desde la búsqueda o la última actualización.|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|Transmite los cambios pendientes realizados en todas las filas desde la búsqueda o la última actualización.|  
  
## Comentarios  
 En OLE DB, un conjunto de filas es el objeto en el que un programa establece y recupera los datos.  
  
 Esta clase no está diseñado para crear instancias pero para pasar suficiente como parámetro de plantilla a `CTable` o a `CCommand` \(`CRowset` es el valor predeterminado\).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Ejemplo de DBViewer](../../top/visual-cpp-samples.md)   
 [Ejemplo MultiRead](../../top/visual-cpp-samples.md)   
 [Ejemplo de atributos MultiRead](../../top/visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)