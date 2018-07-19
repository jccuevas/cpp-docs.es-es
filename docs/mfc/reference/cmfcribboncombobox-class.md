---
title: CMFCRibbonComboBox (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2ccefbc435cac5b48cd2c9509831699dcec70af
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849674"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox (clase)
La `CMFCRibbonComboBox` clase implementa un control de cuadro combinado que se puede agregar a una barra de cinta, un panel de cinta o un menú emergente de cinta de opciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Construye un objeto CMFCRibbonComboBox.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|Anexa un elemento único en el cuadro de lista.|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Elimina un elemento especificado en el cuadro de lista.|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Especifica si el cuadro de lista puede cambiar el tamaño cuando despliega.|  
|[CMFCRibbonComboBox::FindItem](#finditem)|Devuelve el índice del primer elemento en el cuadro de lista que coincide con una cadena especificada.|  
|[CMFCRibbonComboBox::GetCount](#getcount)|Devuelve el número de elementos en el cuadro de lista.|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Obtiene el índice del elemento actualmente seleccionado en el cuadro de lista.|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Obtiene el alto del cuadro de lista cuando se quita el cuadro de lista.|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Devuelve el tamaño del cuadro combinado, tal como se muestra en el modo intermedio.|  
|[CMFCRibbonComboBox::GetItem](#getitem)|Devuelve la cadena asociada a un elemento en el índice especificado en el cuadro de lista.|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Devuelve los datos asociados con un elemento en el índice especificado en el cuadro de lista.|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Indica si el control contiene un cuadro de edición.|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Indica si se puede cambiar el tamaño del cuadro de lista.|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Lo llama el marco cuando el usuario selecciona un elemento en el cuadro de lista.|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Elimina todos los elementos del cuadro de lista y borra el cuadro de edición.|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Selecciona un elemento en el cuadro de lista.|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Establece el alto del cuadro de lista cuando se coloca.|  
  
## <a name="remarks"></a>Comentarios  
 El cuadro combinado cinta consta de un cuadro de lista combinado con una etiqueta estática o una etiqueta que se puede editar el usuario. Debe especificar qué tipo que desee al crear el cuadro combinado de cinta de opciones.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonComboBox` clase, agregue un elemento al cuadro combinado, seleccione un elemento en el cuadro combinado y agregue un cuadro combinado a un panel.  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribboncombobox.h  
  
##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem  
 Anexa un elemento único en el cuadro de lista.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszItem*  
 La cadena del elemento que se va a agregar.  
  
 [in] *dwData*  
 Los datos asociados con el elemento que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento anexado.  
  
##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox  
 Construye un objeto `CMFCRibbonComboBox`.  
  
```  
public:  
CMFCRibbonComboBox(
    UINT nID,  
    BOOL bHasEditBox=TRUE,  
    Int nWidth=-1,  
    LPCTSTR lpszLabel=NULL,  
    Int nImage=-1);

protected:  
CMFCRibbonComboBox();
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nID*  
 El identificador del cuadro combinado.  
  
 [in] *bHasEditBox*  
 TRUE si desea que un cuadro de edición dentro del control. FALSE en caso contrario.  
  
 [in] *nWidth*  
 Ancho del cuadro combinado en píxeles. o -1 para el ancho predeterminado.  
  
 [in] *lpszLabel*  
 La etiqueta de pantalla del cuadro combinado.  
  
 [in] *nImage*  
 El índice de imagen pequeña del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 El ancho predeterminado es 108 píxeles.  
  
##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem  
 Elimina un elemento especificado en el cuadro de lista.  
  
```  
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iÍndice*  
 Índice de base cero del elemento que se va a eliminar.  
  
 [in] *dwData*  
 Los datos asociados con el elemento que se va a eliminar.  
  
 [in] *lpszText*  
 La cadena del elemento que se va a eliminar. Si hay varios elementos con la misma cadena, se elimina el primer elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se ha eliminado el elemento especificado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize  
 Especifica si el cuadro de lista puede cambiar el tamaño cuando despliega.  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHabilitar el*  
 True para habilitar el cambio de tamaño; FALSE para deshabilitar el cambio de tamaño.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se habilita el cambio de tamaño, el cuadro de lista cambiará de tamaño para ajustarse a los elementos que muestra.  
  
##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem  
 Devuelve el índice del primer elemento en el cuadro de lista que coincide con una cadena especificada.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszText*  
 La cadena de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento; o -1 si no se encuentra el elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount  
 Devuelve el número de elementos en el cuadro de lista.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el cuadro de lista, o 0 si el cuadro de lista no contiene ningún elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel  
 Obtiene el índice del elemento actualmente seleccionado en el cuadro de lista.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento actualmente seleccionado en el cuadro de lista. o -1 si ningún elemento seleccionado.  
  
##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight  
 Obtiene el alto del cuadro de lista cuando se quita el cuadro de lista.  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto, en píxeles, del cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize  
 Devuelve el tamaño del cuadro combinado, tal como se muestra en el modo intermedio.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo para el cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño devuelto se basa en el tamaño del cuadro combinado cuando se muestran imágenes pequeñas.  
  
##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem  
 Devuelve la cadena asociada a un elemento en el índice especificado en el cuadro de lista.  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iÍndice*  
 Índice de base cero de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la cadena que está asociado con el elemento; de lo contrario, NULL si el parámetro de índice no es válido, o si el parámetro de índice es -1 y no hay ningún elemento seleccionado en el cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData  
 Devuelve los datos asociados con un elemento en el índice especificado en el cuadro de lista.  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iÍndice*  
 Índice de base cero de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos asociados con el elemento; o 0 si el elemento no existe, o si el parámetro de índice es -1 y no hay ningún elemento seleccionado en el cuadro de lista.  
  
##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox  
 Indica si el control contiene un cuadro de edición.  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el control contiene un cuadro de edición; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList  
 Indica si se puede cambiar el tamaño del cuadro de lista.  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el cuadro de lista puede cambiar de tamaño; en caso contrario, FALSE. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>Comentarios  
 Puede permitir que cambiar el tamaño del cuadro de lista mediante el uso de la [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) método.  
  
##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem  
 Lo llama el marco cuando un usuario selecciona un elemento en el cuadro de lista.  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nItem*  
 El índice del elemento seleccionado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea procesar una selección de entrada del usuario.  
  
##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems  
 Elimina todos los elementos del cuadro de lista y borra el cuadro de edición.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem  
 Selecciona un elemento en el cuadro de lista.  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iÍndice*  
 Índice de base cero de un elemento en el cuadro de lista.  
  
 [in] *dwData*  
 Los datos asociados a un elemento en el cuadro de lista.  
  
 [in] *lpszText*  
 La cadena de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight  
 Establece el alto del cuadro de lista cuando se coloca.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nHeight*  
 El alto, en píxeles, del cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 El alto predeterminado es 150 píxeles.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit (clase)](../../mfc/reference/cmfcribbonedit-class.md)
