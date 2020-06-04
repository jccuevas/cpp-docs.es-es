---
title: Interfaz IWorkerThreadClient
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 6a68f25f153a0ad2cf42ebfaa374ff63c5746fcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326307"
---
# <a name="iworkerthreadclient-interface"></a>Interfaz IWorkerThreadClient

`IWorkerThreadClient`es la interfaz implementada por los clientes de la clase [CWorkerThread.](../../atl/reference/cworkerthread-class.md)

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CloseHandle](#closehandle)|Implemente este método para cerrar el identificador asociado a este objeto.|
|[Ejecutar](#execute)|Implemente este método para ejecutar código cuando se señale el identificador asociado a este objeto.|

## <a name="remarks"></a>Observaciones

Implemente esta interfaz cuando tenga código que necesite ejecutarse en un subproceso de trabajo en respuesta a un identificador que se señala.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implemente este método para cerrar el identificador asociado a este objeto.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parámetros

*hHandle*<br/>
El mango que se va a cerrar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El identificador pasado a este método se asoció anteriormente a este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra `IWorkerThreadClient::CloseHandle`una implementación simple de .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Ejecutar

Implemente este método para ejecutar código cuando se señale el identificador asociado a este objeto.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parámetros

*dwParam*<br/>
El parámetro de usuario.

*hObject*<br/>
El mango que se ha señalado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El identificador y DWORD/pointer pasados a este método se asociaron previamente a este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra `IWorkerThreadClient::Execute`una implementación simple de .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Consulte también

[Clases](../../atl/reference/atl-classes.md)<br/>
[Clase CWorkerThread](../../atl/reference/cworkerthread-class.md)
