---
title: IRowsetNotifyImpl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 860b735863acbcac869a4a297984084946aaf028
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106263"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl (Clase)
Implementa y registra [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) en el consumidor (también conocido como "receptor") para que pueda controlar las notificaciones.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|Notifica al consumidor de cualquier cambio en el valor de una columna.|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|Notifica al consumidor del primer cambio en una fila o de cualquier cambio que afecta a toda la fila.|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|Notifica al consumidor de cualquier cambio que afecte a todo el conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 Vea [recibir notificaciones](../../data/oledb/receiving-notifications.md) acerca de cómo implementar la interfaz de punto de conexión en el consumidor.  
  
 `IRowsetNotifyImpl` Proporciona una implementación ficticia para `IRowsetNotify`, con funciones vacías para la `IRowsetNotify` métodos [OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx), [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx), y [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx). Si se hereda de esta clase al implementar un `IRowsetNotify` interfaz, puede implementar solo los métodos que necesita. También debe proporcionar implementaciones vacías para los demás métodos usted mismo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP (Clase)](../../data/oledb/irowsetnotifycp-class.md)