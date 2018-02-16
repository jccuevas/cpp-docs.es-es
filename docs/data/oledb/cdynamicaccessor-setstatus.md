---
title: CDynamicAccessor::SetStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
dev_langs:
- C++
helpviewer_keywords:
- SetStatus method
ms.assetid: 6db82694-e87d-4bf8-a7e3-5765cf6abff9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0efaca855eed98a0d62c9a6da50dd140b9e9bc1f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessorsetstatus"></a>CDynamicAccessor::SetStatus
Establece el estado de la columna especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```
bool SetStatus(DBORDINAL nColumn,   
   DBSTATUS status)throw();  

bool SetStatus(const CHAR* pColumnName,   
   DBSTATUS status) throw();  

bool SetStatus(const WCHAR* pColumnName,   
   DBSTATUS status) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nColumn`  
 [in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si lo hay.  
  
 *status*  
 [in] El estado de la columna. Vea [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en el *referencia del programador de OLE DB* para obtener más información.  
  
 `pColumnName`  
 [in] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el estado de la columna especificada está establecido correctamente. En caso contrario, esta función devuelve **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (clase)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)