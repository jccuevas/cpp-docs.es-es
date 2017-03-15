---
title: Clase CMFCFontInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFontInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontInfo class
- CMFCFontInfo::CMFCFontInfo constructor
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ac1409bcfce389cbc334edd2b864f7505d7443c7
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfontinfo-class"></a>Clase CMFCFontInfo
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
|[CMFCFontInfo::GetFullName](#getfullname)|Recupera los nombres concatenados de una fuente y el carácter conjunto (script).|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Un valor que especifica el juego de caracteres (alfabeto) asociado a la fuente.|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Un valor que especifica el cabeceo y la familia de la fuente.|  
|[CMFCFontInfo::m_nType](#m_ntype)|Un valor que especifica el tipo de la fuente.|  
|[CMFCFontInfo::m_strName](#m_strname)|El nombre de la fuente; Por ejemplo, **Arial**.|  
|[CMFCFontInfo::m_strScript](#m_strscript)|El nombre de un juego de caracteres (alfabeto) asociado a la fuente.|  
  
## <a name="remarks"></a>Comentarios  
 Puede adjuntar un `CMFCFontInfo` objeto a un elemento de la [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md) clase. Llame a la [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) método para recuperar un puntero a un `CMFCFontInfo` objeto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar los diversos miembros de la `CMFCFontInfo` clase. En el ejemplo se muestra cómo obtener un `CMFCFontInfo` objeto a partir de un `CMFCRibbonFontComboBox`y cómo tener acceso a las variables locales. Este ejemplo forma parte de la [ejemplo de demostración de 2007 MSOffice](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo Nº&6;](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarfontcombobox.h  
  
##  <a name="a-namecmfcfontinfoa--cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo  
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
 Un valor que especifica el juego de caracteres (alfabeto) de la fuente. Para obtener más información, consulte el `lfCharSet` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura.  
  
 [in] `nPitchAndFamily`  
 Un valor que especifica el cabeceo y la familia de la fuente. Para obtener más información, consulte el `lfPitchAndFamily` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura.  
  
 [in] `nType`  
 Un valor que especifica el tipo de fuente. Este parámetro puede ser una combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.  
  
 [in] `src`  
 Existente `CMFCFontInfo` objeto cuyos miembros se utilizan para construir este `CMFCFontInfo` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Esta documentación utiliza los términos *juego de caracteres* y *secuencia de comandos* indistintamente. Un *secuencia de comandos*, que también es conocido como un sistema de escritura, es un conjunto de caracteres y las reglas para escribir los caracteres en uno o más idiomas. El conjunto de caracteres incluye el alfabeto y la puntuación que se usa en el script. Por ejemplo, alfabeto latino se utiliza para inglés se habla en Estados Unidos y su alfabeto incluye los caracteres de la A la Z. El `lfCharSet` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura especifica un juego de caracteres. Por ejemplo, el valor `ANSI_CHARSET` especifica la [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] juego de caracteres, que incluye el alfabeto del alfabeto latino.  
  
##  <a name="a-namegetfullnamea--cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFCFontInfo::GetFullName  
 Recupera los nombres concatenados de una fuente y el carácter conjunto (script).  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Cadena que contiene el nombre de la fuente y el script.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para obtener el nombre completo de la fuente. Por ejemplo, si el nombre de la fuente es `Arial` y la secuencia de comandos de la fuente es `Cyrillic`, este método devuelve "Arial (cirílico)".  
  
##  <a name="a-namemncharseta--cmfcfontinfomncharset"></a><a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet  
 Un valor que especifica el juego de caracteres (alfabeto) asociado a la fuente.  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `nCharSet` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="a-namemnpitchandfamilya--cmfcfontinfomnpitchandfamily"></a><a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily  
 Un valor que especifica el tono (tamaño) y la familia (por ejemplo, serif, sans-serif y monospace) de la fuente.  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `nPitchAndFamily` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="a-namemntypea--cmfcfontinfomntype"></a><a name="m_ntype"></a>CMFCFontInfo::m_nType  
 Un valor que especifica el tipo de la fuente.  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `nType` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="a-namemstrnamea--cmfcfontinfomstrname"></a><a name="m_strname"></a>CMFCFontInfo::m_strName  
 El nombre de la fuente: por ejemplo, **Arial**.  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `lpszName` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
##  <a name="a-namemstrscripta--cmfcfontinfomstrscript"></a><a name="m_strscript"></a>CMFCFontInfo::m_strScript  
 El nombre de un juego de caracteres (alfabeto) asociado a la fuente.  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el `lpszScript` parámetro de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [Clase CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

