---
title: 'ICommandImpl:: Execute | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandImpl::Execute
- ICommandImpl.Execute
dev_langs:
- C++
helpviewer_keywords:
- Execute method
ms.assetid: 033e0d4e-256b-4eed-9215-70e0bebb768c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d4d24bbb7f7aad94210672ce9bbf0cc0c7d5414
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="icommandimplexecute"></a>ICommandImpl::Execute
Ejecuta el comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Execute(IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [ICommand:: Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Solicitados la interfaz de salida será una interfaz adquirida desde el objeto de conjunto de filas creados por esta función.  
  
 **Ejecutar** llamadas [CreateRowset](../../data/oledb/icommandimpl-createrowset.md). Invalidar la implementación predeterminada para crear más de un conjunto de filas o para proporcionar sus propias condiciones para la creación de conjuntos de filas diferentes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [ICommandImpl (clase)](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)