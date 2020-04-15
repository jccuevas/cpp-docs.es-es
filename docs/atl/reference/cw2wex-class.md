---
title: Clase CW2WEX
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: b116775a595f9fb3612d46e19526cf1396f85002
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330349"
---
# <a name="cw2wex-class"></a>Clase CW2WEX

Esta clase es utilizada por las macros de conversión de cadenas CW2TEX y CT2WEX, y el typedef CW2W.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer utilizado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|El constructor.|
|[CW2WEX::-CW2WEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2WEX::operador LPWSTR](#operator_lpwstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|El búfer estático, utilizado para almacenar la cadena convertida.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, utilice CW2TEX, CT2WEX o CW2W en el código.

Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, liberando la memoria cuando el objeto sale del ámbito. Esto garantiza que, a diferencia de las macros de conversión de texto disponibles en versiones anteriores de ATL, esta clase es segura de usar en bucles y que no desbordará la pila.

Si la clase intenta asignar memoria en el `AtlThrow` montón y se produce un error, llamará con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las macros y las clases de conversión ATL usan la página de códigos ANSI del subproceso actual para la conversión.

Las siguientes macros se basan en esta clase:

- CW2TEX

- CT2WEX

La siguiente typedef se basa en esta clase:

- CW2W

Para obtener una explicación de estas macros de conversión de texto, vea Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

## <a name="cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX::CW2WEX

El constructor.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos. No se usa en esta clase.

### <a name="remarks"></a>Observaciones

Crea el búfer necesario para la traducción.

## <a name="cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX::-CW2WEX

El destructor.

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="cw2wexm_psz"></a><a name="m_psz"></a>CW2WEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPWSTR m_psz;
```

## <a name="cw2wexm_szbuffer"></a><a name="m_szbuffer"></a>CW2WEX::m_szBuffer

El búfer estático, utilizado para almacenar la cadena convertida.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX::operador LPWSTR

Operador de reparto.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como tipo LPWSTR.

## <a name="see-also"></a>Consulte también

[Clase CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Clase CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Clase CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Clase CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
