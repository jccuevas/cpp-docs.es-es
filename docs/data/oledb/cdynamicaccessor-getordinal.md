---
title: 'CDynamicAccessor:: GetOrdinal | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
dev_langs:
- C++
helpviewer_keywords:
- GetOrdinal method
ms.assetid: 2095b71c-a7a4-4034-89a1-77a78cb9633f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e935340265d0239240ce47169aecb4f3210a106f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094402"
---
# <a name="cdynamicaccessorgetordinal"></a>CDynamicAccessor::GetOrdinal
Recupera el número de columna tiene un nombre de columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      bool GetOrdinal(const CHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  

bool GetOrdinal(const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pColumnName`  
 [in] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
 *pOrdinal*  
 [out] Un puntero al número de columna.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si se encuentra una columna con el nombre especificado. En caso contrario, esta función devuelve **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)