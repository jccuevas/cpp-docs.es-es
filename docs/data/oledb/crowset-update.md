---
title: 'CRowset:: Update | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset.Update
- ATL.CRowset.Update
- ATL.CRowset<TAccessor>.Update
- ATL::CRowset<TAccessor>::Update
- CRowset<TAccessor>::Update
- CRowset::Update
- CRowset<TAccessor>.Update
- ATL::CRowset::Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b40486db73d3d545a3226e71a19ba0b588f631ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetupdate"></a>CRowset::Update
Los cambios pendientes realizados en la fila actual desde la última recuperación transmite o **actualización** llamar en ella.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Update(DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcRows`  
 [out] Un puntero a la ubicación donde **actualizar** devuelve el número de filas que intentó actualizar, si es necesario.  
  
 `phRow`  
 [out] Un puntero a la ubicación donde **actualizar** devuelve el identificador de la fila intentó actualizar. No hay ningún identificador se devuelve si `phRow` es null.  
  
 `pStatus`  
 [out] Un puntero a la ubicación donde **actualización** devuelve el valor de estado de fila. Si no se devuelve ningún estado `pStatus` es null.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Los cambios pendientes realizados en la fila actual desde que se capturan o se actualizó por última esa fila transmite (mediante **actualización** o [UpdateAll](../../data/oledb/crowset-updateall.md)). Se suele llamar a [SetData](../../data/oledb/crowset-setdata.md) para establecer los valores de datos de columnas de una fila y, a continuación, llame a **actualización** para transmitir los cambios.  
  
 Este método requiere que la interfaz opcional `IRowsetUpdate`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate:: Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset:: UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)