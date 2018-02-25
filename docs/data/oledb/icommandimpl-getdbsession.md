---
title: 'ICommandImpl:: Getdbsession | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
dev_langs:
- C++
helpviewer_keywords:
- GetDBSession method
ms.assetid: e5b1cb13-453f-4698-90bf-f6bfe6814a54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 11b94f64d389686abfea675c457e13296423b2e4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="icommandimplgetdbsession"></a>ICommandImpl::GetDBSession
Devuelve un puntero de interfaz a la sesión que creó el comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (GetDBSession) (REFIID riid,  
   IUnknown** ppSession);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [ICommand::GetDBSession](https://msdn.microsoft.com/en-us/library/ms719622.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Es útil para recuperar las propiedades de la sesión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [ICommandImpl (Clase)](../../data/oledb/icommandimpl-class.md)