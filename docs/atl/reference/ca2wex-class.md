---
title: Clase CA2WEX
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: a710034c5d94a8fb093a2b6a2a52373e2bab2d6d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168506"
---
# <a name="ca2wex-class"></a>Clase CA2WEX

Esta clase la usan las macros de conversión de cadenas CA2TEX, CA2CTEX, CT2WEX y CT2CWEX, y la definición de tipo CA2W.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template <int t_nBufferLength = 128>
class CA2WEX
```

### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
Tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es 128 bytes.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|El constructor.|
|[CA2WEX:: ~ CA2WEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2WEX:: Operator LPWSTR](#operator_lpwstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2WEX:: m_psz](#m_psz)|Miembro de datos que almacena la cadena de origen.|
|[CA2WEX:: m_szBuffer](#m_szbuffer)|Búfer estático, que se usa para almacenar la cadena convertida.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, use CA2TEX, CA2CTEX, CT2WEX, CT2CWEX o CA2W en el código.

Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, liberando la memoria cuando el objeto sale del ámbito. Esto garantiza que, a diferencia de las macros de conversión de texto disponibles en versiones anteriores de ATL, esta clase se puede usar de forma segura en los bucles y no desbordar la pila.

Si la clase intenta asignar memoria en el montón y se produce un error, llamará `AtlThrow` a con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las clases de conversión de ATL y las macros usan la página de códigos ANSI del subproceso actual para la conversión. Si desea invalidar ese comportamiento para una conversión concreta, especifique la página de códigos como el segundo parámetro para el constructor de la clase.

Las macros siguientes se basan en esta clase:

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

La definición de tipo siguiente se basa en esta clase:

- CA2W

Para obtener una descripción de estas macros de conversión de texto, vea [ATL y macros de conversión de cadenas de MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Vea [macros de conversión de cadenas de ATL y MFC](string-conversion-macros.md) para obtener un ejemplo de cómo usar estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv. h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

El constructor.

```cpp
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
Cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos que se usa para realizar la conversión. Vea la descripción del parámetro de la página de códigos de la función Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) para obtener más detalles.

### <a name="remarks"></a>Observaciones

Asigna el búfer usado en el proceso de traducción.

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX:: ~ CA2WEX

Destructor.

```cpp
~CA2WEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX:: m_psz

Miembro de datos que almacena la cadena de origen.

```cpp
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX:: m_szBuffer

Búfer estático, que se usa para almacenar la cadena convertida.

```cpp
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX:: Operator LPWSTR

Operador de conversión.

```cpp
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como tipo LPWSTR.

## <a name="see-also"></a>Consulte también

[Clase CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Clase CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Clase CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Clase CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
