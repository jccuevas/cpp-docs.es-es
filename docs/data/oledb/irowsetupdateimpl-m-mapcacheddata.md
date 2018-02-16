---
title: IRowsetUpdateImpl::m_mapCachedData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- m_mapCachedData
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 45f990f7ab718a37975c808545d20f47d8186bd1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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