---
title: Clase CMFCRibbonFontComboBox | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonFontComboBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonFontComboBox class
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
caps.latest.revision: 24
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
ms.openlocfilehash: 851ef15013ca62012931fd92baf277d5db96033d
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonfontcombobox-class"></a>Clase CMFCRibbonFontComboBox
Implementa un cuadro combinado que contiene una lista de fuentes. El cuadro combinado se coloca en un panel de la cinta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destructor.|  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Construye e inicializa un objeto `CMFCRibbonFontComboBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia especificados.|  
|`CMFCRibbonFontComboBox::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Devuelve el juego de caracteres especificado.|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.|  
|`CMFCRibbonFontComboBox::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia previamente especificados.|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Selecciona la fuente especificada en el cuadro combinado.|  
  
## <a name="remarks"></a>Comentarios  
 Después de crear un `CMFCRibbonFontComboBox` de objeto, agregue un panel de cinta de opciones mediante una llamada a [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonComboBox.h  
  
##  <a name="a-namebuildfontsa--cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts  
 Rellena el cuadro combinado de la cinta de opciones con las fuentes.  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFontType`  
 Especifica el tipo de fuente de las fuentes para agregar.  
  
 [in] `nCharSet`  
 Especifica el juego de caracteres de las fuentes para agregar.  
  
 [in] `nPitchAndFamily`  
 Especifica el tono y la familia de las fuentes para agregar.  
  
##  <a name="a-namecmfcribbonfontcomboboxa--cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
 Construye e inicializa un [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) objeto.  
  
```  
CMFCRibbonFontComboBox(
    UINT nID,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH,  
    int nWidth = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 El identificador de comando del comando que se ejecuta cuando el usuario selecciona un elemento en el cuadro combinado.  
  
 [in] `nFontType`  
 Especifica los tipos de fuente para mostrar en el cuadro combinado. Las opciones válidas son **DEVICE_FONTTYPE**, **RASTER_FONTTYPE**, y **TRUETYPE_FONTTYPE**, o una combinación bit a bit.  
  
 [in] `nCharSet`  
 Filtra las fuentes en el cuadro combinado a los que pertenecen al conjunto de caracteres especificado...  
  
 [in] `nPitchAndFamily`  
 Especifica el tono y la familia de las fuentes que se muestran en el cuadro combinado.  
  
 [in] `nWidth`  
 Especifica el ancho, en píxeles, del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre las posibles `nFontType` valores de parámetro, consulte [EnumFontFamProc](http://msdn.microsoft.com/library/windows/desktop/dd162621) en la documentación del SDK de Windows.  
  
 Para obtener más información acerca de los conjuntos de caracteres válidos que pueden asignarse a `nCharSet,` y los valores válidos que pueden asignarse a `nPitchAndFamily`, consulte [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) en la documentación del SDK de Windows.  
  
##  <a name="a-namegetfontdesca--cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerebuildfontsa--cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts  
 Rellena el cuadro combinado en la cinta de opciones con las fuentes de un tipo de fuente especificados anteriormente, el juego de caracteres y cabeceo y familia.  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede especificar el tipo de fuente, el juego de caracteres, y cuadro de cabeceo y la familia de fuentes para incluir en el cuadro combinado de fuente de cinta de opciones de la [constructor](#cmfcribbonfontcombobox) para esta clase, o mediante una llamada a [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="a-namesetfonta--cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFCRibbonFontComboBox::SetFont  
 Selecciona la fuente especificada en el cuadro combinado.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Especifica el nombre de la fuente que seleccione.  
  
 `nCharSet`  
 Especifica el juego de caracteres de la fuente seleccionada.  
  
 `bExact`  
 `TRUE`para especificar que debe coincidir con el juego de caracteres cuando se selecciona una fuente; `FALSE` para especificar que se puede omitir el juego de caracteres cuando se selecciona una fuente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la fuente especificada ha encontrado y seleccionada; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcharseta--cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet  
 Devuelve el juego de caracteres especificado.  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Juego de caracteres (consulte LOGFONT en la documentación del SDK de Windows).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetfonttypea--cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType  
 Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipos de fuentes (consulte EnumFontFamProc en la documentación del SDK de Windows).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpitchandfamilya--cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily  
 Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Paso y la familia (consulte LOGFONT en la documentación del SDK de Windows).  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

