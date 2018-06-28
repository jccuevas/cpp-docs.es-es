---
title: Clase CMFCRibbonFontComboBox | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 857eb87caf42e39366e261ac92c3b2f289fb41d9
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039380"
---
# <a name="cmfcribbonfontcombobox-class"></a>Clase CMFCRibbonFontComboBox
Implementa un cuadro combinado que contiene una lista de fuentes. El cuadro combinado se coloca en un panel de la cinta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destructor.|  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Construye e inicializa un objeto `CMFCRibbonFontComboBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia especificados.|  
|`CMFCRibbonFontComboBox::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Devuelve el juego de caracteres especificado.|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.|  
|`CMFCRibbonFontComboBox::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia previamente especificados.|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Selecciona la fuente especificada en el cuadro combinado.|  
  
## <a name="remarks"></a>Comentarios  
 Después de crear un `CMFCRibbonFontComboBox` objeto, agréguelo a un panel de cinta de opciones mediante una llamada a [cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonComboBox.h  
  
##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts  
 Rellena el cuadro combinado en la cinta de opciones con las fuentes.  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nFontType*  
 Especifica el tipo de fuente de las fuentes para agregar.  
  
 [in] *nCharSet*  
 Especifica el juego de caracteres de las fuentes para agregar.  
  
 [in] *nPitchAndFamily*  
 Especifica el tono y la familia de las fuentes para agregar.  
  
##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
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
 [in] *nID*  
 El identificador de comando del comando que se ejecuta cuando el usuario selecciona un elemento en el cuadro combinado.  
  
 [in] *nFontType*  
 Especifica los tipos de fuente para mostrar en el cuadro combinado. Las opciones válidas son **DEVICE_FONTTYPE**, **RASTER_FONTTYPE**, y **TRUETYPE_FONTTYPE**, o cualquier combinación bit a bit de los anteriores.  
  
 [in] *nCharSet*  
 Filtra las fuentes en el cuadro combinado a los que pertenecen al juego de caracteres especificado...  
  
 [in] *nPitchAndFamily*  
 Especifica el tono y la familia de las fuentes que se muestran en el cuadro combinado.  
  
 [in] *nWidth*  
 Especifica el ancho, en píxeles, del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los posibles *nFontType* valores de parámetros, vea [EnumFontFamProc](http://msdn.microsoft.com/library/windows/desktop/dd162621) en la documentación del SDK de Windows.  
  
 Para obtener más información acerca de los juegos de caracteres válidos que puede asignarse a *nCharSet*y los valores válidos que pueden asignarse a *nPitchAndFamily*, consulte [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) en el Documentación del SDK de Windows.  
  
##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iÍndice*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts  
 Rellena el cuadro combinado en la cinta de opciones con las fuentes de un tipo de fuente especificada anteriormente, el juego de caracteres y el tono y la familia.  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede especificar el tipo de fuente, el juego de caracteres, y cuadro tono y la familia de las fuentes que se incluirán en el cuadro combinado de fuente de la cinta de opciones la [constructor](#cmfcribbonfontcombobox) para esta clase, o mediante una llamada a [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont  
 Selecciona la fuente especificada en el cuadro combinado.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 ' lpszName *  
 Especifica el nombre de la fuente que se va a seleccionar.  
  
 *nCharSet*  
 Especifica el juego de caracteres para la fuente seleccionada.  
  
 *bExact*  
 `TRUE` para especificar que debe coincidir con el juego de caracteres al seleccionar una fuente; `FALSE` para especificar que se puede omitir el juego de caracteres cuando se selecciona una fuente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la fuente especificada se ha encontrado y seleccionada; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet  
 Devuelve el juego de caracteres especificado.  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Juego de caracteres (consulte LOGFONT en la documentación del SDK de Windows).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType  
 Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipos de fuentes (consulte EnumFontFamProc en la documentación del SDK de Windows).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily  
 Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Paso y la familia (consulte LOGFONT en la documentación del SDK de Windows).  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox (clase)](../../mfc/reference/cmfcribboncombobox-class.md)
