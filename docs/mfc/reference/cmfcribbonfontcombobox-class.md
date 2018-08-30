---
title: CMFCRibbonFontComboBox (clase) | Microsoft Docs
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
ms.openlocfilehash: 3a53dd239d2c6cdba77f977cc94642828c5e91b7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216479"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox (clase)
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
|`CMFCRibbonFontComboBox::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia previamente especificados.|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Selecciona la fuente especificada en el cuadro combinado.|  
  
## <a name="remarks"></a>Comentarios  
 Después de crear un `CMFCRibbonFontComboBox` de objetos, agréguelo a un panel de cinta de opciones mediante una llamada a [cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
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
 Rellena el cuadro combinado en la cinta con fuentes.  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nFontType*  
 Especifica el tipo de fuente de las fuentes a agregar.  
  
 [in] *nCharSet*  
 Especifica el juego de caracteres de las fuentes a agregar.  
  
 [in] *nPitchAndFamily*  
 Especifica el cabeceo y la familia de fuentes para agregar.  
  
##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
 Crea e inicializa un [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) objeto.  
  
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
 Especifica los tipos de fuente para mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.  
  
 [in] *nCharSet*  
 Filtra las fuentes en el cuadro combinado a los que pertenecen al juego de caracteres especificado...  
  
 [in] *nPitchAndFamily*  
 Especifica el tono y la familia de fuentes que se muestran en el cuadro combinado.  
  
 [in] *nWidth*  
 Especifica el ancho, en píxeles, del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre las posibles *nFontType* valores de parámetros, vea [EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) en la documentación del SDK de Windows.  
  
 Para obtener más información acerca de los juegos de caracteres válidos que se pueden asignar a *nCharSet*y los valores válidos que se pueden asignar a *nPitchAndFamily*, consulte [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) en el Documentación del SDK de Windows.  
  
##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc  
 Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iÍndice*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts  
 Rellena el cuadro combinado de la cinta con fuentes de un tipo de fuente especificado anteriormente, el juego de caracteres y cabeceo y familia.  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede especificar el tipo de fuente, el juego de caracteres, y cuadro paso y la familia de fuentes para incluir en el cuadro combinado de fuente de cinta de opciones el [constructor](#cmfcribbonfontcombobox) para esta clase, o mediante una llamada a [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
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
 Especifica el nombre de la fuente que seleccione.  
  
 *nCharSet*  
 Especifica el juego de caracteres para la fuente seleccionada.  
  
 *bExact*  
 TRUE para especificar que debe coincidir con el juego de caracteres cuando se selecciona una fuente; FALSE para especificar que se puede omitir el juego de caracteres cuando se selecciona una fuente.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la fuente especificada se ha encontrado y seleccionada; en caso contrario, es cero.  
  
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
