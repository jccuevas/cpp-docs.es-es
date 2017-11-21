---
title: 'CDynamicAccessor:: GetStatus | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
dev_langs: C++
helpviewer_keywords: GetStatus method
ms.assetid: 8f1aba69-5c2c-4ca7-ad84-7b4b27995eb8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fd1c55e78cdc4a0ec8bd5c24c7010ec133b043bf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetstatus"></a>CDynamicAccessor::GetStatus
Recupera el estado de la columna especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      bool GetStatus(   
   DBORDINAL nColumn,   
   DBSTATUS* pStatus    
) const throw( );  
bool GetStatus(  
   const CHAR* pColumnName,  
   DBSTATUS* pStatus   
) const throw( );  
bool GetStatus(  
   const WCHAR* pColumnName,  
   DBSTATUS* pStatus   
) const throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nColumn`  
 [in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si lo hay.  
  
 `pColumnName`  
 [in] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
 `pStatus`  
 [out] Un puntero a la variable que contiene el estado de la columna. Vea [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en el *referencia del programador de OLE DB* para obtener más información.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si se encuentra la columna especificada. En caso contrario, esta función devuelve **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (clase)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)