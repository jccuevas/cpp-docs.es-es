---
title: Clase CW2AEX
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 849cbe5c26d7c7af7a8925a26057b5777554471d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330453"
---
# <a name="cw2aex-class"></a>Clase CW2AEX

Esta clase es utilizada por las macros de conversión de cadenas CT2AEX, CW2TEX, CW2CTEX y CT2CAEX, y el typedef CW2A.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer utilizado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|El constructor.|
|[CW2AEX::-CW2AEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2AEX::operador LPSTR](#operator_lpstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|El búfer estático, utilizado para almacenar la cadena convertida.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, utilice CT2AEX, CW2TEX, CW2CTEX, CT2CAEX o CW2A en su código.

Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, liberando la memoria cuando el objeto sale del ámbito. Esto garantiza que, a diferencia de las macros de conversión de texto disponibles en versiones anteriores de ATL, esta clase es segura de usar en bucles y que no desbordará la pila.

Si la clase intenta asignar memoria en el `AtlThrow` montón y se produce un error, llamará con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las macros y las clases de conversión ATL usan la página de códigos ANSI del subproceso actual para la conversión. Si desea invalidar ese comportamiento para una conversión específica, especifique la página de códigos como el segundo parámetro para el constructor de la clase.

Las siguientes macros se basan en esta clase:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

La siguiente typedef se basa en esta clase:

- CW2A

Para obtener una explicación de estas macros de conversión de texto, vea Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte Macros de conversión de cadenas [ATL y MFC](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

## <a name="cw2aexcw2aex"></a><a name="cw2aex"></a>CW2AEX::CW2AEX

El constructor.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos utilizada para realizar la conversión. Consulte la discusión de parámetros de página de códigos para la función de Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) para obtener más detalles.

### <a name="remarks"></a>Observaciones

Asigna el búfer utilizado en el proceso de traducción.

## <a name="cw2aexcw2aex"></a><a name="dtor"></a>CW2AEX::-CW2AEX

Destructor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="cw2aexm_psz"></a><a name="m_psz"></a>CW2AEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPSTR m_psz;
```

## <a name="cw2aexm_szbuffer"></a><a name="m_szbuffer"></a>CW2AEX::m_szBuffer

El búfer estático, utilizado para almacenar la cadena convertida.

```
char m_szBuffer[t_nBufferLength];
```

## <a name="cw2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CW2AEX::operador LPSTR

Operador de conversión.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como tipo LPSTR.

## <a name="see-also"></a>Consulte también

[Clase CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Clase CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Clase CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Clase CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
