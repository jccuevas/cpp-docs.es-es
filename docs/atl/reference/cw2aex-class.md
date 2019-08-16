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
ms.openlocfilehash: 4dda1cb9e54c44f7940475660bc629192b9ead61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496268"
---
# <a name="cw2aex-class"></a>Clase CW2AEX

Esta clase la usan las macros de conversión de cadenas CT2AEX, CW2TEX, CW2CTEX y CT2CAEX, y la definición de tipo CW2A.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
Tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|El constructor.|
|[CW2AEX::~CW2AEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CW2AEX:: Operator LPSTR](#operator_lpstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Miembro de datos que almacena la cadena de origen.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Búfer estático, que se usa para almacenar la cadena convertida.|

## <a name="remarks"></a>Comentarios

A menos que se requiera funcionalidad adicional, use CT2AEX, CW2TEX, CW2CTEX, CT2CAEX o CW2A en el código.

Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, liberando la memoria cuando el objeto sale del ámbito. Esto garantiza que, a diferencia de las macros de conversión de texto disponibles en versiones anteriores de ATL, esta clase se puede usar de forma segura en los bucles y no desbordar la pila.

Si la clase intenta asignar memoria en el montón y se produce un error, llamará `AtlThrow` a con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las clases de conversión de ATL y las macros usan la página de códigos ANSI del subproceso actual para la conversión. Si desea invalidar ese comportamiento para una conversión concreta, especifique la página de códigos como el segundo parámetro para el constructor de la clase.

Las macros siguientes se basan en esta clase:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

La definición de tipo siguiente se basa en esta clase:

- CW2A

Para obtener una descripción de estas macros de conversión de texto, vea [ATL y macros de conversión de cadenas de MFC](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Vea [macros de conversión de cadenas de ATL y MFC](string-conversion-macros.md) para obtener un ejemplo de cómo usar estas macros de conversión de cadenas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv. h

##  <a name="cw2aex"></a>  CW2AEX::CW2AEX

El constructor.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
Cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos que se usa para realizar la conversión. Vea la descripción del parámetro de la página de códigos de la función Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) para obtener más detalles.

### <a name="remarks"></a>Comentarios

Asigna el búfer usado en el proceso de traducción.

##  <a name="dtor"></a>  CW2AEX::~CW2AEX

Destructor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Comentarios

Libera el búfer asignado.

##  <a name="m_psz"></a>  CW2AEX::m_psz

Miembro de datos que almacena la cadena de origen.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer

Búfer estático, que se usa para almacenar la cadena convertida.

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>CW2AEX:: Operator LPSTR

Operador de conversión.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como tipo LPSTR.

## <a name="see-also"></a>Vea también

[CA2AEX (clase)](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX (clase)](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX (clase)](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX (clase)](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX (clase)](../../atl/reference/cw2wex-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
