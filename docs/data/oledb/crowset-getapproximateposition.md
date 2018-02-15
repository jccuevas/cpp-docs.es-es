---
title: CRowset::GetApproximatePosition | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::GetApproximatePosition
- ATL::CRowset<TAccessor>::GetApproximatePosition
- CRowset.GetApproximatePosition
- CRowset::GetApproximatePosition
- GetApproximatePosition
- ATL.CRowset.GetApproximatePosition
- CRowset<TAccessor>::GetApproximatePosition
dev_langs:
- C++
helpviewer_keywords:
- GetApproximatePosition method
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 07d0f816579fb7097389d676e241143d4891677d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetgetapproximateposition"></a>CRowset::GetApproximatePosition
Devuelve la posición aproximada de una fila que corresponda a un marcador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetApproximatePosition(const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pBookmark`  
 [in] Un puntero a un marcador que identifica la fila cuya posición se va a calcular. **NULL** si solo se necesita el recuento de filas.  
  
 *pPosition*  
 [out] Un puntero a la ubicación donde `GetApproximatePosition` devuelve la posición de la fila. **NULL** si la posición no es necesaria.  
  
 `pcRows`  
 [out] Un puntero a la ubicación donde `GetApproximatePosition` devuelve el número total de filas. **NULL** si el recuento de filas no es necesario.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método requiere que la interfaz opcional `IRowsetScroll`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetScroll** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre el uso de marcadores en los consumidores, consulte [Using Bookmarks](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)