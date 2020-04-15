---
title: Clase CA2AEX
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: 4f8b9f91e9bc499523fe3484bc76325e2efb8140
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319180"
---
# <a name="ca2aex-class"></a>Clase CA2AEX

Esta clase es utilizada por las macros de conversión de cadenas CA2TEX y CT2AEX, y el typedef CA2A.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer utilizado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|El constructor.|
|[CA2AEX::-CA2AEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2AEX::operador LPSTR](#operator_lpstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2AEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|
|[CA2AEX::m_szBuffer](#m_szbuffer)|El búfer estático, utilizado para almacenar la cadena convertida.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, utilice CA2TEX, CT2AEX o CA2A en su propio código.

Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, liberando la memoria cuando el objeto sale del ámbito. Esto garantiza que, a diferencia de las macros de conversión de texto disponibles en versiones anteriores de ATL, esta clase es segura de usar en bucles y que no desbordará la pila.

Si la clase intenta asignar memoria en el `AtlThrow` montón y se produce un error, llamará con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las macros y las clases de conversión ATL usan la página de códigos ANSI del subproceso actual para la conversión.

Las siguientes macros se basan en esta clase:

- CA2TEX

- CT2AEX

La siguiente typedef se basa en esta clase:

- CA2A

Para obtener una explicación de estas macros de conversión de texto, vea Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

El constructor.

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
Sin usar en esta clase.

### <a name="remarks"></a>Observaciones

Crea el búfer necesario para la traducción.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX::-CA2AEX

Destructor.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX::m_szBuffer

El búfer estático, utilizado para almacenar la cadena convertida.

```
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX::operador LPSTR

Operador de conversión.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como tipo LPSTR.

## <a name="see-also"></a>Consulte también

[Clase CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Clase CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Clase CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Clase CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
