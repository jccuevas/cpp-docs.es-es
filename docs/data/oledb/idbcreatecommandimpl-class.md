---
title: IDBCreateCommandImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6d8a07ded3da02c21c4ee8c528474efc6e52b6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021569"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl (Clase)

Proporciona una implementación de la [IDBCreateCommand](/previous-versions/windows/desktop/ms711625\(v=vs.85\)) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>Parámetros  

*T*<br/>
El objeto de sesión derivada de `IDBCreateCommandImpl`.  
  
*CommandClass*<br/>
La clase de comando.  

## <a name="requirements"></a>Requisitos  

**Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[CreateCommand](#createcommand)|Crea un nuevo comando.|  
  
## <a name="remarks"></a>Comentarios  

Una interfaz opcional para el objeto de sesión para obtener un nuevo comando.  

## <a name="createcommand"></a> Idbcreatecommandimpl:: CreateCommand

Crea un nuevo comando y devuelve la interfaz solicitada.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IDBCreateCommand:: CreateCommand](/previous-versions/windows/desktop/ms709772\(v=vs.85\)) en el *referencia del programador OLE DB*.  
  
Algunos parámetros se corresponden con *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en `IDBCreateCommand::CreateCommand`:  
  
|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>Vea también  

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)