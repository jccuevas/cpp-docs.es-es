---
title: 'Icolumnsinfoimpl:: Mapcolumnids | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
dev_langs: C++
helpviewer_keywords: MapColumnIDs method
ms.assetid: 7aa2d011-75ba-440a-bafe-ab8fccd16dfb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: adcc2509cacdb6e05c2f3b3018fa95fd9a99e3bf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="icolumnsinfoimplmapcolumnids"></a>IColumnsInfoImpl::MapColumnIDs
Devuelve una matriz de ordinales de las columnas de un conjunto de filas que se identifican mediante los identificadores de columna especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      STDMETHOD (MapColumnIDs)(  
   DBORDINAL cColumnIDs,  
   const DBID rgColumnIDs[],  
   DBORDINAL rgColumns[]   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IColumnsInfo::MapColumnIDs](https://msdn.microsoft.com/en-us/library/ms714200.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IColumnsInfoImpl (clase)](../../data/oledb/icolumnsinfoimpl-class.md)   
 [IColumnsInfoImpl::GetColumnInfo](../../data/oledb/icolumnsinfoimpl-getcolumninfo.md)