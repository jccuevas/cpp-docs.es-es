---
title: 'ICommandImpl:: Getdbsession | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 116838ebb5857d5761b9d58d4f84e315de56d240
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099750"
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