---
title: 'Iopenrowsetimpl:: CreateRowset | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d4554a2aeee3218ce505dc2c135167a3e38d55c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105184"
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
Crea un objeto de conjunto de filas. No llama directamente al usuario. Vea [IOpenRowset:: OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en el *referencia del programador OLE DB.*  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `RowsetClass`  
 Un miembro de clase de plantilla que representa la clase de conjunto de filas del usuario. Normalmente, generado por el asistente.  
  
 `pRowsetObj`  
 [out] Un puntero a un objeto de conjunto de filas. Normalmente no se utiliza este parámetro, pero se puede usar si debe realizar más trabajo en el conjunto de filas antes de pasarlo a un objeto COM. La duración de `pRowsetObj` está limitado por `ppRowset`.  
  
 Para otros parámetros, vea [IOpenRowset:: OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en el *referencia del programador de OLE DB.*  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IOpenRowsetImpl (Clase)](../../data/oledb/iopenrowsetimpl-class.md)