---
title: CRowset (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>
- CRowset
- ATL::CRowset
- ATL::CRowset<TAccessor>
- ATL.CRowset
dev_langs:
- C++
helpviewer_keywords:
- CRowset class
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef4ec2851365d9fbabab6819a0883b6a9b660f28
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crowset-class"></a>CRowset (Clase)
Encapsula un objeto de conjunto de filas de OLE DB y varios relacionados con interfaces y proporciona métodos de manipulación de datos de conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso. De manera predeterminada, es `CAccessorBase`.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|Incrementa el recuento de referencias asociado a la fila actual.|  
|[Cerrar](../../data/oledb/crowset-close.md)|Libera filas y la actual `IRowset` interfaz.|  
|[Compare](../../data/oledb/crowset-compare.md)|Compara dos marcadores usando [IRowsetLocate:: Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).|  
|[CRowset](../../data/oledb/crowset-crowset.md)|Crea un nuevo `CRowset` objeto y (opcionalmente) lo asocia a un **IRowset** interfaz proporcionada como un parámetro.|  
|[Eliminar](../../data/oledb/crowset-delete.md)|Elimina las filas desde el conjunto de filas mediante [IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx).|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|Busca la siguiente fila coincidente después del marcador especificado.|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|Devuelve la posición aproximada de una fila que corresponda a un marcador.|  
|[GetData](../../data/oledb/crowset-getdata.md)|Recupera datos de la copia del conjunto de filas de la fila.|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|Recupera los datos desde el búfer especificado.|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|Recupera los datos que se captura más recientemente o transmitida al origen de datos, pasando por alto los cambios pendientes.|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|Devuelve el estado de todas las filas.|  
|[Insertar](../../data/oledb/crowset-insert.md)|Crea e inserta una nueva fila utilizando [IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx).|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|Compara la fila especificada con la fila actual.|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|Cambia de posición de la ubicación de búsqueda siguiente a la posición inicial.|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|Se desplaza hasta el último registro.|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|Captura los datos de la siguiente fila secuencial o un número especificado de posiciones más allá de la fila siguiente.|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|Se desplaza al registro anterior.|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|Obtiene la fila en un desplazamiento especificado o la fila marcada por un marcador de este marcador.|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|Captura de filas a partir de una posición fracciones del conjunto de filas.|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|Llamadas [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) para liberar el identificador de fila actual.|  
|[SetData](../../data/oledb/crowset-setdata.md)|Establece los valores de datos en una o más columnas de una fila mediante [IRowsetChange:SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx).|  
|[Undo](../../data/oledb/crowset-undo.md)|Deshace los cambios realizados en una fila desde la última recuperación o [actualización](../../data/oledb/crowset-update.md).|  
|[Actualizar](../../data/oledb/crowset-update.md)|Los cambios realizados en la fila actual desde la última captura o de actualizaciones pendientes transmite.|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|Los cambios pendientes realizados en todas las filas desde la última captura o de actualización transmite.|  
  
## <a name="remarks"></a>Comentarios  
 En OLE DB, un conjunto de filas es el objeto a través del cual un programa establece y recupera los datos.  
  
 Esta clase no pretende ser crea una instancia, pero en su lugar se pasa como un parámetro de plantilla a `CTable` o `CCommand` (`CRowset` es el valor predeterminado).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo DBViewer](../../visual-cpp-samples.md)   
 [Ejemplo multiRead](../../visual-cpp-samples.md)   
 [Ejemplo de atributos multiRead](../../visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)