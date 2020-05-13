---
title: Clase CD2DTextFormat
ms.date: 03/27/2019
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
ms.openlocfilehash: f7310fd3ca2ac34df7cc1a99cd5527ea8ba709c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369048"
---
# <a name="cd2dtextformat-class"></a>Clase CD2DTextFormat

Un contenedor para IDWriteTextFormat.

## <a name="syntax"></a>Sintaxis

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Construye un objeto CD2DTextFormat.|
|[CD2DTextFormat::-CD2DTextFormat](#_dtorcd2dtextformat)|Destructor. Se llama cuando se destruye un objeto de formato de texto D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextFormat::Create](#create)|Crea un CD2DTextFormat. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormat::Destroy](#destroy)|Destruye un objeto CD2DTextFormat. (Reemplaza [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextFormat::Get](#get)|Devuelve la interfaz IDWriteTextFormat|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Obtiene una copia del nombre de la familia de fuentes.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Obtiene una copia del nombre de configuración regional.|
|[CD2DTextFormat::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::ReCreate](#recreate)|Vuelve a crear un CD2DTextFormat. (Reemplaza [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextFormat::operator IDWriteTextFormat*](#operator_idwritetextformat_star)|Devuelve la interfaz IDWriteTextFormat|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Un puntero a un IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2DTextFormat::-CD2DTextFormat

Destructor. Se llama cuando se destruye un objeto de formato de texto D2D.

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2DTextFormat::CD2DTextFormat

Construye un objeto CD2DTextFormat.

```
CD2DTextFormat(
    CRenderTarget* pParentTarget,
    const CString& strFontFamilyName,
    FLOAT fontSize,
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,
    const CString& strFontLocale = _T(""),
    IDWriteFontCollection* pFontCollection = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*strFontFamilyName*<br/>
Un CString objeto que contiene el nombre de la familia de fuentes.

*Fontsize*<br/>
El tamaño lógico de la fuente en unidades DIP ("píxel independiente del dispositivo"). Un DIPequals 1/96 pulgadas.

*fontWeight*<br/>
Valor que indica el grosor de fuente del objeto de texto.

*fontStyle*<br/>
Valor que indica el estilo de fuente del objeto de texto.

*fontStretch*<br/>
Valor que indica la extensión de fuente para el objeto de texto.

*strFontLocale*<br/>
Un CString objeto que contiene el nombre de configuración regional.

*pFontCollection*<br/>
Puntero a un objeto de colección de fuentes. Cuando se trata de NULL, indica la colección de fuentes del sistema.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dtextformatcreate"></a><a name="create"></a>CD2DTextFormat::Create

Crea un CD2DTextFormat.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a>CD2DTextFormat::Destroy

Destruye un objeto CD2DTextFormat.

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a>CD2DTextFormat::Get

Devuelve la interfaz IDWriteTextFormat

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz IDWriteTextFormat o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextFormat::GetFontFamilyName

Obtiene una copia del nombre de la familia de fuentes.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Valor devuelto

CString objeto que contiene el nombre de familia de fuentes actual.

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2DTextFormat::GetLocaleName

Obtiene una copia del nombre de configuración regional.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Valor devuelto

CString objeto que contiene el nombre de configuración regional actual.

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2DTextFormat::IsValid

Comprueba la validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el recurso es válido; de lo contrario FALSO.

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a>CD2DTextFormat::m_pTextFormat

Un puntero a un IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2DTextFormat::operator IDWriteTextFormat*

Devuelve la interfaz IDWriteTextFormat

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz IDWriteTextFormat o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a>CD2DTextFormat::ReCreate

Vuelve a crear un CD2DTextFormat.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
