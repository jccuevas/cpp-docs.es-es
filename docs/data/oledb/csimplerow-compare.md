---
title: CSimpleRow::Compare | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2649fcf708abaf9e971490d3e88a746c264b1009
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
Compara dos filas para comprobar si hacen referencia a la misma instancia de fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Compare(CSimpleRow* pRow);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRow`  
 Un puntero a un `CSimpleRow` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` valor, normalmente `S_OK`, que indica las dos filas son la misma instancia de fila, o **S_FALSE**, que indica las dos filas son diferentes. Vea [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) en el *referencia del programador de OLE DB* para otros posibles valores devueltos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CSimpleRow (clase)](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)