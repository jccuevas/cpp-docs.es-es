---
title: IDBCreateCommandImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 7450d91cd5e5383b55e2ebb391fe5f1190cbed2a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024934"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl (Clase)

Proporciona una implementación de la [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) interfaz.

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

## <a name="createcommand"></a> IDBCreateCommandImpl::CreateCommand

Crea un nuevo comando y devuelve la interfaz solicitada.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Parámetros

Consulte [IDBCreateCommand:: CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) en el *referencia del programador OLE DB*.

Algunos parámetros se corresponden con *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en `IDBCreateCommand::CreateCommand`:

|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)