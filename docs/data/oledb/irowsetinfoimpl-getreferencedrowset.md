---
title: 'Irowsetinfoimpl:: Getreferencedrowset | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
dev_langs:
- C++
helpviewer_keywords:
- GetReferencedRowset method
ms.assetid: 94d2155c-9da0-4c19-a37c-bc35716359fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca538822acdc9493e89639715588db35d5cee686
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103335"
---
# <a name="irowsetinfoimplgetreferencedrowset"></a>IRowsetInfoImpl::GetReferencedRowset
Devuelve un puntero de interfaz al conjunto de filas al que se aplica un marcador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetInfo::GetReferencedRowset](https://msdn.microsoft.com/en-us/library/ms721145.aspx) en el *referencia del programador OLE DB*. El *iOrdinal* parámetro debe ser una columna de marcador.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetInfoImpl (clase)](../../data/oledb/irowsetinfoimpl-class.md)   
 [IRowsetInfoImpl::GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)   
 [IRowsetInfoImpl::GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)