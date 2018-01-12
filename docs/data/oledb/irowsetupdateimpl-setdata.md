---
title: 'IRowsetUpdateImpl:: SetData | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
dev_langs: C++
helpviewer_keywords: SetData method
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4cc3eba57e79c40ab3f011581b08cf910ffde86e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetupdateimplsetdata"></a>IRowsetUpdateImpl::SetData
Establece los valores de datos en una o varias columnas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      STDMETHOD ( SetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetChange:: SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Este método invalida el [IRowsetChangeImpl:: SetData](../../data/oledb/irowsetchangeimpl-setdata.md) pero el método incluye almacenamiento en caché de datos originales para permitir el procesamiento de la operación de inmediato o diferido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetUpdateImpl (Clase)](../../data/oledb/irowsetupdateimpl-class.md)