---
title: Clase CMFCFontInfo
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
ms.openlocfilehash: a27606b494b13cd7b50f01b38fa95a918bacc7aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505270"
---
# <a name="cmfcfontinfo-class"></a>Clase CMFCFontInfo

La `CMFCFontInfo` clase describe el nombre y otros atributos de una fuente.

## <a name="syntax"></a>Sintaxis

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCFontInfo`|Construye un objeto `CMFCFontInfo`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|Recupera los nombres concatenados de una fuente y su juego de caracteres (Script).|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Valor que especifica el juego de caracteres (Script) asociado a la fuente.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Valor que especifica el paso y la familia de la fuente.|
|[CMFCFontInfo::m_nType](#m_ntype)|Valor que especifica el tipo de la fuente.|
|[CMFCFontInfo::m_strName](#m_strname)|Nombre de la fuente; por ejemplo, **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Nombre de un juego de caracteres (Script) asociado a la fuente.|

## <a name="remarks"></a>Comentarios

Puede adjuntar `CMFCFontInfo` un objeto a un elemento de la clase [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) . Llame al método [CMFCToolBarFontComboBox:: GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) para recuperar un puntero a un `CMFCFontInfo` objeto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar varios miembros de `CMFCFontInfo` la clase. En el ejemplo se muestra cómo obtener `CMFCFontInfo` un objeto `CMFCRibbonFontComboBox`de y cómo obtener acceso a sus variables locales. Este ejemplo forma parte del [ejemplo de demostración de MSOffice 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox. h

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
de Nombre de la fuente. Para obtener más información, vea `lfFaceName` el miembro de la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*lpszScript*<br/>
de Nombre del script (juego de caracteres) de la fuente.

*nCharSet*<br/>
de Valor que especifica el juego de caracteres (Script) de la fuente. Para obtener más información, vea `lfCharSet` el miembro de la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nPitchAndFamily*<br/>
de Valor que especifica el paso y la familia de la fuente. Para obtener más información, vea `lfPitchAndFamily` el miembro de la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nType*<br/>
de Valor que especifica el tipo de fuente. Este parámetro puede ser una combinación bit a bit (o) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.

*src*<br/>
de Objeto existente `CMFCFontInfo` cuyos miembros se utilizan para construir este `CMFCFontInfo` objeto.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

En esta documentación se usa el *juego de caracteres* y el *script* indistintamente. Un *script*, que también se conoce como sistema de escritura, es una colección de caracteres y reglas para escribir esos caracteres en uno o varios idiomas. La colección de caracteres incluye el alfabeto y la puntuación utilizados en el script. Por ejemplo, el script Latino se utiliza para inglés mientras se habla en el Estados Unidos, y su alfabeto incluye los caracteres de la A a la Z. El `lfCharSet` miembro de la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) especifica un juego de caracteres. Por ejemplo, el valor ANSI_CHARSET especifica el juego de caracteres ANSI, que incluye el alfabeto del alfabeto latino.

##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName

Recupera los nombres concatenados de una fuente y su juego de caracteres (Script).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena que contiene el nombre y el script de la fuente.

### <a name="remarks"></a>Comentarios

Utilice este método para obtener el nombre completo de la fuente. Por ejemplo, si el nombre de la fuente es **Arial** y el script de la fuente es **cirílico**, este método devuelve "Arial (cirílico)".

##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet

Valor que especifica el juego de caracteres (Script) asociado a la fuente.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea el parámetro *nCharSet* del constructor [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily

Valor que especifica el tono (tamaño de punto) y la familia (por ejemplo, Serif, Sans-Serif y monoespacio) de la fuente.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea el parámetro *nPitchAndFamily* del constructor [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

Valor que especifica el tipo de la fuente.

```
const int m_nType;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea el parámetro *ndeclaraciones* del constructor [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

Nombre de la fuente: por ejemplo, **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea el parámetro *lpszName* del constructor [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

Nombre de un juego de caracteres (Script) asociado a la fuente.

```
const CString m_strScript;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea el parámetro *lpszScript* del constructor [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox (clase)](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
