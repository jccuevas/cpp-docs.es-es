---
title: CMFCFontComboBox (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67fae4e4fd130e8cb61554f7e2d41595070ee819
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852290"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox (clase)
La `CMFCFontComboBox` clase crea un control de cuadro combinado que contiene una lista de fuentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Construye un objeto `CMFCFontComboBox`.|  
|`CMFCFontComboBox::~CMFCFontComboBox`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|Lo llama el marco de trabajo para determinar la posición relativa de un nuevo elemento en el cuadro de lista ordenada del control de cuadro de cuadro combinado de fuente actual. (Invalida [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|  
|`CMFCFontComboBox::DrawItem`|Lo llama el marco de trabajo para dibujar un elemento especificado en el control de cuadro de cuadro combinado de fuente actual. (Invalida [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|Recupera información acerca de la fuente seleccionada actualmente.|  
|`CMFCFontComboBox::MeasureItem`|Lo llama el marco de trabajo para informar a Windows de las dimensiones del cuadro de lista en el control de cuadro de cuadro combinado de fuente actual. (Invalida [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|  
|`CMFCFontComboBox::PreTranslateMessage`|Traduce los mensajes de ventana antes de enviarlos a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|  
|[CMFCFontComboBox::SelectFont](#selectfont)|Selecciona la fuente que coincide con los criterios especificados en el cuadro combinado de fuente.|  
|[CMFCFontComboBox::Setup](#setup)|Inicializa la lista de elementos en el cuadro combinado de fuente.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Indica qué fuente se utiliza para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual para el marco de trabajo.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un `CMFCFontComboBox` objetos en un cuadro de diálogo, agregar un `CMFCFontComboBox` variable a la clase de cuadro de diálogo. A continuación, en el `OnInitDialog` método de la clase de cuadro de diálogo, llamada la [CMFCFontComboBox::Setup](#setup) método para inicializar la lista de elementos en el control de cuadro combinado.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxfontcombobox.h  
  
##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox  
 Construye un objeto `CMFCFontComboBox`.  
  
```  
CMFCFontComboBox();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont  
 Recupera información acerca de la fuente seleccionada actualmente.  
  
```  
CMFCFontInfo* GetSelFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a [CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md) objeto que describe una fuente. Puede ser NULL si no se selecciona ninguna fuente en el cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont  
 Indica qué fuente se utiliza para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual para el marco de trabajo.  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro se establece en TRUE para indicar al marco que use la misma fuente para dibujar cada etiqueta de elemento. Este miembro se establece en FALSE para dirigir el marco de trabajo para dibujar cada etiqueta de elemento con la fuente cuyo nombre es el mismo que la etiqueta. El valor predeterminado de este miembro es FALSE.  
  
##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont  
 Selecciona la fuente que coincide con los criterios especificados en el cuadro combinado de fuente.  
  
```  
BOOL SelectFont(CMFCFontInfo* pDesc);

 
BOOL SelectFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDesc*  
 Apunta a un objeto de descripción de la fuente.  
  
 [in] *lpszName*  
 Especifica un nombre de fuente.  
  
 [in] *nCharSet*  
 Especifica un juego de caracteres. El valor predeterminado es DEFAULT_CHARSET. Para obtener más información, consulte el `lfCharSet` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si un elemento en el cuadro combinado de fuente que coincide con el objeto de descripción de la fuente especificada o el nombre de la fuente y el juego de caracteres; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para seleccionar y desplácese hasta el elemento en el cuadro combinado de fuente que corresponde a la fuente especificada.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el `SelectFont` método en el `CMFCFontComboBox` clase. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
##  <a name="setup"></a>  CMFCFontComboBox::Setup  
 Inicializa la lista de elementos en el cuadro combinado de fuente.  
  
```  
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nFontType*  
 Especifica el tipo de fuente. El valor predeterminado es la combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.  
  
 [in] *nCharSet*  
 Especifica el juego de caracteres de la fuente. El valor predeterminado es DEFAULT_CHARSET.  
  
 [in] *nPitchAndFamily*  
 Especifica el paso de la fuente y la familia. El valor predeterminado es DEFAULT_PITCH.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el cuadro combinado de fuente se inicializó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método inicializa el cuadro combinado de fuente al enumerar las fuentes instaladas actualmente que coinciden con los parámetros especificados y la inserción de los nombres de fuente en el cuadro combinado de fuente.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el `Setup` método en el `CMFCFontComboBox` clase. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md)
