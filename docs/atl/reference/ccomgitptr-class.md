---
title: Clase CComGITPtr
ms.date: 11/04/2016
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: 230eeb1577189d2057e530e1df8ef99c611fb32b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327840"
---
# <a name="ccomgitptr-class"></a>Clase CComGITPtr

Esta clase proporciona métodos para tratar con punteros de interfaz y la tabla de interfaz global (GIT).

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo del puntero de interfaz que se va a almacenar en el GIT.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|El constructor.|
|[CComGITPtr::-CComGITPtr](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComGITPtr::Adjuntar](#attach)|Llame a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) al puntero pasado.|
|[CComGITPtr::Detach](#detach)|Llame a este método para desasociar la interfaz del `CComGITPtr` objeto.|
|[CComGITPtr::GetCookie](#getcookie)|Llame a este método para `CComGITPtr` devolver la cookie del objeto.|
|[CComGITPtr::Revocar](#revoke)|Llame a este método para quitar la interfaz de la tabla de interfaz global (GIT).|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComGITPtr::operador DWORD](#operator_dword)|Devuelve la cookie `CComGITPtr` del objeto.|
|[CComGITPtr::operador ?](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|La cookie.|

## <a name="remarks"></a>Observaciones

Los objetos que agregan el serializador de subprocesos libre y necesitan usar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las interfaces se serializan correctamente. Normalmente, esto implica almacenar los punteros de interfaz en el GIT y obtener el puntero del GIT cada vez que se usa. La `CComGITPtr` clase se proporciona para ayudarle a utilizar punteros de interfaz almacenados en el GIT.

> [!NOTE]
> El recurso de tabla de interfaz global solo está disponible en Windows 95 con DCOM versión 1.1 y versiones posteriores, Windows 98, Windows NT 4.0 con Service Pack 3 y versiones posteriores y Windows 2000.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomgitptrattach"></a><a name="attach"></a>CComGITPtr::Adjuntar

Llame a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
El puntero de interfaz que se agregará al GIT.

*dwCookie*<br/>
La cookie utilizada para identificar el puntero de interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si el GIT no es válido o si la cookie es igual a NULL.

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a>CComGITPtr::CComGITPtr

El constructor.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Un puntero de interfaz que se almacenará en la tabla de interfaz global (GIT).

*Git*<br/>
[en] Una referencia a `CComGITPtr` un objeto existente.

*dwCookie*<br/>
[en] Una cookie utilizada para identificar el puntero de interfaz.

*Rv*<br/>
[en] El `CComGITPtr` objeto de origen desde el que se va a mover los datos.

### <a name="remarks"></a>Observaciones

Crea un `CComGITPtr` nuevo objeto, opcionalmente utilizando un objeto existente. `CComGITPtr`

El constructor que utiliza *rv* es un constructor de movimiento. Los datos se mueven desde el origen, *rv*y, a continuación, se borra *rv.*

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a>CComGITPtr::-CComGITPtr

Destructor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Observaciones

Quita la interfaz de la tabla de interfaz global (GIT), utilizando [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a>CComGITPtr::CopyTo

Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) al puntero pasado.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parámetros

*Pp*<br/>
El puntero que va a recibir la interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

La interfaz del GIT se copia en el puntero pasado. El autor de la llamada debe liberar el puntero cuando ya no sea necesario.

## <a name="ccomgitptrdetach"></a><a name="detach"></a>CComGITPtr::Detach

Llame a este método para desasociar la interfaz del `CComGITPtr` objeto.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie `CComGITPtr` del objeto.

### <a name="remarks"></a>Observaciones

Depende del autor de la llamada quitar la interfaz del GIT, utilizando [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a>CComGITPtr::GetCookie

Llame a este método para `CComGITPtr` devolver la cookie del objeto.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie.

### <a name="remarks"></a>Observaciones

La cookie es una variable utilizada para identificar una interfaz y su ubicación.

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a>CComGITPtr::m_dwCookie

La cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Observaciones

La cookie es una variable miembro utilizada para identificar una interfaz y su ubicación.

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a>CComGITPtr::operador ?

El operador de asignación.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Un puntero a una interfaz.

*Git*<br/>
[en] Una referencia `CComGITPtr` a un objeto.

*dwCookie*<br/>
[en] Una cookie utilizada para identificar el puntero de interfaz.

*Rv*<br/>
[en] El `CComGITPtr` para mover datos desde.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CComGITPtr` objeto actualizado.

### <a name="remarks"></a>Observaciones

Asigna un nuevo valor `CComGITPtr` a un objeto, ya sea desde un objeto existente o desde una referencia a una tabla de interfaz global.

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a>CComGITPtr::operador DWORD

Devuelve la cookie `CComGITPtr` asociada al objeto.

```
operator DWORD() const;
```

### <a name="remarks"></a>Observaciones

La cookie es una variable utilizada para identificar una interfaz y su ubicación.

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a>CComGITPtr::Revocar

Llame a este método para quitar la interfaz actual de la tabla de interfaz global (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Quita la interfaz del GIT.

## <a name="see-also"></a>Consulte también

[Alguacil de hilo libre](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Acceso a interfaces en todos los apartamentos](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Cuándo utilizar la tabla de interfaz global](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
