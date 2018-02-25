---
title: CDynamicAccessor::GetColumnInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9f311e9fc5330a68edba4fd5029e97b75033406
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorgetcolumninfo"></a>CDynamicAccessor::GetColumnInfo
Devuelve los metadatos de columna necesarios para la mayoría de los consumidores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRowset`  
 [in] Un puntero a la [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) interfaz.  
  
 *pColumns*  
 [out] Un puntero a la memoria en el que se va a devolver el número de columnas del conjunto de filas; Este número incluye la columna de marcador, si hay alguno.  
  
 *ppColumnInfo*  
 [out] Un puntero a la memoria en el que se va a devolver una matriz de **DBCOLUMNINFO** estructuras. Vea "Estructuras DBCOLUMNINFO" en [IColumnsInfo:: GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en el *referencia del programador OLE DB*.  
  
 `ppStringsBuffer`  
 [out] Un puntero a la memoria en el que se va a devolver un puntero al almacenamiento de información para todos los valores de cadena (nombres usan ya sea dentro de *columnid* o para *pwszName*) dentro de un bloque de asignación único.  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
## <a name="remarks"></a>Comentarios  
 Vea [IColumnsInfo:: GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en el *referencia del programador de OLE DB* para obtener información sobre los tipos de datos **DBORDINAL**, **DBCOLUMNINFO**, y **OLECHAR**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)