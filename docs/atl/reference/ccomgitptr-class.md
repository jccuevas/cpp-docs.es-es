---
title: CComGITPtr (clase)
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
ms.openlocfilehash: bf509d027833610e4251c009d4e444dad3fdd5ce
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296038"
---
# <a name="ccomgitptr-class"></a>CComGITPtr (clase)

Esta clase proporciona métodos para trabajar con punteros de interfaz y la tabla de interfaz global (GIT).

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo del puntero de interfaz que se almacenará en el GIT.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|El constructor.|
|[CComGITPtr::~CComGITPtr](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Llame a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) en el puntero pasado.|
|[CComGITPtr::Detach](#detach)|Llame a este método para desasociar la interfaz desde el `CComGITPtr` objeto.|
|[CComGITPtr::GetCookie](#getcookie)|Llamar a este método para devolver la cookie de la `CComGITPtr` objeto.|
|[CComGITPtr::Revoke](#revoke)|Llame a este método para quitar de la interfaz de la tabla de interfaz global (GIT).|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CComGITPtr::operator DWORD](#operator_dword)|Devuelve la cookie de la `CComGITPtr` objeto.|
|[CComGITPtr::operator =](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|La cookie.|

## <a name="remarks"></a>Comentarios

Los objetos que agregan el contador de referencias de subproceso libre y necesitan utilizar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las interfaces se serializan correctamente. Normalmente, esto implica almacenar los punteros de interfaz en el GIT y obtener el puntero de la GIT cada vez que se utiliza. La clase `CComGITPtr` se proporciona para ayudarle a usar punteros de interfaz almacenados en la GIT.

> [!NOTE]
>  La instalación de la tabla de interfaz global solo está disponible en Windows 95 con DCOM versión 1.1 y versiones posteriores, Windows 98, Windows NT 4.0 con Service Pack 3 y versiones posteriores y Windows 2000.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="attach"></a>  CComGITPtr::Attach

Llame a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
El puntero de interfaz que se agregarán a la de GIT.

*dwCookie*<br/>
La cookie utilizada para identificar el puntero de interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si el GIT no es válido, o si la cookie es igual a NULL.

##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr

El constructor.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parámetros

*p*<br/>
[in] Un puntero de interfaz que se almacenará en la tabla de interfaz global (GIT).

*git*<br/>
[in] Una referencia a una existente `CComGITPtr` objeto.

*dwCookie*<br/>
[in] Una cookie utilizada para identificar el puntero de interfaz.

*rv*<br/>
[in] El origen `CComGITPtr` mover datos de objeto.

### <a name="remarks"></a>Comentarios

Crea un nuevo `CComGITPtr` objeto, utilizando opcionalmente existente `CComGITPtr` objeto.

El uso del constructor *rv* es un constructor de movimiento. Los datos se mueven desde el origen, *rv*y, a continuación, *rv* está desactivada.

##  <a name="dtor"></a>  CComGITPtr::~CComGITPtr

Destructor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Comentarios

Quita la interfaz de la tabla de interfaz global (GIT), mediante [CComGITPtr::Revoke](#revoke).

##  <a name="copyto"></a>  CComGITPtr::CopyTo

Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) en el puntero pasado.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parámetros

*pp*<br/>
El puntero que va a recibir la interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

La interfaz de la GIT se copia en el puntero pasado. El puntero debe liberarla el llamador cuando ya no sea necesario.

##  <a name="detach"></a>  CComGITPtr::Detach

Llame a este método para desasociar la interfaz desde el `CComGITPtr` objeto.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie de la `CComGITPtr` objeto.

### <a name="remarks"></a>Comentarios

Depende del autor de la llamada para quitar de la interfaz de la GIT, mediante [CComGITPtr::Revoke](#revoke).

##  <a name="getcookie"></a>  CComGITPtr::GetCookie

Llamar a este método para devolver la cookie de la `CComGITPtr` objeto.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie.

### <a name="remarks"></a>Comentarios

La cookie es una variable que se usa para identificar una interfaz y su ubicación.

##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie

La cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Comentarios

La cookie es una variable de miembro que se usa para identificar una interfaz y su ubicación.

##  <a name="operator_eq"></a>  CComGITPtr::operator =

El operador de asignación.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parámetros

*p*<br/>
[in] Un puntero a una interfaz.

*git*<br/>
[in] Una referencia a un `CComGITPtr` objeto.

*dwCookie*<br/>
[in] Una cookie utilizada para identificar el puntero de interfaz.

*rv*<br/>
[in] El `CComGITPtr` para mover datos desde.

### <a name="return-value"></a>Valor devuelto

Devuelve el texto actualizado `CComGITPtr` objeto.

### <a name="remarks"></a>Comentarios

Asigna un nuevo valor a un `CComGITPtr` objeto, o desde un objeto existente de una referencia a una tabla de interfaz global.

##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD

Devuelve la cookie asociada con el `CComGITPtr` objeto.

```
operator DWORD() const;
```

### <a name="remarks"></a>Comentarios

La cookie es una variable que se usa para identificar una interfaz y su ubicación.

##  <a name="revoke"></a>  CComGITPtr::Revoke

Llame a este método para quitar la interfaz actual de la tabla de interfaz global (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Quita la interfaz de la GIT.

## <a name="see-also"></a>Vea también

[Contador de referencias de subproceso libre](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Acceso a las Interfaces entre apartamentos](/windows/desktop/com/accessing-interfaces-across-apartments)<br/>
[Cuándo usar la tabla de interfaz Global](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
