---
title: CBookmark (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5c0f5f7a2af7c5b744fcad31ae6901988e92b9e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cbookmark-class"></a>CBookmark (Clase)
Contiene un valor de marcador en su búfer.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nSize`  
 El tamaño del búfer del marcador en bytes. Cuando `nSize` es cero, el búfer de marcador se creará dinámicamente en tiempo de ejecución.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|El constructor|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|Recupera el puntero al búfer.|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|Recupera el tamaño del búfer en bytes.|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|Establece el valor de marcador.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](../../data/oledb/cbookmark-operator-equal.md)|Asigna un valor `CBookmark` clase a otro.|  
  
## <a name="remarks"></a>Comentarios  
 **CBookmark\<0 >** es una especialización de plantilla de `CBookmark`; su búfer se crea dinámicamente en tiempo de ejecución.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)