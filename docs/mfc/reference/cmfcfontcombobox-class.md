---
title: Clase CMFCFontComboBox | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFontComboBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontComboBox::DrawItem method
- CMFCFontComboBox::PreTranslateMessage method
- CMFCFontComboBox::MeasureItem method
- CMFCFontComboBox class
- CMFCFontComboBox::CompareItem method
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
caps.latest.revision: 29
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
ms.openlocfilehash: 1252f5ca102637e70cc384afd723464aec4144b4
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfontcombobox-class"></a>Clase CMFCFontComboBox
La `CMFCFontComboBox` clase crea un control de cuadro combinado que contiene una lista de fuentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Construye un objeto `CMFCFontComboBox`.|  
|`CMFCFontComboBox::~CMFCFontComboBox`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|Llamado por el marco de trabajo para determinar la posición relativa de un elemento nuevo en el cuadro de lista ordenada del control de cuadro combinado de actual fuente. (Invalida [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|  
|`CMFCFontComboBox::DrawItem`|Llamado por el marco para dibujar un elemento especificado en el control de cuadro de cuadro combinado de fuente actual. (Invalida [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|Recupera información acerca de la fuente seleccionada actualmente.|  
|`CMFCFontComboBox::MeasureItem`|Llamado por el marco para informar a Windows de las dimensiones del cuadro de lista de control de cuadro combinado de actual fuente. (Invalida [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|  
|`CMFCFontComboBox::PreTranslateMessage`|Convierte los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCFontComboBox::SelectFont](#selectfont)|Selecciona la fuente que coincida con los criterios especificados en el cuadro combinado de fuente.|  
|[CMFCFontComboBox::Setup](#setup)|Inicializa la lista de elementos en el cuadro combinado de fuente.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Indica al marco de la fuente que se utiliza para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un `CMFCFontComboBox` objeto en un cuadro de diálogo, agregue un `CMFCFontComboBox` variable a la clase de cuadro de diálogo. A continuación, en la `OnInitDialog` método de la clase de cuadro de diálogo, llamada la [CMFCFontComboBox::Setup](#setup) método para inicializar la lista de elementos en el control de cuadro combinado.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxfontcombobox.h  
  
##  <a name="a-namecmfcfontcomboboxa--cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox  
 Construye un objeto `CMFCFontComboBox`.  
  
```  
CMFCFontComboBox();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetselfonta--cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFCFontComboBox::GetSelFont  
 Recupera información acerca de la fuente seleccionada actualmente.  
  
```  
CMFCFontInfo* GetSelFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a [CMFCFontInfo clase](../../mfc/reference/cmfcfontinfo-class.md) objeto que describe una fuente. Puede ser `NULL` si no hay ninguna fuente está seleccionada en el cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namembdrawusingfonta--cmfcfontcomboboxmbdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont  
 Indica al marco de la fuente que se utiliza para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual.  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro del grupo `TRUE` para dirigir el marco de trabajo para utilizar la misma fuente para dibujar cada etiqueta de elemento. Este miembro del grupo `FALSE` para dirigir el marco de trabajo para dibujar cada etiqueta de elemento con la fuente cuyo nombre es el mismo que la etiqueta. El valor predeterminado de este miembro es `FALSE`.  
  
##  <a name="a-nameselectfonta--cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFCFontComboBox::SelectFont  
 Selecciona la fuente que coincida con los criterios especificados en el cuadro combinado de fuente.  
  
```  
BOOL SelectFont(CMFCFontInfo* pDesc);

 
BOOL SelectFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDesc`  
 Apunta a un objeto de descripción de la fuente.  
  
 [in] `lpszName`  
 Especifica un nombre de fuente.  
  
 [in] `nCharSet`  
 Especifica un juego de caracteres. El valor predeterminado es DEFAULT_CHARSET. Para obtener más información, consulte el `lfCharSet` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un elemento en el cuadro combinado de fuente coincide con el objeto de descripción de la fuente especificada o el nombre de la fuente y el juego de caracteres; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para seleccionar y desplácese hasta el elemento en el cuadro combinado de fuente que corresponde a la fuente especificada.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SelectFont` método en la `CMFCFontComboBox` clase. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls&#34;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls&#35;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
##  <a name="a-namesetupa--cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontComboBox::Setup  
 Inicializa la lista de elementos en el cuadro combinado de fuente.  
  
```  
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFontType`  
 Especifica el tipo de fuente. El valor predeterminado es la combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.  
  
 [in] `nCharSet`  
 Especifica el juego de caracteres de la fuente. El valor predeterminado es DEFAULT_CHARSET.  
  
 [in] `nPitchAndFamily`  
 Especifica el tono de la fuente y la familia. El valor predeterminado es DEFAULT_PITCH.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el cuadro combinado de fuente se inicializó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método inicializa el cuadro combinado de fuente enumerar las fuentes instaladas actualmente que coinciden con los parámetros especificados e insertar los nombres de fuente en el cuadro combinado de fuente.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Setup` método en la `CMFCFontComboBox` clase. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls&#34;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls&#36;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [Clase CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)

