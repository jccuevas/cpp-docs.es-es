---
title: CMFCFontInfo (Clase)
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
ms.openlocfilehash: 6e87971e2afefc9cf1574abe951920c254dcd2ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367480"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo (Clase)

La `CMFCFontInfo` clase describe el nombre y otros atributos de una fuente.

## <a name="syntax"></a>Sintaxis

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCFontInfo`|Construye un objeto `CMFCFontInfo`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|Recupera los nombres concatenados de una fuente y su juego de caracteres (script).|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Valor que especifica el juego de caracteres (script) asociado a la fuente.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Valor que especifica el tono y la familia de la fuente.|
|[CMFCFontInfo::m_nType](#m_ntype)|Valor que especifica el tipo de fuente.|
|[CMFCFontInfo::m_strName](#m_strname)|El nombre de la fuente; por ejemplo, **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|El nombre de un juego de caracteres (script) asociado a la fuente.|

## <a name="remarks"></a>Observaciones

Puede asociar `CMFCFontInfo` un objeto a un elemento de la [CMFCToolBarFontComboBox clase.](../../mfc/reference/cmfctoolbarfontcombobox-class.md) Llame a la [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) método `CMFCFontInfo` para recuperar un puntero a un objeto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCFontInfo` cómo utilizar varios miembros de la clase. En el ejemplo se `CMFCFontInfo` muestra cómo `CMFCRibbonFontComboBox`obtener un objeto de un archivo , y cómo tener acceso a sus variables locales. Este ejemplo forma parte del ejemplo de demostración de [MSOffice 2007.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox.h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

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
[en] El nombre de la fuente. Para obtener más `lfFaceName` información, consulte el miembro de la [estructura LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*lpszScript*<br/>
[en] El nombre del script (conjunto de caracteres) de la fuente.

*nCharSet*<br/>
[en] Valor que especifica el juego de caracteres (script) de la fuente. Para obtener más `lfCharSet` información, consulte el miembro de la [estructura LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nPitchAndFamily*<br/>
[en] Valor que especifica el tono y la familia de la fuente. Para obtener más `lfPitchAndFamily` información, consulte el miembro de la [estructura LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nType*<br/>
[en] Valor que especifica el tipo de fuente. Este parámetro puede ser una combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.

*src*<br/>
[en] Objeto `CMFCFontInfo` existente cuyos miembros `CMFCFontInfo` se utilizan para construir este objeto.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Esta documentación utiliza los términos juego de *caracteres* y *script* indistintamente. Un *script,* que también se conoce como sistema de escritura, es una colección de caracteres y reglas para escribir esos caracteres en uno o más idiomas. La colección de caracteres incluye el alfabeto y la puntuación utilizada en ese script. Por ejemplo, el alfabeto latino se utiliza para inglés tal como se habla en los Estados Unidos, y su alfabeto incluye los caracteres de la A a la Z. El `lfCharSet` miembro de la [estructura LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) especifica un juego de caracteres. Por ejemplo, el valor ANSI_CHARSET especifica el juego de caracteres ANSI, que incluye el alfabeto de la escritura latina.

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFCFontInfo::GetFullName

Recupera los nombres concatenados de una fuente y su juego de caracteres (script).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena que contiene el nombre de fuente y el script.

### <a name="remarks"></a>Observaciones

Utilice este método para obtener el nombre completo de la fuente. Por ejemplo, si el nombre de fuente es **Arial** y el script de fuente es **cirílico,** este método devuelve "Arial (cirílico)".

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet

Valor que especifica el juego de caracteres (script) asociado a la fuente.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea el *nCharSet* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily

Valor que especifica el tono (tamaño del punto) y la familia (por ejemplo, serif, sans-serif y monoespacio) de la fuente.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea el *nPitchAndFamily* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a>CMFCFontInfo::m_nType

Valor que especifica el tipo de fuente.

```
const int m_nType;
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea el *nType* parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a>CMFCFontInfo::m_strName

El nombre de la fuente: por ejemplo, **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea el *parámetro lpszName* del constructor [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a>CMFCFontInfo::m_strScript

El nombre de un juego de caracteres (script) asociado a la fuente.

```
const CString m_strScript;
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea el parámetro *lpszScript* del constructor [CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox (Clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox (Clase)](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
