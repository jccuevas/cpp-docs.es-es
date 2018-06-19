---
title: Clase CMFCFontInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9e4c1031ba06eaabe67418a018f95d689f71d1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368298"
---
# <a name="cmfcfontinfo-class"></a>Clase CMFCFontInfo
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
|[CMFCFontInfo::GetFullName](#getfullname)|Recupera los nombres concatenados de una fuente y el carácter del conjunto (script).|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Un valor que especifica el juego de caracteres (script) asociado a la fuente.|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Un valor que especifica el tono y la familia de la fuente.|  
|[CMFCFontInfo::m_nType](#m_ntype)|Un valor que especifica el tipo de la fuente.|  
|[CMFCFontInfo::m_strName](#m_strname)|El nombre de la fuente; Por ejemplo, **Arial**.|  
|[CMFCFontInfo::m_strScript](#m_strscript)|El nombre de un juego de caracteres (script) asociado a la fuente.|  
  
## <a name="remarks"></a>Comentarios  
 Puede adjuntar un `CMFCFontInfo` objeto a un elemento de la [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md) clase. Llame a la [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) método para recuperar un puntero a un `CMFCFontInfo` objeto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios miembros de la `CMFCFontInfo` clase. En el ejemplo se muestra cómo obtener un `CMFCFontInfo` objeto desde un `CMFCRibbonFontComboBox`y cómo obtener acceso a sus variables locales. Este ejemplo forma parte de la [ejemplo de demostración de 2007 MSOffice](../../visual-cpp-samples.md).  
  
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
 [in] `lpszName`  
 El nombre de la fuente. Para obtener más información, consulte el `lfFaceName` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura.  
  
 [in] `lpszScript`  
 El nombre de la secuencia de comandos (juego de caracteres) de la fuente.  
  
 [in] `nCharSet`  
 Un valor que especifica el juego de caracteres (script) de la fuente. Para obtener más información, consulte el `lfCharSet` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura.  
  
 [in] `nPitchAndFamily`  
 Un valor que especifica el tono y la familia de la fuente. Para obtener más información, consulte el `lfPitchAndFamily` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura.  
  
 [in] `nType`  
 Un valor que especifica el tipo de fuente. Este parámetro puede ser una combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.  
  
 [in] `src`  
 Existente `CMFCFontInfo` objeto cuyos miembros se utilizan para construir este `CMFCFontInfo` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Esta documentación, utilizan los términos *juego de caracteres* y *script* indistintamente. A *secuencia de comandos*, que también se denomina es un sistema de escritura, es una colección de reglas para escribir los caracteres en uno o más idiomas y caracteres. El conjunto de caracteres que incluye el alfabeto y puntuación que se usa en el script. Por ejemplo, alfabeto latino se usa para inglés como se habla en Estados Unidos y su alfabeto incluye los caracteres de la A la Z. El `lfCharSet` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura especifica un juego de caracteres. Por ejemplo, el valor `ANSI_CHARSET` especifica la [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] juego de caracteres, que incluye el alfabeto del alfabeto latino.  
  
##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName  
 Recupera los nombres concatenados de una fuente y el carácter del conjunto (script).  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena que contiene el nombre de la fuente y el script.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para obtener el nombre completo de la fuente. Por ejemplo, si es el nombre de la fuente es `Arial` y la secuencia de comandos de la fuente es `Cyrillic`, este método devuelve "Arial (cirílico)".  
  
##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet  
 Un valor que especifica el juego de caracteres (script) asociado a la fuente.  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `nCharSet` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily  
 Un valor que especifica el tono (tamaño de punto) y la familia (por ejemplo, serif, sans-serif y monospace) de la fuente.  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `nPitchAndFamily` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType  
 Un valor que especifica el tipo de la fuente.  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `nType` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="m_strname"></a>  CMFCFontInfo::m_strName  
 El nombre de la fuente: por ejemplo, **Arial**.  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `lpszName` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript  
 El nombre de un juego de caracteres (script) asociado a la fuente.  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `lpszScript` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox (clase)](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
