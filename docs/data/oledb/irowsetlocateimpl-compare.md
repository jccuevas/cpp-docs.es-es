---
title: 'IRowsetLocateImpl:: Compare | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 208f912e92045daec36066e1dcc06fc38b5a8ed2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetlocateimplcompare"></a>IRowsetLocateImpl::Compare
Compara dos marcadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (Compare )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetLocate:: Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Cualquiera de los marcadores pueden ser un estándar definido por OLE DB [marcador estándar](https://msdn.microsoft.com/en-us/library/ms712954.aspx) (**DBBMK_FIRST**, **DBBMK_LAST**, o **DBBMK_INVALID**). El valor devuelto en `pComparison` indica la relación entre los dos marcadores:  
  
-   **DBCOMPARE_LT** (`cbBookmark1` antes `cbBookmark2`.)  
  
-   **DBCOMPARE_EQ** (`cbBookmark1` es igual a `cbBookmark2`.)  
  
-   **DBCOMPARE_GT** (`cbBookmark1` después `cbBookmark2`.)  
  
-   **DBCOMPARE_NE** (los marcadores son iguales y no ordenada).  
  
-   **DBCOMPARE_NOTCOMPARABLE** (no se pueden comparar los marcadores).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetLocateImpl (Clase)](../../data/oledb/irowsetlocateimpl-class.md)