---
title: Clase CD2DTextLayout
ms.date: 03/27/2019
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
ms.openlocfilehash: 9be4c1134e2f82ceb3af31cbeb1a7d55f4071777
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369025"
---
# <a name="cd2dtextlayout-class"></a>Clase CD2DTextLayout

Un contenedor para IDWriteTextLayout.

## <a name="syntax"></a>Sintaxis

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Construye un CD2DTextLayout objeto.|
|[CD2DTextLayout::-CD2DTextLayout](#_dtorcd2dtextlayout)|Destructor. Se llama cuando se destruye un objeto de diseño de texto D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextLayout::Create](#create)|Crea un CD2DTextLayout. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextLayout::Destroy](#destroy)|Destruye un objeto CD2DTextLayout. (Reemplaza [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextLayout::Get](#get)|Devuelve IDWriteTextLayout interfaz|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Copia el nombre de la familia de fuentes del texto en la posición especificada.|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Obtiene el nombre de configuración regional del texto en la posición especificada.|
|[CD2DTextLayout::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextLayout::ReCreate](#recreate)|Vuelve a crear un CD2DTextLayout. (Reemplaza [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Establece el nombre de familia de fuentes terminada en null para el texto dentro de un intervalo de texto especificado|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Establece el nombre de la configuración regional para el texto dentro de un intervalo de texto especificado|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextLayout::operator IDWriteTextLayout*](#operator_idwritetextlayout_star)|Devuelve IDWriteTextLayout interfaz|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Un puntero a un IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a>CD2DTextLayout::-CD2DTextLayout

Destructor. Se llama cuando se destruye un objeto de diseño de texto D2D.

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a>CD2DTextLayout::CD2DTextLayout

Construye un CD2DTextLayout objeto.

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*strText*<br/>
Un CString objeto que contiene la cadena para crear un nuevo CD2DTextLayout objeto desde.

*textFormat*<br/>
Un CString objeto que contiene el formato que se aplicará a la cadena.

*sizeMax*<br/>
El tamaño del cuadro de diseño.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a>CD2DTextLayout::Create

Crea un CD2DTextLayout.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a>CD2DTextLayout::Destroy

Destruye un objeto CD2DTextLayout.

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a>CD2DTextLayout::Get

Devuelve IDWriteTextLayout interfaz

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz IDWriteTextLayout o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextLayout::GetFontFamilyName

Copia el nombre de la familia de fuentes del texto en la posición especificada.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parámetros

*currentPosition*<br/>
La posición del texto a examinar.

*Textrange*<br/>
El intervalo de texto que tiene el mismo formato que el texto en la posición especificada por currentPosition. Esto significa que la ejecución tiene el formato exacto como la posición especificada, incluido, entre otros, el nombre de la familia de fuentes.

### <a name="return-value"></a>Valor devuelto

CString objeto que contiene el nombre de familia de fuentes actual.

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a>CD2DTextLayout::GetLocaleName

Obtiene el nombre de configuración regional del texto en la posición especificada.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parámetros

*currentPosition*<br/>
La posición del texto que se debe inspeccionar.

*Textrange*<br/>
El intervalo de texto que tiene el mismo formato que el texto en la posición especificada por currentPosition. Esto significa que la ejecución tiene el formato exacto como la posición especificada, incluyendo pero no limitado al nombre de la configuración regional.

### <a name="return-value"></a>Valor devuelto

CString objeto que contiene el nombre de configuración regional actual.

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a>CD2DTextLayout::IsValid

Comprueba la validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el recurso es válido; de lo contrario FALSO.

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a>CD2DTextLayout::m_pTextLayout

Un puntero a un IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a>CD2DTextLayout::operator IDWriteTextLayout*

Devuelve IDWriteTextLayout interfaz

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz IDWriteTextLayout o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a>CD2DTextLayout::ReCreate

Vuelve a crear un CD2DTextLayout.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a>CD2DTextLayout::SetFontFamilyName

Establece el nombre de familia de fuentes terminada en null para el texto dentro de un intervalo de texto especificado

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parámetros

*pwzFontFamilyName*<br/>
El nombre de familia de fuentes que se aplica a toda la cadena de texto dentro del intervalo especificado por textRange

*Textrange*<br/>
Rango de texto al que se aplica este cambio

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a>CD2DTextLayout::SetLocaleName

Establece el nombre de la configuración regional para el texto dentro de un intervalo de texto especificado

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parámetros

*pwzLocaleName*<br/>
Una cadena de nombre de configuración regional terminada en null

*Textrange*<br/>
Rango de texto al que se aplica este cambio

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
