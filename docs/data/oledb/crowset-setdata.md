---
title: CRowset::SetData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.SetData
- SetData
- ATL::CRowset::SetData
- CRowset<TAccessor>.SetData
- CRowset::SetData
- ATL.CRowset.SetData
- CRowset.SetData
- CRowset<TAccessor>::SetData
- ATL::CRowset<TAccessor>::SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 68125142-8510-4132-9393-e39efd39c784
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f9b619bbc62ac81c4d1c2cc8c27e4246c026ca23
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetsetdata"></a>CRowset::SetData
Establece los valores de datos en una o varias columnas de una fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetData() const throw();   


HRESULT SetData(int nAccessor) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nAccessor`  
 [in] El número del descriptor de acceso que se utilizará para tener acceso a los datos.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Para el `SetData` form que acepta ningún argumento, todos los descriptores de acceso se utilizan para la actualización. Se suele llamar a **SetData** para establecer los valores de datos en columnas de una fila, a continuación, llame a [actualización](../../data/oledb/crowset-update.md) para transmitir los cambios.  
  
 Este método requiere que la interfaz opcional `IRowsetChange`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetChange** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
 La operación de configuración podría producir errores si no se puede escribir una o varias columnas. Modifique la asignación del cursor para corregirlo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)