---
title: 'IRowsetUpdateImpl:: M_mapcacheddata | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- m_mapCachedData
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bd19f8706e50d1eefb26dadfb837d8bd4f13f061
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103260"
---
# <a name="irowsetupdateimplmmapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData
Un mapa que contiene los datos originales para la operación diferida.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hRow`  
 Identificador de las filas de los datos.  
  
 `pData`  
 Un puntero a los datos que se va a almacenar en caché. Los datos son de tipo *almacenamiento* (la clase de registro de usuario). Consulte la *almacenamiento* argumento de plantilla en [IRowsetUpdateImpl (clase)](../../data/oledb/irowsetupdateimpl-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetUpdateImpl (Clase)](../../data/oledb/irowsetupdateimpl-class.md)