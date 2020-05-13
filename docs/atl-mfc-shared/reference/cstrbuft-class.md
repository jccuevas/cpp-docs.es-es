---
title: Clase CStrBufT
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 71d7b6f7d53e9613b1ac26013d73c1dbd1ef0aab
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746930"
---
# <a name="cstrbuft-class"></a>Clase CStrBufT

Esta clase proporciona limpieza `GetBuffer` `ReleaseBuffer` automática de `CStringT` recursos para y llamadas a un objeto existente.

## <a name="syntax"></a>Sintaxis

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parámetros

*TCharType*<br/>
El tipo de `CStrBufT` carácter de la clase. Puede ser uno de los siguientes:

- **char** (para cadenas de caracteres ANSI)

- **wchar_t** (para cadenas de caracteres Unicode)

- TCHAR (para cadenas de caracteres ANSI y Unicode)

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|PCXSTR|Un puntero a una cadena constante.|
|PXSTR|Un puntero a una cadena.|
|`StringType`|El tipo de cadena cuyo búfer debe ser manipulado por las especializaciones de esta plantilla de clase.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|El constructor del objeto de búfer de cadena.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|Establece la longitud del búfer de caracteres del objeto de cadena asociado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStrBufT::operador PCXSTR](#operator_pcxstr)|Recupera un puntero **const** al búfer de caracteres del objeto de cadena asociado.|
|[CStrBufT::operador PXSTR](#operator_pxstr)|Recupera un puntero al búfer de caracteres del objeto de cadena asociado.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|Determine automáticamente la nueva longitud de la cadena en el momento del lanzamiento.|
|[CStrBufT::SET_LENGTH](#set_length)|Establezca la longitud del objeto de cadena en el tiempo GetBuffer|

## <a name="remarks"></a>Observaciones

Esta clase se utiliza como clase contenedora para reemplazar llamadas a [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) y [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), o [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) y `ReleaseBuffer`.

Principalmente diseñado como una `CStrBufT` clase auxiliar, proporciona una manera conveniente para que un desarrollador trabaje con `ReleaseBuffer`el búfer de caracteres de un objeto de cadena sin preocuparse por cómo o cuándo llamar a . Esto es posible porque el objeto contenedor sale del ámbito de forma natural en el caso de una excepción o varias rutas de acceso de código de salida; haciendo que su destructor libere el recurso de cadena.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpstr.h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT::AUTO_LENGTH

Determine automáticamente la nueva longitud de la cadena en el momento del lanzamiento.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Observaciones

Determine automáticamente la nueva longitud de la cadena en el momento del lanzamiento. La cadena debe estar terminada en null.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

Construye un objeto de búfer.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
El objeto de cadena asociado al búfer. Normalmente, el desarrollador utilizará las definiciones `CStrBuf` de tipo predefinidas de (variante TCHAR), `CStrBufA` (variante**char)** y `CStrBufW` (**wchar_t** variante).

*nMinLength*<br/>
La longitud mínima del búfer de caracteres.

*dwFlags*<br/>
Determina si la longitud de la cadena se determina automáticamente. Puede ser uno de los siguientes:

- AUTO_LENGTH longitud de cadena se determina automáticamente cuando [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) se llama. La cadena debe estar terminada en null. Valor predeterminado.

- SET_LENGTH longitud de cadena se establece cuando [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) se llama.

### <a name="remarks"></a>Observaciones

Crea un búfer de cadena para el objeto de cadena asociado. Durante la construcción, [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) o [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) se llama.

Tenga en cuenta que el constructor de copias es **privado.**

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT::operador PCXSTR

Accede directamente a los caracteres almacenados en el objeto de cadena asociado como una cadena de estilo C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero de carácter a los datos de la cadena.

### <a name="remarks"></a>Observaciones

Llame a esta función para devolver un puntero al búfer de caracteres de un objeto de cadena. El contenido del objeto de cadena no se puede cambiar con este puntero.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT::operador PXSTR

Accede directamente a los caracteres almacenados en el objeto de cadena asociado como una cadena de estilo C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero de carácter a los datos de la cadena.

### <a name="remarks"></a>Observaciones

Llame a esta función para devolver un puntero al búfer de caracteres de un objeto de cadena. El desarrollador puede cambiar el contenido del objeto de cadena con este puntero.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::PCXSTR

Un puntero a una cadena constante.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::PXSTR

Un puntero a una cadena.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT::SET_LENGTH

Establezca la longitud del `GetBuffer` objeto de cadena en el momento.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Observaciones

Establezca la longitud del objeto de cadena en el momento GetBuffer.

Determina si [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) y [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) se llaman cuando se construye el objeto de búfer de cadena.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT::SetLength

Establece la longitud del búfer de caracteres.

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>Parámetros

*nLongitud*<br/>
La nueva longitud del búfer de caracteres del objeto de cadena.

> [!NOTE]
> Debe ser menor o igual que la longitud de `CStrBufT`búfer mínima especificada en el constructor de .

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer la longitud de la cadena representada por el objeto de búfer.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::StringType

El tipo de cadena cuyo búfer debe ser manipulado por las especializaciones de esta plantilla de clase.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Observaciones

`TCharType`es el tipo de carácter utilizado para especializar la plantilla de clase.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
