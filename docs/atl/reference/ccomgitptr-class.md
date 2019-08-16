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
ms.openlocfilehash: 00265cc445191a5a539ab21d6f64b255849495e9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497265"
---
# <a name="ccomgitptr-class"></a>Clase CComGITPtr

Esta clase proporciona métodos para trabajar con punteros de interfaz y la tabla de interfaz global (GIT).

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del puntero de interfaz que se va a almacenar en GIT.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|El constructor.|
|[CComGITPtr::~CComGITPtr](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Llame a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) en el puntero que se pasa.|
|[CComGITPtr::Detach](#detach)|Llame a este método para desasociar la `CComGITPtr` interfaz del objeto.|
|[CComGITPtr::GetCookie](#getcookie)|Llame a este método para devolver la cookie del `CComGITPtr` objeto.|
|[CComGITPtr::Revoke](#revoke)|Llame a este método para quitar la interfaz de la tabla de interfaz global (GIT).|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComGITPtr:: Operator DWORD](#operator_dword)|Devuelve la cookie del `CComGITPtr` objeto.|
|[CComGITPtr::operator =](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Cookie.|

## <a name="remarks"></a>Comentarios

Los objetos que agregan el contador de referencias de subprocesamiento libre y necesitan usar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las referencias de las interfaces son correctas. Normalmente esto implica almacenar los punteros de interfaz en GIT y obtener el puntero de GIT cada vez que se usa. La clase `CComGITPtr` se proporciona para ayudarle a usar punteros de interfaz almacenados en Git.

> [!NOTE]
>  La utilidad de tabla de interfaz global solo está disponible en Windows 95 con DCOM versión 1,1 y versiones posteriores, Windows 98, Windows NT 4,0 con Service Pack 3 y versiones posteriores, y Windows 2000.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="attach"></a>  CComGITPtr::Attach

Llame a este método para registrar el puntero de interfaz en la tabla de interfaz global (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero de interfaz que se va a agregar a GIT.

*dwCookie*<br/>
Cookie que se usa para identificar el puntero de interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si GIT no es válido o si la cookie es igual a NULL.

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
de Puntero de interfaz que se va a almacenar en la tabla de interfaz global (GIT).

*git*<br/>
de Referencia a un objeto existente `CComGITPtr` .

*dwCookie*<br/>
de Cookie que se usa para identificar el puntero de interfaz.

*rv*<br/>
de Objeto de `CComGITPtr` origen del que se van a trasladar los datos.

### <a name="remarks"></a>Comentarios

Crea un nuevo `CComGITPtr` objeto y, opcionalmente, usa `CComGITPtr` un objeto existente.

El constructor que usa *RV* es un constructor de movimiento. Los datos se mueven desde el origen, *RV*y, a continuación, se borra *RV* .

##  <a name="dtor"></a>  CComGITPtr::~CComGITPtr

Destructor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Comentarios

Quita la interfaz de la tabla de interfaz global (GIT), mediante [CComGITPtr:: REVOKE](#revoke).

##  <a name="copyto"></a>  CComGITPtr::CopyTo

Llame a este método para copiar la interfaz de la tabla de interfaz global (GIT) en el puntero que se pasa.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parámetros

*pp*<br/>
Puntero que va a recibir la interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

La interfaz de GIT se copia en el puntero que se pasa. El llamador debe liberar el puntero cuando ya no sea necesario.

##  <a name="detach"></a>  CComGITPtr::Detach

Llame a este método para desasociar la `CComGITPtr` interfaz del objeto.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie del `CComGITPtr` objeto.

### <a name="remarks"></a>Comentarios

Depende del llamador quitar la interfaz de GIT, mediante [CComGITPtr:: REVOKE](#revoke).

##  <a name="getcookie"></a>  CComGITPtr::GetCookie

Llame a este método para devolver la cookie del `CComGITPtr` objeto.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie.

### <a name="remarks"></a>Comentarios

La cookie es una variable que se usa para identificar una interfaz y su ubicación.

##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie

Cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Comentarios

La cookie es una variable miembro que se usa para identificar una interfaz y su ubicación.

##  <a name="operator_eq"></a>CComGITPtr:: Operator =

Operador de asignación.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a una interfaz.

*git*<br/>
de Referencia a un `CComGITPtr` objeto.

*dwCookie*<br/>
de Cookie que se usa para identificar el puntero de interfaz.

*rv*<br/>
de Del `CComGITPtr` que se van a trasladar los datos.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CComGITPtr` actualizado.

### <a name="remarks"></a>Comentarios

Asigna un nuevo valor a un `CComGITPtr` objeto, ya sea de un objeto existente o de una referencia a una tabla de interfaz global.

##  <a name="operator_dword"></a>CComGITPtr:: Operator DWORD

Devuelve la cookie asociada `CComGITPtr` al objeto.

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

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Quita la interfaz de GIT.

## <a name="see-also"></a>Vea también

[Contador de referencias de subprocesamiento libre](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Acceso a interfaces entre apartamentos](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Cuándo usar la tabla de interfaz global](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
