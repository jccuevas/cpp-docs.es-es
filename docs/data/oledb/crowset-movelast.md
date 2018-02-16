---
title: CRowset::MoveLast | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset<TAccessor>::MoveLast
- CRowset<TAccessor>::MoveLast
- ATL.CRowset.MoveLast
- ATL::CRowset::MoveLast
- CRowset<TAccessor>.MoveLast
- MoveLast
- CRowset::MoveLast
- ATL.CRowset<TAccessor>.MoveLast
- CRowset.MoveLast
dev_langs:
- C++
helpviewer_keywords:
- MoveLast method
ms.assetid: 81063578-ae9d-467b-8c88-81d8fc66e020
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1080a86273df82361511eaee3c3616aeb0868fd3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetmovelast"></a>CRowset::MoveLast
Mueve el cursor a la última fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT MoveLast() throw();  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Llamadas [IRowset:: RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) para cambiar la posición de la ubicación de búsqueda siguiente a la última posición y recupera la última fila.  
  
 Este método requiere que se establezcan **DBPROP_CANSCROLLBACKWARDS** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas. (Para mejorar el rendimiento, también se puede establecer **DBPROP_QUICKRESTART** a `VARIANT_TRUE`.)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)