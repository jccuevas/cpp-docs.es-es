---
title: ICommandImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandImpl class
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec1c9bb3a430b30350ca3940fc7c90e6758d7c40
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="icommandimpl-class"></a>ICommandImpl (Clase)
Proporciona la implementación para la [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `ICommandImpl`.  
  
 `CommandBase`  
 Una interfaz de comandos. De manera predeterminada, es `ICommand`.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|Cancela la ejecución del comando actual.|  
|[Cancelar](../../data/oledb/icommandimpl-cancel.md)|Cancela la ejecución del comando actual.|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|Crea un objeto de conjunto de filas.|  
|[Execute](../../data/oledb/icommandimpl-execute.md)|Ejecuta el comando.|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|Devuelve un puntero de interfaz a la sesión que creó el comando.|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|El constructor.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|Indica si se puede cancelar el comando.|  
|[m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|Indica si se cancelará cuando se ejecuta el comando.|  
|[m_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|Indica si el comando se está ejecutando actualmente.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria en el objeto de comando.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)