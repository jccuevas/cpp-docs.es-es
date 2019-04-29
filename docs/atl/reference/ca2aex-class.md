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
ms.openlocfilehash: 712e663ab58e2c9de4e2f25090b84b35d0bced71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247643"
---
# <a name="ca2aex-class"></a>Clase CA2AEX

Esta clase se utiliza por las macros de conversión de cadena CA2TEX y CT2AEX y la definición de tipo CA2A.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|El constructor.|
|[CA2AEX::~CA2AEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CA2AEX::operator LPSTR](#operator_lpstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CA2AEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|
|[CA2AEX::m_szBuffer](#m_szbuffer)|El búfer estático, utilizado para almacenar la cadena convertida.|

## <a name="remarks"></a>Comentarios

A menos que se requiere una funcionalidad adicional, use CA2TEX, CT2AEX o CA2A en su propio código.

Esta clase contiene un búfer estático de tamaño fijo que se usa para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, libere la memoria cuando el objeto queda fuera del ámbito. Esto garantiza que, a diferencia del texto macros de conversión disponibles en versiones anteriores de ATL, esta clase es segura para el uso en bucles y que no desbordarán la pila.

Si la clase intenta asignar memoria en el montón y se produce un error, llamará a `AtlThrow` con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las macros y clases de conversión de ATL usan la página de códigos ANSI del subproceso actual para la conversión.

Las macros siguientes se basan en esta clase:

- CA2TEX

- CT2AEX

La siguiente definición de tipo se basa en esta clase:

- CA2A

Para obtener una explicación de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

##  <a name="ca2aex"></a>  CA2AEX::CA2AEX

El constructor.

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
No se usan en esta clase.

### <a name="remarks"></a>Comentarios

Crea el búfer necesario para la traducción.

##  <a name="dtor"></a>  CA2AEX::~CA2AEX

Destructor.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Comentarios

Libera el búfer asignado.

##  <a name="m_psz"></a>  CA2AEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CA2AEX::m_szBuffer

El búfer estático, utilizado para almacenar la cadena convertida.

```
char m_szBuffer[ t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CA2AEX::operator LPSTR

Operador de conversión.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como un tipo LPSTR.

## <a name="see-also"></a>Vea también

[CA2CAEX (clase)](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX (clase)](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX (clase)](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX (clase)](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX (clase)](../../atl/reference/cw2wex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
