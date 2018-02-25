---
title: 'CDataSource:: Getinitializationstring | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
dev_langs:
- C++
helpviewer_keywords:
- GetInitializationString method
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d548fd79ec857f95957bf8306511738d1c88ea55
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdatasourcegetinitializationstring"></a>CDataSource::GetInitializationString
Recupera la cadena de inicialización de un origen de datos que está abierto actualmente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,   
   bool bIncludePassword = false) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pInitializationString*  
 [out] Un puntero a la cadena de inicialización.  
  
 *bIncludePassword*  
 [in] **true** si la cadena incluye una contraseña; en caso contrario, **false**.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 La cadena de inicialización resultante puede utilizarse para después volver a abrir esta conexión de origen de datos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataSource (Clase)](../../data/oledb/cdatasource-class.md)