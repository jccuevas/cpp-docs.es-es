---
title: CRowset::GetRowStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowset.GetRowStatus
- ATL.CRowset<TAccessor>.GetRowStatus
- ATL::CRowset<TAccessor>::GetRowStatus
- CRowset::GetRowStatus
- ATL::CRowset::GetRowStatus
- CRowset<TAccessor>::GetRowStatus
- ATL.CRowset.GetRowStatus
- CRowset<TAccessor>.GetRowStatus
- GetRowStatus
dev_langs:
- C++
helpviewer_keywords:
- GetRowStatus method
ms.assetid: 7a29a235-cb7e-40c1-92ce-5441751febee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0dd42846eb6ee46ea38c808c7542af8fd9990201
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetgetrowstatus"></a>CRowset::GetRowStatus
Devuelve el estado de todas las filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetRowStatus(DBPENDINGSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStatus`  
 [out] Un puntero a una ubicación donde `GetRowStatus` devuelve el valor de estado. Vea DBPENDINGSTATUS en referencia del programador OLE DB.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método requiere que la interfaz opcional `IRowsetUpdate`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)