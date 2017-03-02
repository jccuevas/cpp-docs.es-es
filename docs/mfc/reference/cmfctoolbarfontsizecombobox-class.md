---
title: Clase CMFCToolBarFontSizeComboBox | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox class
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
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
ms.openlocfilehash: 9dddb563617a708bdc8b2193fa5ee8bd10321828
ms.lasthandoff: 02/24/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Devuelve el tamaño de fuente seleccionado en twips.|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|La lista del cuadro combinado se rellena con todos los tamaños de fuente compatibles para una fuente especificada.|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Establece el tamaño de fuente en twips.|  
  
## <a name="remarks"></a>Comentarios  
 Puede usar un `CMFCToolBarFontSizeComboBox` objeto junto con un [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objeto y permitir al usuario seleccionar una fuente y tamaño.  
  
 Puede agregar un botón de cuadro combinado de tamaño de fuente a una barra de herramientas, como agregar un botón de cuadro combinado de fuente. Para obtener más información, consulte [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
 Cuando el usuario selecciona una fuente nueva en un `CMFCToolBarFontComboBox` objeto, puede rellenar el cuadro combinado de tamaño de fuente con los tamaños admitidos de la fuente mediante la [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCToolBarFontSizeComboBox` clase para configurar un `CMFCToolBarFontSizeComboBox` objeto. En el ejemplo se muestra cómo recuperar el tamaño de fuente, en twips, desde el cuadro de texto, rellene el cuadro combinado de tamaño de fuente con todos los tamaños válidos de la fuente y especifique el tamaño de fuente en twips. Este fragmento de código forma parte de la [ejemplo de panel de palabras](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad Nº&8;](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarfontcombobox.h  
  
##  <a name="a-namecmfctoolbarfontsizecomboboxa--cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 Construye un objeto `CMFCToolBarFontSizeComboBox`.  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="a-namegettwipsizea--cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize  
 Recupera el tamaño de fuente, en twips, desde el cuadro de texto de un cuadro combinado de tamaño de fuente.  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es positivo, es el tamaño de fuente en twips. Es -1 si el cuadro de texto del cuadro combinado está vacío. Es -2 si se produce un error.  
  
##  <a name="a-namerebuildfontsizesa--cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 Rellena un cuadro combinado de tamaño de fuente con todos los tamaños válidos de la fuente dada.  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>Parámetros  
 `[in] strFontName`  
 Especifica un nombre de fuente.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función cuando desee sincronizar entre la selección en un cuadro combinado de fuente y un cuadro combinado de tamaño de fuente, como un [CMFCToolBarFontComboBox clase](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
##  <a name="a-namesettwipsizea--cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize  
 Redondea especificado (en twips) para el tamaño más cercano en puntos y, a continuación, Establece el tamaño seleccionado en el cuadro combinado para ese valor.  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nSize`  
 Especifica el tamaño de fuente (en twips) para establecer.  
  
### <a name="remarks"></a>Comentarios  
 Puede recuperar el tamaño de fuente válido anterior más adelante llamando a la [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) método.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Clase CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [Clase CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Tutorial: Poner controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)




