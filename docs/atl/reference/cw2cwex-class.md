---
title: Clase CW2CWEX
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 07dd0319586054403d8ed0c8efc813b4061e355a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330431"
---
# <a name="cw2cwex-class"></a>Clase CW2CWEX

Esta clase es utilizada por las macros de conversión de cadenas CW2CTEX y CT2CWEX, y el typedef CW2W.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer utilizado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|El constructor.|
|[CW2CWEX::-CW2CWEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2CWEX::operador LPCWSTR](#operator_lpcwstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, utilice CW2CTEX, CT2CWEX o CW2W en el código.

Esta clase es segura de usar en bucles y no desbordará la pila. De forma predeterminada, las macros y las clases de conversión ATL usan la página de códigos ANSI del subproceso actual para la conversión.

Las siguientes macros se basan en esta clase:

- CW2CTEX

- CT2CWEX

La siguiente typedef se basa en esta clase:

- CW2W

Para obtener una explicación de estas macros de conversión de texto, vea Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX::CW2CWEX

El constructor.

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos. No se usa en esta clase.

### <a name="remarks"></a>Observaciones

Asigna el búfer utilizado en el proceso de traducción.

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX::-CW2CWEX

Destructor.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a>CW2CWEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::operador LPCWSTR

Operador de conversión.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como tipo LPCWSTR.

## <a name="see-also"></a>Consulte también

[Clase CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Clase CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Clase CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Clase CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Clase CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
