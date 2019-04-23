---
title: CMFCFontInfo (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: 930aceb4514195f0e844c35d326b52d9cd8d31fa
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781333"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo (clase)

La `CMFCFontInfo` clase describe el nombre y otros atributos de una fuente.

## <a name="syntax"></a>Sintaxis

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCFontInfo`|Construye un objeto `CMFCFontInfo`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|Recupera los nombres de una fuente y el carácter concatenados conjunto (script).|

### <a name="data-members"></a>Miembros de datos

|Name|Descripción|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Un valor que especifica el juego de caracteres (script) asociado a la fuente.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Un valor que especifica el cabeceo y la familia de la fuente.|
|[CMFCFontInfo::m_nType](#m_ntype)|Un valor que especifica el tipo de la fuente.|
|[CMFCFontInfo::m_strName](#m_strname)|El nombre de la fuente; Por ejemplo, **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|El nombre de un juego de caracteres (script) asociado a la fuente.|

## <a name="remarks"></a>Comentarios

Puede adjuntar un `CMFCFontInfo` objeto a un elemento de la [CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md) clase. Llame a la [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) método para recuperar un puntero a un `CMFCFontInfo` objeto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar los diversos miembros de la `CMFCFontInfo` clase. El ejemplo muestra cómo obtener un `CMFCFontInfo` objeto desde un `CMFCRibbonFontComboBox`y cómo tener acceso a sus variables locales. Este ejemplo forma parte de la [ejemplo de demostración de 2007 MSOffice](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox.h

##  <a name="cmfcfontinfo"></a>  CMFCFontInfo::CMFCFontInfo

Construye un objeto `CMFCFontInfo`.

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[in] El nombre de la fuente. Para obtener más información, consulte el `lfFaceName` miembro de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura.

*lpszScript*<br/>
[in] El nombre de la secuencia de comandos (juego de caracteres) de la fuente.

*nCharSet*<br/>
[in] Un valor que especifica el juego de caracteres (script) de la fuente. Para obtener más información, consulte el `lfCharSet` miembro de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura.

*nPitchAndFamily*<br/>
[in] Un valor que especifica el cabeceo y la familia de la fuente. Para obtener más información, consulte el `lfPitchAndFamily` miembro de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura.

*nType*<br/>
[in] Un valor que especifica el tipo de fuente. Este parámetro puede ser una combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.

*src*<br/>
[in] Existente `CMFCFontInfo` objeto cuyos miembros se usan para construir este `CMFCFontInfo` objeto.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Esta documentación utiliza los términos *juego de caracteres* y *script* indistintamente. Un *script*, que también se denomina es un sistema de escritura, es una colección de reglas para escribir estos caracteres en uno o varios idiomas y caracteres. El conjunto de caracteres que incluye el alfabeto y la puntuación que se usa en el script. Por ejemplo, alfabeto latino sirve para inglés se habla en Estados Unidos, y su alfabeto incluye los caracteres de la A Z. El `lfCharSet` miembro de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura especifica un juego de caracteres. Por ejemplo, el valor ANSI_CHARSET especifica el juego de caracteres ANSI, lo que incluye el alfabeto del alfabeto latino.

##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName

Recupera los nombres de una fuente y el carácter concatenados conjunto (script).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Valor devuelto

Una cadena que contiene el nombre de la fuente y el script.

### <a name="remarks"></a>Comentarios

Utilice este método para obtener el nombre completo de la fuente. Por ejemplo, si es el nombre de fuente **Arial** y la secuencia de comandos de la fuente es **cirílico**, este método devuelve "Arial (cirílico)".

##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet

Un valor que especifica el juego de caracteres (script) asociado a la fuente.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el *nCharSet* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily

Un valor que especifica el paso (tamaño de punto) y la familia (por ejemplo, serif, sans-serif y monospace) de la fuente.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el *nPitchAndFamily* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

Un valor que especifica el tipo de la fuente.

```
const int m_nType;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el *nLas* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

El nombre de la fuente: por ejemplo, **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el *lpszName* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

El nombre de un juego de caracteres (script) asociado a la fuente.

```
const CString m_strScript;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el *lpszScript* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox (clase)](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
