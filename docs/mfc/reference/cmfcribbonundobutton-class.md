---
title: Clase CMFCRibbonUndoButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonUndoButton class
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
caps.latest.revision: 35
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
ms.openlocfilehash: d4406e21a7e2a945965020d85a748b93d66b5682
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonundobutton-class"></a>Clase CMFCRibbonUndoButton
La `CMFCRibbonUndoButton` clase implementa un botón de lista desplegable que contiene los comandos de usuario más reciente. Los usuarios pueden seleccionar uno o varios de los comandos más recientes de la lista desplegable rehacer o deshacer en ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Construye un nuevo `CMFCRibbonUndoButton` objeto con el identificador de comando que especifique, etiqueta de texto y las imágenes de la lista de imágenes del objeto primario.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Agrega una nueva acción a la lista de acciones.|  
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Borra la lista de acciones, que es la lista desplegable.|  
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Determina el número de elementos que el usuario seleccionado de la lista desplegable.|  
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Indica si el objeto contiene un menú.|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCRibbonUndoButton` clase utiliza una pila para representar la lista desplegable.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonUndoButton` de clases y agregue una nueva acción a la lista de acciones. Este fragmento de código forma parte de la [ejemplo de Gadgets de cinta de opciones](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RibbonGadgets&#2;](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonundobutton.h  
  
##  <a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction  
 Agrega una nueva acción a la lista de acciones.  
  
```  
void AddUndoAction(LPCTSTR lpszLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 La etiqueta de acción que se mostrará en la lista desplegable.  
  
##  <a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList  
 Borra la lista de acciones, que es la lista desplegable.  
  
```  
void CleanUpUndoList();
```  
  
##  <a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton  
 Construye un nuevo `CMFCRibbonUndoButton` objeto con el identificador de comando que especifique, etiqueta de texto y las imágenes de la lista de imágenes del objeto primario.  
  
```  
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1);

 
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Especifica el identificador de comando.  
  
 [in] `lpszText`  
 Especifica la etiqueta de texto del botón.  
  
 [in] `nSmallImageIndex`  
 Índice de base cero en la lista de imágenes del objeto primario de la imagen del botón pequeño.  
  
 [in] `nLargeImageIndex`  
 Índice de base cero en la lista de imágenes del objeto primario para el de la imagen de gran tamaño del botón.  
  
 [in] `hIcon`  
 Identificador de un icono que puede utilizar como imagen del botón.  
  
##  <a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber  
 Determina el número de elementos que el usuario seleccionado de la lista desplegable.  
  
```  
int GetActionNumber() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos que el usuario seleccionado.  
  
##  <a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu  
 Indica si el objeto contiene un menú.  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)   
 [Clase CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

