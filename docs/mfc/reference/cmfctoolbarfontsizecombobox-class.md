---
title: Clase CMFCToolBarFontSizeComboBox | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2c5734618bf1bedc72fe78dbeaada8c437391f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>Clase CMFCToolBarFontSizeComboBox
Un botón de barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar un tamaño de fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Construye un objeto `CMFCToolBarFontSizeComboBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Devuelve el tamaño de fuente seleccionado en twips.|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Rellena la lista del cuadro combinado con todos los tamaños de fuente compatibles para una fuente determinada.|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Establece el tamaño de fuente en twips.|  
  
## <a name="remarks"></a>Comentarios  
 Puede usar un `CMFCToolBarFontSizeComboBox` objeto junto con un [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objeto y permitir al usuario seleccionar una fuente y tamaño de fuente.  
  
 Puede agregar un botón de cuadro combinado de tamaño de fuente a una barra de herramientas, como agregar un botón de cuadro combinado de fuente. Para obtener más información, consulte [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
 Cuando el usuario selecciona una fuente nueva en un `CMFCToolBarFontComboBox` objeto, puede rellenar el cuadro combinado de tamaño de fuente con los tamaños admitidos de la fuente mediante el uso de la [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CMFCToolBarFontSizeComboBox` clase para configurar un `CMFCToolBarFontSizeComboBox` objeto. El ejemplo muestra cómo recuperar el tamaño de fuente, en twips, en el cuadro de texto, rellenar el cuadro combinado de tamaño de fuente con todos los tamaños válidos de la fuente determinada y especificar el tamaño de fuente en twips. Este fragmento de código forma parte del [ejemplo de WordPad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 Construye un objeto `CMFCToolBarFontSizeComboBox`.  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize  
 Recupera el tamaño de fuente, en twips, en el cuadro de texto de un cuadro combinado de tamaño de fuente.  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es positivo, es el tamaño de fuente en twips. Es -1 si el cuadro de texto del cuadro combinado está vacío. Es -2 si se produce un error.  
  
##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 Un cuadro combinado de tamaño de fuente se llena con todos los tamaños válidos de la fuente determinada.  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>Parámetros  
 `[in] strFontName`  
 Especifica un nombre de fuente.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función cuando desee sincronizar entre la selección de un cuadro combinado de fuente y un cuadro combinado del tamaño de fuente, como un [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize  
 Redondea especificado tamaño (en twips) para el tamaño más cercano en puntos y, a continuación, Establece el tamaño seleccionado en el cuadro combinado para ese valor.  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nSize`  
 Especifica el tamaño de fuente (en twips) para establecer.  
  
### <a name="remarks"></a>Comentarios  
 Puede recuperar el tamaño de fuente válido anterior más tarde mediante una llamada a la [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) método.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Clase CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [Clase CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)



