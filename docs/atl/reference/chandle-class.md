---
title: Clase CHandle
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 4b883bdf3159c40f8d74866f04f655ae73d82a8a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747696"
---
# <a name="chandle-class"></a>Clase CHandle

Esta clase proporciona métodos para crear y usar un objeto handle.

## <a name="syntax"></a>Sintaxis

```
class CHandle
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|El constructor.|
|[CHandle::-CHandle](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHandle::Attach](#attach)|Llame a este `CHandle` método para asociar el objeto a un identificador existente.|
|[CHandle::Cerrar](#close)|Llame a este `CHandle` método para cerrar un objeto.|
|[CHandle::Detach](#detach)|Llame a este método para `CHandle` separar un identificador de un objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHandle::operador HANDLE](#operator_handle)|Devuelve el valor del identificador almacenado.|
|[CHandle::operador ?](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHandle::m_h](#m_h)|La variable miembro que almacena el identificador.|

## <a name="remarks"></a>Observaciones

Un `CHandle` objeto se puede utilizar siempre que se requiera `CHandle` un identificador: la principal diferencia es que el objeto se eliminará automáticamente.

> [!NOTE]
> Algunas funciones de API usarán NULL como un identificador vacío o no válido, mientras que otras usan INVALID_HANDLE_VALUE. `CHandle`solo usa NULL y tratará INVALID_HANDLE_VALUE como un identificador real. Si llama a una API que puede devolver INVALID_HANDLE_VALUE, debe comprobar este valor antes `CHandle` de llamar a [CHandle::Attach](#attach) o pasarlo al constructor y, en su lugar, pasar NULL.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="chandleattach"></a><a name="attach"></a>CHandle::Attach

Llame a este `CHandle` método para asociar el objeto a un identificador existente.

```cpp
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Parámetros

*H*<br/>
`CHandle`tomará la propiedad de la manija *h*.

### <a name="remarks"></a>Observaciones

Asigna el `CHandle` objeto al identificador *h* y, a continuación, llama a **h.Detach()**. En las compilaciones de depuración, se generará un ATLASSERT si *h* es NULL. No se realiza ninguna otra comprobación en cuanto a la validez del mango.

## <a name="chandlechandle"></a><a name="chandle"></a>CHandle::CHandle

El constructor.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Un identificador `CHandle`existente o .

### <a name="remarks"></a>Observaciones

Crea un `CHandle` nuevo objeto, opcionalmente `CHandle` mediante un identificador u objeto existente.

## <a name="chandlechandle"></a><a name="dtor"></a>CHandle::-CHandle

Destructor.

```
~CHandle() throw();
```

### <a name="remarks"></a>Observaciones

Libera el `CHandle` objeto llamando a [CHandle::Close](#close).

## <a name="chandleclose"></a><a name="close"></a>CHandle::Cerrar

Llame a este `CHandle` método para cerrar un objeto.

```cpp
void Close() throw();
```

### <a name="remarks"></a>Observaciones

Cierra un identificador de objeto abierto. Si el identificador es NULL, que `Close` será el caso si ya se ha llamado, se generará un ATLASSERT en compilaciones de depuración.

## <a name="chandledetach"></a><a name="detach"></a>CHandle::Detach

Llame a este método para `CHandle` separar un identificador de un objeto.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador que se está desasociando.

### <a name="remarks"></a>Observaciones

Libera la propiedad del identificador.

## <a name="chandlem_h"></a><a name="m_h"></a>CHandle::m_h

La variable miembro que almacena el identificador.

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a>CHandle::operador ?

El operador de asignación.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Parámetros

*H*<br/>
`CHandle`tomará la propiedad de la manija *h*.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia `CHandle` al nuevo objeto.

### <a name="remarks"></a>Observaciones

Si `CHandle` el objeto contiene actualmente un identificador, se cerrará. El `CHandle` objeto que se pasa tendrá su referencia de identificador establecida en NULL. Esto garantiza `CHandle` que dos objetos nunca contendrán el mismo identificador activo.

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a>CHandle::operador HANDLE

Devuelve el valor del identificador almacenado.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve el valor almacenado en [CHandle::m_h](#m_h).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
