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
ms.openlocfilehash: dfd8967d21005d83b38eeae36cfc147051d7beaf
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168532"
---
# <a name="ca2aex-class"></a>Clase CA2AEX

Esta clase la usan las macros de conversión de cadenas CA2TEX y CT2AEX, y la definición de tipo CA2A.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template <int t_nBufferLength = 128>
class CA2AEX
```

### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
Tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es 128 bytes.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|El constructor.|
|[CA2AEX:: ~ CA2AEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2AEX:: Operator LPSTR](#operator_lpstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CA2AEX:: m_psz](#m_psz)|Miembro de datos que almacena la cadena de origen.|
|[CA2AEX:: m_szBuffer](#m_szbuffer)|Búfer estático, que se usa para almacenar la cadena convertida.|

## <a name="remarks"></a>Observaciones

A menos que se requiera funcionalidad adicional, use CA2TEX, CT2AEX o CA2A en su propio código.

Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, liberando la memoria cuando el objeto sale del ámbito. Esto garantiza que, a diferencia de las macros de conversión de texto disponibles en versiones anteriores de ATL, esta clase se puede usar de forma segura en los bucles y no desbordar la pila.

Si la clase intenta asignar memoria en el montón y se produce un error, llamará `AtlThrow` a con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las clases de conversión de ATL y las macros usan la página de códigos ANSI del subproceso actual para la conversión.

Las macros siguientes se basan en esta clase:

- CA2TEX

- CT2AEX

La definición de tipo siguiente se basa en esta clase:

- CA2A

Para obtener una descripción de estas macros de conversión de texto, vea [ATL y macros de conversión de cadenas de MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Vea [macros de conversión de cadenas de ATL y MFC](string-conversion-macros.md) para obtener un ejemplo de cómo usar estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv. h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

El constructor.

```cpp
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
Cadena de texto que se va a convertir.

*nCodePage*<br/>
No se usa en esta clase.

### <a name="remarks"></a>Observaciones

Crea el búfer necesario para la traducción.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX:: ~ CA2AEX

Destructor.

```cpp
~CA2AEX() throw();
```

### <a name="remarks"></a>Observaciones

Libera el búfer asignado.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX:: m_psz

Miembro de datos que almacena la cadena de origen.

```cpp
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX:: m_szBuffer

Búfer estático, que se usa para almacenar la cadena convertida.

```cpp
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX:: Operator LPSTR

Operador de conversión.

```cpp
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
