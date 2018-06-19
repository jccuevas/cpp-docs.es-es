---
title: 'Csimplerow:: Compare | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75d79e753f1f4af630c26ef07fbb7241576535ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098970"
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
 [Csimplerow:: Releaserow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)