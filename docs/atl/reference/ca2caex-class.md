---
title: Clase CA2CAEX
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: e6c727993b2907aaa551421a5d2d23e372b68917
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319144"
---
# <a name="ca2caex-class"></a>Clase CA2CAEX

Esta clase es utilizada por las macros de conversión de cadenas CA2CTEX y CT2CAEX, y el typedef CA2CA.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer utilizado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|El constructor.|
|[CA2CAEX::-CA2CAEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2CAEX::operador LPCSTR](#operator_lpcstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, utilice CA2CTEX, CT2CAEX o CA2CA en su propio código.

Esta clase es segura de usar en bucles y no desbordará la pila. Las macros y clases de conversión de ATL utilizarán de forma predeterminada la página de código ANSI del subproceso actual para la conversión.

Las siguientes macros se basan en esta clase:

- CA2CTEX

- CT2CAEX

La siguiente typedef se basa en esta clase:

- CA2CA

Para obtener una explicación de estas macros de conversión de texto, vea Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

El constructor.

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
Sin usar en esta clase.

### <a name="remarks"></a>Observaciones

Crea el búfer necesario para la traducción.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX::-CA2CAEX

Destructor.

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX::operador LPCSTR

Operador de conversión.

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como tipo LPCSTR.

## <a name="see-also"></a>Consulte también

[Clase CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Clase CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Clase CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Clase CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
