---
title: Clase CMFCRibbonButtonsGroup | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonButtonsGroup
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButtonsGroup class
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2d8909ca63bd1d9121e1126d46a08312521cc4ac
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup (Clase)
La `CMFCRibbonButtonsGroup` clase le permite organizar un conjunto de botones de la cinta de opciones en un grupo. Todos los botones del grupo son directamente adyacentes a otros horizontalmente y se incluyen en un borde.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Construye un objeto `CMFCRibbonButtonsGroup`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Agrega un botón a un grupo.|  
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Agrega una lista de botones a un grupo.|  
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Devuelve un puntero al botón que se encuentra en un índice especificado.|  
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Devuelve el número de botones en el grupo.|  
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Devuelve el tamaño de la imagen de las imágenes normales en el grupo de la cinta de opciones (reemplaza [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|  
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta de opciones (reemplaza [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Informes si la `CMFCRibbonButtonsGroup` objeto contiene imágenes de la barra de herramientas.|  
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Dibuja la imagen adecuada para un botón especificada, dependiendo de si el botón normal, resaltada o está deshabilitado.|  
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Quita todos los botones de la `CMFCRibbonButtonsGroup` objeto.|  
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Las imágenes se asigna al grupo.|  
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Establece el elemento primario `CMFCRibbonCategory` de la `CMFCRibbonButtonsGroup` objeto y todos los botones dentro de él (reemplaza [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|  
  
## <a name="remarks"></a>Comentarios  
 El grupo se deriva [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) y se pueden tratar como una sola entidad. El grupo se puede colocar en cualquier panel o un menú emergente.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCRibbonButtonsGroup` clase. En el ejemplo se muestra cómo construir un `CMFCRibbonButtonsGroup` de objeto, asignar imágenes al grupo de botones de la cinta y agregue un botón al grupo de botones de la cinta. Este fragmento de código forma parte de la [ejemplo dibujar cliente](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient&#2;](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonbuttonsgroup.h  
  
##  <a name="a-nameaddbuttona--cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton  
 Agrega un botón a un grupo.  
  
```  
void AddButton(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero a un botón para agregar.  
  
##  <a name="a-nameaddbuttonsa--cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFCRibbonButtonsGroup::AddButtons  
 Agrega una lista de botones a un grupo.  
  
```  
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lstButtons`  
 Una lista de punteros a los botones que se va a agregar.  
  
##  <a name="a-namecmfcribbonbuttonsgroupa--cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup  
 Construye un objeto `CMFCRibbonButtonsGroup`.  
  
```  
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Especifica un botón para agregar a la recién creado `CMFCRibbonButtonsGroup` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetbuttona--cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton  
 Devuelve un puntero al botón que se encuentra en un índice especificado.  
  
```  
CMFCRibbonBaseElement* GetButton(int i) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `i`  
 Índice de base cero de un botón para volver.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al botón que se encuentra en el índice especificado. `NULL`Si el índice especificado está fuera del intervalo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcounta--cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount  
 Devuelve el número de botones en el grupo.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de botones del grupo.  
  
##  <a name="a-namegetimagesizea--cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize  
 Recupera el tamaño de la imagen de origen de protegido `CMFCToolBarImages` miembro `m_Images`.  
  
```  
const CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño de la imagen de origen de las imágenes de la barra de herramientas, si hubiera alguno, o un `CSize` de cero si no es así.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetregularsizea--cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize  
 Recupera el tamaño máximo posible del elemento de grupo de la cinta de opciones.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero al contexto de dispositivo del grupo de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehasimagesa--cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages  
 Informes si la `CMFCRibbonButtonsGroup` objeto contiene imágenes de la barra de herramientas.  
  
```  
BOOL HasImages() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el modo protegido `CMFCToolBarImages` miembro `m_Images` contiene las imágenes o FALSE si no.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawimagea--cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage  
 Dibuja la imagen adecuada para un botón especificada, dependiendo de si el botón normal, resaltada o está deshabilitado.  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rectImage,  
    CMFCRibbonBaseElement* pButton,  
    int nImageIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero al contexto de dispositivo de la `CMFCRibbonButtonsGroup` objeto.  
  
 [in] `rectImage`  
 El rectángulo en el que se va a dibujar la imagen.  
  
 [in] `pButton`  
 El botón para el que se va a dibujar la imagen.  
  
 [in] `nImageIndex`  
 El índice de la imagen para dibujar en el botón (en una de las matrices de tres imágenes para los botones normales, resaltadas o deshabilitados).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremovealla--cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFCRibbonButtonsGroup::RemoveAll  
 Quita todos los botones de la `CMFCRibbonButtonsGroup` objeto.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetimagesa--cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages  
 Imágenes se asigna al grupo de botones de la cinta.  
  
```  
void SetImages(
    CMFCToolBarImages* pImages,  
    CMFCToolBarImages* pHotImages,  
    CMFCToolBarImages* pDisabledImages);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pImages`  
 Imágenes normales.  
  
 [in] `pHotImages`  
 Imágenes activas.  
  
 [in] `pDisabledImages`  
 Imágenes deshabilitadas.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `SetImages` antes de agregar botones a un grupo. El número de imágenes debe ser mayor o igual que el número de botones que deben agregarse al grupo.  
  
> [!NOTE]
>  Imágenes activas son imágenes que se muestran cuando el usuario se desplaza sobre el botón. Imágenes deshabilitadas son imágenes que se muestran cuando el botón está deshabilitado.  
  
##  <a name="a-namesetparentcategorya--cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParentCategory  
 Establece el elemento primario `CMFCRibbonCategory` de la `CMFCRibbonButtonsGroup` objeto y todos los botones dentro de él.  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCategory`  
 Puntero a la categoría primaria para establecer (los grupos con pestañas en los controles de la cinta de opciones se denominan categorías).  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

