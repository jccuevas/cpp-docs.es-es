---
title: "ICommandImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandImpl (clase)"
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ICommandImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la implementación de la interfaz de [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) .  
  
## Sintaxis  
  
```  
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### Parámetros  
 `T`  
 La clase, derivada de `ICommandImpl`.  
  
 `CommandBase`  
 Una interfaz de comando.  El valor predeterminado es `ICommand`.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|Cancela la ejecución del comando actual.|  
|[Cancelar](../../data/oledb/icommandimpl-cancel.md)|Cancela la ejecución del comando actual.|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|Crea un objeto de conjunto de filas.|  
|[Ejecutar](../../data/oledb/icommandimpl-execute.md)|Ejecuta el comando.|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|Devuelve un puntero de interfaz a la sesión que creó el comando.|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|Constructor.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|Indica si el comando debe cancelarse.|  
|[el m\_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|Indica si el comando se cancelará al ejecutarse.|  
|[el m\_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|Indica si el comando se está ejecutando actualmente.|  
  
## Comentarios  
 Una interfaz de enlace en el objeto de comando.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)