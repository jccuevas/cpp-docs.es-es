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
ms.openlocfilehash: d1f960f8ec94b8e573490d4e708d4240b894b5ec
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297165"
---
# <a name="cw2cwex-class"></a>Clase CW2CWEX

Esta clase se utiliza por las macros de conversión de cadena CW2CTEX y CT2CWEX y la definición de tipo CW2W.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|El constructor.|
|[CW2CWEX::~CW2CWEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|

## <a name="remarks"></a>Comentarios

A menos que se requiere una funcionalidad adicional, use CW2CTEX, CT2CWEX o CW2W en el código.

Esta clase es segura utilizar en bucles y no desbordarán la pila. De forma predeterminada, las macros y clases de conversión de ATL usan la página de códigos ANSI del subproceso actual para la conversión.

Las macros siguientes se basan en esta clase:

- CW2CTEX

- CT2CWEX

La siguiente definición de tipo se basa en esta clase:

- CW2W

Para obtener una explicación de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

##  <a name="cw2cwex"></a>  CW2CWEX::CW2CWEX

El constructor.

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos. No se utiliza en esta clase.

### <a name="remarks"></a>Comentarios

Asigna el búfer usado en el proceso de traducción.

##  <a name="dtor"></a>  CW2CWEX::~CW2CWEX

Destructor.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Comentarios

Libera el búfer asignado.

##  <a name="m_psz"></a>  CW2CWEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPCWSTR m_psz;
```

##  <a name="operator_lpcwstr"></a>  CW2CWEX::operator LPCWSTR

Operador de conversión.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como un tipo LPCWSTR.

## <a name="see-also"></a>Vea también

[CA2AEX (clase)](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX (clase)](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX (clase)](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX (clase)](../../atl/reference/cw2aex-class.md)<br/>
[CW2WEX (clase)](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
