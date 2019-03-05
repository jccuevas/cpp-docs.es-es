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
ms.openlocfilehash: 88389d4fe913a31fce43e3c8cc95605f99701695
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326444"
---
# <a name="ca2caex-class"></a>Clase CA2CAEX

Esta clase se usa macros de conversión de cadena CA2CTEX y CT2CAEX y la definición de tipo CA2CA.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|El constructor.|
|[CA2CAEX::~CA2CAEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|

## <a name="remarks"></a>Comentarios

A menos que se requiere una funcionalidad adicional, use CA2CTEX, CT2CAEX o CA2CA en su propio código.

Esta clase es segura utilizar en bucles y no desbordarán la pila. Las macros y clases de conversión de ATL utilizarán de forma predeterminada la página de código ANSI del subproceso actual para la conversión.

Las macros siguientes se basan en esta clase:

- CA2CTEX

- CT2CAEX

La siguiente definición de tipo se basa en esta clase:

- CA2CA

Para obtener una explicación de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

##  <a name="ca2caex"></a>  CA2CAEX::CA2CAEX

El constructor.

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
No se usan en esta clase.

### <a name="remarks"></a>Comentarios

Crea el búfer necesario para la traducción.

##  <a name="dtor"></a>  CA2CAEX::~CA2CAEX

Destructor.

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>Comentarios

Libera el búfer asignado.

##  <a name="m_psz"></a>  CA2CAEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPCSTR m_psz;
```

##  <a name="operator_lpcstr"></a>  CA2CAEX::operator LPCSTR

Operador de conversión.

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como un tipo LPCSTR.

## <a name="see-also"></a>Vea también

[CA2AEX (clase)](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX (clase)](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX (clase)](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX (clase)](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX (clase)](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
