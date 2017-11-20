---
title: 'Iopenrowsetimpl:: OpenRowset | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs: C++
helpviewer_keywords: OpenRowset method
ms.assetid: 2ece8d6c-d165-4f1d-b155-8609bbb60eb6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 168b9a8e73ea1c9c365ba87b2b8900e710de8bcc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="iopenrowsetimplopenrowset"></a>IOpenRowsetImpl::OpenRowset
Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT OpenRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IOpenRowset:: OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Este método no se encuentra en ATLDB. H. Se crea mediante el Asistente para objetos ATL cuando se crea un proveedor.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IOpenRowsetImpl (Clase)](../../data/oledb/iopenrowsetimpl-class.md)