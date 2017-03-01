---
title: Clase CVSListBox | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CVSListBox
dev_langs:
- C++
helpviewer_keywords:
- CVSListBox::PreTranslateMessage method
- CVSListBox class
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
caps.latest.revision: 30
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
ms.openlocfilehash: 4527249fc1a22a1db0623ea46954065fcbd071f4
ms.lasthandoff: 02/24/2017

---
# <a name="cvslistbox-class"></a>Clase CVSListBox
La `CVSListBox` clase admite un control de lista modificable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](#cvslistbox)|Construye un objeto `CVSListBox`.|  
|`CVSListBox::~CVSListBox`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CVSListBox::AddItem](#additem)|Agrega una cadena a un control de lista. (Invalida `CVSListBoxBase::AddItem`).|  
|[CVSListBox::EditItem](#edititem)|Inicia una operación de edición en el texto de un elemento de control de lista. (Invalida `CVSListBoxBase::EditItem`).|  
|[CVSListBox::GetCount](#getcount)|Recupera el número de cadenas en un control de lista modificable. (Invalida `CVSListBoxBase::GetCount`).|  
|[CVSListBox::GetItemData](#getitemdata)|Recupera un valor de 32 bits específicos de la aplicación que está asociado a un elemento de control de lista modificable. (Invalida `CVSListBoxBase::GetItemData`).|  
|[CVSListBox::GetItemText](#getitemtext)|Recupera el texto de un elemento de control de lista modificable. (Invalida `CVSListBoxBase::GetItemText`).|  
|[CVSListBox::GetSelItem](#getselitem)|Recupera el índice de base cero del elemento actualmente seleccionado en un control de lista modificable. (Invalida `CVSListBoxBase::GetSelItem`).|  
|`CVSListBox::PreTranslateMessage`|Convierte los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. Para obtener más información y la sintaxis del método, consulte [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CVSListBoxBase::PreTranslateMessage`).|  
|[CVSListBox::RemoveItem](#removeitem)|Quita un elemento de un control de lista modificable. (Invalida `CVSListBoxBase::RemoveItem`).|  
|[CVSListBox::SelectItem](#selectitem)|Selecciona una cadena de control de lista modificable. (Invalida `CVSListBoxBase::SelectItem`).|  
|[CVSListBox::SetItemData](#setitemdata)|Asocia un valor de 32 bits específicos de la aplicación con un elemento de control de lista modificable. (Invalida `CVSListBoxBase::SetItemData`).|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|Devuelve el identificador para el control de vista de lista incrustada actual.|  
  
## <a name="remarks"></a>Comentarios  
 La `CVSListBox` clase proporciona un conjunto de botones de edición que permiten al usuario crear, modificar, eliminar o reorganizar los elementos de un control de lista.  
  
 La siguiente es una imagen del control de lista modificable. La segunda entrada de lista, el título "Item2", está seleccionada para su edición.  
  
 ![Control CVSListBox](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 Si utiliza el editor de recursos para agregar un control de lista modificable, tenga en cuenta que el **herramientas** panel del editor no proporciona un control de lista modificable predefinido. En su lugar, agregue un control estático como el **cuadro de grupo** control. El marco de trabajo usa el control estático como un marcador de posición para especificar el tamaño y la posición del control de lista modificable.  
  
 Para utilizar un control de lista modificable en una plantilla de cuadro de diálogo, declara un `CVSListBox` variable en la clase de cuadro de diálogo. Para admitir el intercambio de datos entre la variable y el control, defina un `DDX_Control` entrada de macro en el `DoDataExchange` (método) del cuadro de diálogo. De forma predeterminada, se crea el control de lista modificable sin botones Editar. Utilice el método CVSListBoxBase::SetStandardButtons heredado para habilitar los botones de edición.  
  
 Para obtener más información, consulte el directorio de ejemplos, la `New Controls` de ejemplo, los archivos Page3.cpp y Page3.h.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxvslistbox.h  
  
##  <a name="a-nameadditema--cvslistboxadditem"></a><a name="additem"></a>CVSListBox::AddItem  
 Agrega una cadena a un control de lista.  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strIext`  
 Una referencia a una cadena.  
  
 [in] `dwData`  
 Un valor de 32 bits específicos de la aplicación que está asociado a la cadena. El valor predeterminado es 0.  
  
 [in] `iIndex`  
 Índice de base cero de la posición que contendrá la cadena. Si el `iIndex` parámetro es -1, la cadena se agrega al final de la lista. El valor predeterminado es -1.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la posición de la cadena del control de lista.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CVSListBox::GetItemData](#getitemdata) método para recuperar el valor especificado por el `dwData` parámetro. Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.  
  
##  <a name="a-namecvslistboxa--cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox::CVSListBox  
 Construye un objeto `CVSListBox`.  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameedititema--cvslistboxedititem"></a><a name="edititem"></a>CVSListBox::EditItem  
 Inicia una operación de edición en el texto de un elemento de control de lista.  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento de control de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la operación de edición se inicia correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El usuario inicia una operación de edición haciendo doble clic en la etiqueta de un elemento, o bien presionando el **F2** o **espaciadora** clave cuando un elemento tiene el foco.  
  
##  <a name="a-namegetcounta--cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox::GetCount  
 Recupera el número de cadenas en un control de lista modificable.  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos en el control de lista.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el recuento es mayor que el valor de índice del último elemento porque el índice está basado en cero.  
  
##  <a name="a-namegetitemdataa--cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox::GetItemData  
 Recupera un valor de 32 bits específicos de la aplicación que está asociado a un elemento de control de lista modificable.  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento de control de lista modificable.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de 32 bits que está asociado con el elemento especificado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CVSListBox::SetItemData](#setitemdata) o [CVSListBox::AddItem](#additem) para asociar el valor de 32 bits con el elemento de control de lista. Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.  
  
##  <a name="a-namegetitemtexta--cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox::GetItemText  
 Recupera el texto de un elemento de control de lista modificable.  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento de control de lista modificable.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto del elemento especificado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetlisthwnda--cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox::GetListHwnd  
 Devuelve el identificador para el control de vista de lista incrustada actual.  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del control de vista de lista incrustada.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para obtener un identificador para el control de vista de lista incrustada que admite la `CVSListBox` clase.  
  
##  <a name="a-namegetselitema--cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::GetSelItem  
 Recupera el índice de base cero del elemento actualmente seleccionado en un control de lista modificable.  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si este método se realiza correctamente, el índice de base cero del elemento actualmente seleccionado; en caso contrario, es -1.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremoveitema--cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox::RemoveItem  
 Quita un elemento de un control de lista modificable.  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento de control de lista modificable.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se quita el elemento especificado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameselectitema--cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox::SelectItem  
 Selecciona una cadena de control de lista modificable.  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iItem`  
 Índice de base cero de un elemento de control de lista modificable.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método selecciona el elemento especificado y, si es necesario, desplaza el elemento en la vista.  
  
##  <a name="a-namesetitemdataa--cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::SetItemData  
 Asocia un valor de 32 bits específicos de la aplicación con un elemento de control de lista modificable.  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento de control de lista modificable.  
  
 [in] `dwData`  
 Un valor de 32 bits. Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

