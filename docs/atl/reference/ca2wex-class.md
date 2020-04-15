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
ms.openlocfilehash: c9123e163ca828fa71fe217e46537ceb18e6f549
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319127"
---
# <a name="ca2wex-class"></a>Clase CA2WEX

Esta clase es utilizada por las macros de conversión de cadenas CA2TEX, CA2CTEX, CT2WEX y CT2CWEX, y la typedef CA2W.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer utilizado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|El constructor.|
|[CA2WEX::-CA2WEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2WEX::operador LPWSTR](#operator_lpwstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|
|[CA2WEX::m_szBuffer](#m_szbuffer)|El búfer estático, utilizado para almacenar la cadena convertida.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, utilice CA2TEX, CA2CTEX, CT2WEX, CT2CWEX o CA2W en el código.

Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, liberando la memoria cuando el objeto sale del ámbito. Esto garantiza que, a diferencia de las macros de conversión de texto disponibles en versiones anteriores de ATL, esta clase es segura de usar en bucles y que no desbordará la pila.

Si la clase intenta asignar memoria en el `AtlThrow` montón y se produce un error, llamará con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las macros y las clases de conversión ATL usan la página de códigos ANSI del subproceso actual para la conversión. Si desea invalidar ese comportamiento para una conversión específica, especifique la página de códigos como el segundo parámetro para el constructor de la clase.

Las siguientes macros se basan en esta clase:

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

La siguiente typedef se basa en esta clase:

- CA2W

Para obtener una explicación de estas macros de conversión de texto, vea Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

El constructor.

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos utilizada para realizar la conversión. Consulte la discusión de parámetros de página de códigos para la función de Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) para obtener más detalles.

### <a name="remarks"></a>Observaciones

Asigna el búfer utilizado en el proceso de traducción.

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX::-CA2WEX

Destructor.

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX::m_szBuffer

El búfer estático, utilizado para almacenar la cadena convertida.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX::operador LPWSTR

Operador de conversión.

```
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
