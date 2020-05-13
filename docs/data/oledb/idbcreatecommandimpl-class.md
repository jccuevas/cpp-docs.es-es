---
title: IDBCreateCommandImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 4a4978401ba90e3a7a91ac40cc1b0668adf12ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210722"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl (Clase)

Proporciona una implementación de la interfaz [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Objeto de sesión derivado de `IDBCreateCommandImpl`.

*CommandClass*<br/>
La clase de comando.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[CreateCommand](#createcommand)|Crea un nuevo comando.|

## <a name="remarks"></a>Observaciones

Una interfaz opcional en el objeto de sesión para obtener un nuevo comando.

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a>Idbcreatecommandimpl (:: CreateCommand

Crea un nuevo comando y devuelve la interfaz solicitada.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Parámetros

Consulte [IDBCreateCommand:: CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) en la *Referencia del programador de OLE DB*.

Algunos parámetros corresponden a los parámetros de *Referencia del programador de OLE DB* de nombres diferentes, que se describen en `IDBCreateCommand::CreateCommand`:

|OLE DB de los parámetros de plantilla|Parámetros *de referencia del programador de OLE DB*|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
