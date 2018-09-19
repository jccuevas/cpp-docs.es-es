---
title: CHandle (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99d8cd4b076e5de35ffcb957a05f3c680bc82214
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106810"
---
# <a name="chandle-class"></a>CHandle (clase)

Esta clase proporciona métodos para crear y usar un identificador de objeto.

## <a name="syntax"></a>Sintaxis

```
class CHandle
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|El constructor.|
|[CHandle:: ~ CHandle](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHandle::Attach](#attach)|Llame a este método para adjuntar el `CHandle` objeto en un identificador existente.|
|[CHandle::Close](#close)|Llame a este método para cerrar un `CHandle` objeto.|
|[CHandle::Detach](#detach)|Llame a este método para desasociar un identificador de un `CHandle` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CHandle::operator identificador](#operator_handle)|Devuelve el valor del identificador almacenado.|
|[CHandle::operator =](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CHandle::m_h](#m_h)|La variable de miembro que almacena el identificador.|

## <a name="remarks"></a>Comentarios

Un `CHandle` cada vez que se requiere un identificador de objeto que se puede usar: la principal diferencia es que el `CHandle` automáticamente se eliminará el objeto.

> [!NOTE]
>  Algunas funciones de la API utilizará NULL como un identificador vacío o no válido, mientras que otros usan INVALID_HANDLE_VALUE. `CHandle` solo usa NULL y trata INVALID_HANDLE_VALUE como un identificador real. Si se llama a una API que puede devolver INVALID_HANDLE_VALUE, debe comprobar este valor antes de llamar a [CHandle::Attach](#attach) o pasarlo a la `CHandle` constructor y en su lugar, pase NULL.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="attach"></a>  CHandle::Attach

Llame a este método para adjuntar el `CHandle` objeto en un identificador existente.

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Parámetros

*h*<br/>
`CHandle` tomará posesión del controlador *h*.

### <a name="remarks"></a>Comentarios

Asigna el `CHandle` de objeto para el *h* controlar. En las compilaciones depura, se generará una ATLASSERT si *h* es NULL. Se realiza ninguna otra comprobación validez del identificador.

##  <a name="chandle"></a>  CHandle::CHandle

El constructor.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Un identificador existente o `CHandle`.

### <a name="remarks"></a>Comentarios

Crea un nuevo `CHandle` objeto, utilizando opcionalmente un identificador existente o `CHandle` objeto.

##  <a name="dtor"></a>  CHandle:: ~ CHandle

Destructor.

```
~CHandle() throw();
```

### <a name="remarks"></a>Comentarios

Libera el `CHandle` objeto mediante una llamada a [CHandle::Close](#close).

##  <a name="close"></a>  CHandle::Close

Llame a este método para cerrar un `CHandle` objeto.

```
void Close() throw();
```

### <a name="remarks"></a>Comentarios

Cierra un identificador de objeto abierto. Si el identificador no es NULL, lo que será el caso si `Close` ya ha sido llamado, se generará un ATLASSERT en las compilaciones de depuración.

##  <a name="detach"></a>  CHandle::Detach

Llame a este método para desasociar un identificador de un `CHandle` objeto.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador que se va a separar.

### <a name="remarks"></a>Comentarios

Libera la propiedad del identificador.

##  <a name="m_h"></a>  CHandle::m_h

La variable de miembro que almacena el identificador.

```
HANDLE m_h;
```

##  <a name="operator_eq"></a>  CHandle::operator =

El operador de asignación.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Parámetros

*h*<br/>
`CHandle` tomará posesión del controlador *h*.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al nuevo `CHandle` objeto.

### <a name="remarks"></a>Comentarios

Si el `CHandle` objeto actualmente contiene un identificador, se cerrará. El `CHandle` de objeto que se pasa en tendrá su referencia de identificador establecido en NULL. Esto garantiza que dos `CHandle` objetos nunca contendrá el mismo identificador de activo.

##  <a name="operator_handle"></a>  CHandle::operator identificador

Devuelve el valor del identificador almacenado.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve el valor almacenado en [CHandle::m_h](#m_h).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
