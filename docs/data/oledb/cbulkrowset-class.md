---
title: CBulkRowset (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
dev_langs: C++
helpviewer_keywords: CBulkRowset class
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 26ed8c0a3f58ae046ad3e4766b7e009023759be0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cbulkrowset-class"></a>CBulkRowset (Clase)
Recupera y manipula filas para trabajar con datos de forma masiva mediante la recuperación de varios identificadores de fila con una sola llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)|Incrementa el recuento de referencias.|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|Constructor.|  
|[MoveFirst](../../data/oledb/cbulkrowset-movefirst.md)|Recupera la primera fila de datos, realizar una captura de forma masiva nueva si es necesario.|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|Se mueve a la última fila.|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|Recupera la fila siguiente de datos.|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|Se desplaza a la fila anterior.|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|Obtiene la fila en un desplazamiento especificado o la fila marcada por un marcador de este marcador.|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|Captura de filas a partir de una posición fracciones del conjunto de filas.|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|Establece la fila actual (**m_nCurrentRow**) a cero y libera todas las filas.|  
|[SetRows](../../data/oledb/cbulkrowset-setrows.md)|Establece el número de identificadores de fila para ser recuperado por una llamada.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `CBulkRowset` clase.  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)