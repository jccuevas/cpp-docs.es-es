---
title: IWorkerThreadClient (interfaz)
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 22ea136dd91a514ff10e13cd02b796565b7b0307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523644"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient (interfaz)

`IWorkerThreadClient` es la interfaz implementada por los clientes de la [CWorkerThread](../../atl/reference/cworkerthread-class.md) clase.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CloseHandle](#closehandle)|Implemente este método para cerrar el identificador asociado a este objeto.|
|[Execute](#execute)|Implemente este método para ejecutar código cuando se señaliza el identificador asociado a este objeto.|

## <a name="remarks"></a>Comentarios

Implemente esta interfaz si tiene código que necesita para ejecutarse en un subproceso de trabajo en respuesta a un identificador que se ha señalado.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implemente este método para cerrar el identificador asociado a este objeto.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parámetros

*hHandle*<br/>
El identificador al cerrarse.

### <a name="return-value"></a>Valor devuelto

Devuelva S_OK si funciona correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El identificador pasado a este método se asoció anteriormente con este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra una implementación simple de `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implemente este método para ejecutar código cuando se señaliza el identificador asociado a este objeto.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parámetros

*dwParam*<br/>
El parámetro de usuario.

*hObject*<br/>
El identificador que se convertirá en señalado.

### <a name="return-value"></a>Valor devuelto

Devuelva S_OK si funciona correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El identificador y el DWORD/puntero pasado a este método estaban asociados anteriormente con este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra una implementación simple de `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Vea también

[Clases](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread (clase)](../../atl/reference/cworkerthread-class.md)
