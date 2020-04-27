---
title: Clase CAtlException
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: f09d9b2f46233cf356f5ade8a5b90e08a213d276
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168207"
---
# <a name="catlexception-class"></a>Clase CAtlException

Esta clase define una excepción ATL.

## <a name="syntax"></a>Sintaxis

```cpp
class CAtlException
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|El constructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlException:: Operator HRESULT](#operator_hresult)|Convierte el objeto actual en un valor HRESULT.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlException:: m_hr](#m_hr)|Variable de tipo HRESULT creada por el objeto y utilizada para almacenar la condición de error.|

## <a name="remarks"></a>Observaciones

Un `CAtlException` objeto representa una condición de excepción relacionada con una operación ATL. La `CAtlException` clase incluye un miembro de datos público que almacena el código de estado que indica el motivo de la excepción y un operador de conversión que le permite tratar la excepción como si fuera un HRESULT.

En general, llamará `AtlThrow` en lugar de crear un `CAtlException` objeto directamente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlexcept. h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

El constructor.

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parámetros

*hr*<br/>
Código de error HRESULT.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException:: Operator HRESULT

Convierte el objeto actual en un valor HRESULT.

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException:: m_hr

El miembro de datos HRESULT.

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>Observaciones

Miembro de datos que almacena la condición de error. El valor HRESULT lo establece el constructor, [CAtlException:: CAtlException](#catlexception).

## <a name="see-also"></a>Consulte también

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
