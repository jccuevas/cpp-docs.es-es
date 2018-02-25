---
title: CRowset::Delete | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CRowset::Delete
- CRowset.Delete
- CRowset::Delete
- ATL.CRowset.Delete
- ATL::CRowset<TAccessor>::Delete
- CRowset<TAccessor>.Delete
- CRowset<TAccessor>::Delete
- ATL.CRowset<TAccessor>.Delete
dev_langs:
- C++
helpviewer_keywords:
- Delete method
ms.assetid: 4feb4f7e-139f-489a-b7d5-ea6ec0058e0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: abbb56f013a7366f27c0e0f46fc99bd451db079e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetdelete"></a>CRowset::Delete
Llamadas [IRowsetChange:: DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx) para eliminar la fila actual del conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Delete() const throw();  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (Clase)](../../data/oledb/crowset-class.md)