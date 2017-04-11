---
title: Clase CMFCToolBarEditBoxButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarEditBoxButton class
- SetACCData method
- OnCalculateSize method
- OnDraw method
- OnDrawOnCustomizeList method
- Serialize method
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
caps.latest.revision: 28
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 4334dfc7074cd55173af15cc1fab59882c9e8e6c
ms.lasthandoff: 04/04/2017

---
# <a name="cmfctoolbareditboxbutton-class"></a>Clase CMFCToolBarEditBoxButton
Un botón de barra de herramientas que contiene un control de edición ( [clase CEdit](../../mfc/reference/cedit-class.md)).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Construye un objeto `CMFCToolBarEditBoxButton`.|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Especifica si un usuario puede ajustar el botón durante la personalización. (Invalida [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de barra de herramientas a la actual. (Invalida [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Crea un nuevo control de edición en el botón.|  
|`CMFCToolBarEditBoxButton::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Recupera el primer `CMFCToolBarEditBoxButton` objeto de la aplicación con el identificador de comando especificado.|  
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Recupera el texto del primer control de barra de herramientas de cuadro de edición con el identificador de comando especificado.|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Recupera el identificador de recurso del menú contextual que está asociado con el botón.|  
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Recupera el rectángulo delimitador de la parte de edición del botón de cuadro de edición.|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Devuelve un puntero para el control de edición que está incrustado en el botón.|  
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Recupera el identificador de ventana que está asociado con el botón de barra de herramientas. (Invalida [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Recupera la región del área cliente del botón que se debe volver a dibujar. (Invalida [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|  
|`CMFCToolBarEditBoxButton::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Determina si un borde del botón se muestra cuando un usuario hace clic en el botón. (Invalida [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Determina si los botones del cuadro de edición tienen un estilo plano.|  
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Especifica si el botón procesa el [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje. (Invalida [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Invalida [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Lo llama el marco cuando el usuario hace clic en el botón del mouse. (Invalida [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Lo llama el marco cuando la barra de herramientas primario controla un `WM_CTLCOLOR` mensaje. (Invalida [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarEditBoxButton::OnDraw`|Lo llama el marco de trabajo para dibujar el botón con los estilos especificados y las opciones. (Invalida [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Lo llama el marco para dibujar el botón el **comandos** panel de la **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Lo llama el marco de trabajo cuando ha cambiado la fuente global. (Invalida [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Llamado por el marco de trabajo cuando se mueve la barra de herramientas primario. (Invalida [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible. (Invalida [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Lo llama el marco de trabajo cuando la barra de herramientas primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño. (Invalida [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Llamado por el marco de trabajo cuando la barra de herramientas principal actualiza el texto de información sobre herramientas. (Invalida [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarEditBoxButton::Serialize`|Lee este objeto desde un archivo o lo escribe en un archivo. (Invalida [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarEditBoxButton::SetACCData`|Rellena proporcionado `CAccessibilityData` objeto con datos de accesibilidad en el botón de barra de herramientas. (Invalida [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|Establece el texto en el control de edición del botón.|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Busca el botón de control de edición que tiene un identificador de comando especificado y establece el texto en el control de edición de ese botón.|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Especifica el identificador de recurso del menú contextual que está asociado con el botón.|  
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Especifica la apariencia de estilo plano de botones del cuadro de edición en la aplicación.|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Especifica el estilo del botón. (Invalida [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
  
## <a name="remarks"></a>Comentarios  
 Para agregar un botón de cuadro de edición a una barra de herramientas, siga estos pasos:  
  
 1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.  
  
 2. Construir un `CMFCToolBarEditBoxButton` objeto.  
  
 3. En el controlador de mensajes que procesa el `AFX_WM_RESETTOOLBAR` de mensajes, reemplazar el botón ficticio con el nuevo botón de cuadro combinado mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Para obtener más información, consulte [Tutorial: poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCToolBarEditBoxButton` clase. En el ejemplo se muestra cómo especificar que un usuario puede ajustar el botón durante la personalización, especificar que un borde del botón se muestra cuando un usuario hace clic en el botón, establecer el texto en el control de cuadro de texto, especificar la apariencia de estilo plano de botones del cuadro de edición en la aplicación y especifique el estilo de un control de cuadro de edición de barra de herramientas.  
  
 [!code-cpp[NVC_MFC_RibbonApp Nº 40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 `CMFCToolBarEditBoxButton` 
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbareditboxbutton.h  
  
##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched  
 Especifica si un usuario puede ajustar el botón durante la personalización.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo no permite al usuario ajustar un botón de barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) al permitir que el usuario ajustar un botón de barra de herramientas del cuadro de edición durante la personalización.  
  
##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton  
 Construye un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objeto.  
  
```  
CMFCToolBarEditBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=ES_AUTOHSCROLL,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 Especifica el identificador del control.  
  
 [in] `iImage`  
 Especifica el índice de base cero de una imagen de la barra de herramientas. La imagen se encuentra en la [CMFCToolBarImages clase](../../mfc/reference/cmfctoolbarimages-class.md) objeto que [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md) clase mantiene.  
  
 [in] `dwStyle`  
 Especifica el estilo del control de edición.  
  
 [in] `iWidth`  
 Especifica el ancho en píxeles del control de edición.  
  
### <a name="remarks"></a>Comentarios  
 El constructor predeterminado establece el estilo del control de edición a la combinación siguiente:  
  
 `WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL`  
  
 El ancho predeterminado del control es 150 píxeles.  
  
##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom  
 Copia las propiedades de otro botón de barra de herramientas a la actual.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Una referencia al botón de origen desde el que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para copiar otro botón de barra de herramientas en este botón de barra de herramientas. `src`debe ser del tipo `CMFCToolBarEditBoxButton`.  
  
##  <a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit  
 Crea un nuevo control de edición en el botón.  
  
```  
virtual CEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `[in] pWndParent`  
 Especifica la ventana primaria del control de edición. No debe ser NULL.  
  
 `[in] rect`  
 Especifica el tamaño y la posición del control de edición.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero para el control de edición recién creada; es `NULL` si la creación del control y los datos adjuntos producirá un error.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CMFCToolBarEditBoxButton` objeto en dos pasos. Llame primero al constructor y, a continuación, llame a `CreateEdit`, que crea el control de edición de Windows y lo adjunta a la `CMFCToolBarEditBoxButton` objeto.  
  
##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd  
 Recupera el primer `CMFCToolBarEditBoxButton` objeto de la aplicación con el identificador de comando especificado.  
  
```  
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando del botón para recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera `CMFCToolBarEditBoxButton` objeto de la aplicación que tiene el identificador de comando especificado, o `NULL` si no existe el objeto no existe.  
  
### <a name="remarks"></a>Comentarios  
 Este método de utilidad compartida se utiliza por métodos como [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) y [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) establecer u obtener el texto del primer control de barra de herramientas de cuadro de edición con el identificador de comando especificado.  
  
##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll  
 Recupera el texto del primer control de barra de herramientas de cuadro de edición con el identificador de comando especificado.  
  
```  
static CString __stdcall GetContentsAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando del botón desde el que se va a recuperar contenido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene el texto del primer control de barra de herramientas de cuadro de edición con el identificador de comando especificado.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve una cadena vacía si no hay ningún `CMFCToolBarEditBoxButton` objetos tienen el identificador del comando especificado.  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID  
 Recupera el identificador de recurso del menú contextual que está asociado con el botón.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de recurso del menú contextual que está asociado con el botón o 0 si el botón no tiene ningún menú contextual asociado.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario hace clic con un botón en el botón.  
  
##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder  
 Recupera el rectángulo delimitador de la parte de edición del botón de cuadro de edición.  
  
```  
virtual void GetEditBorder(CRect& rectBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectBorder`  
 Una referencia a la `CRect` objeto que recibe el rectángulo delimitador.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera el rectángulo delimitador del control de edición en coordenadas de cliente. Se expande el tamaño del rectángulo en cada dirección de un píxel.  
  
 El [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) método llama a este método cuando dibuja el borde alrededor de un `CMFCToolBarEditBoxButton` objeto.  
  
##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox  
 Devuelve un puntero a la [clase CEdit](../../mfc/reference/cedit-class.md) control que está incrustada en el botón.  
  
```  
CEdit* GetEditBox() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [clase CEdit](../../mfc/reference/cedit-class.md) control que contiene el botón. Es `NULL` si el `CEdit` control aún no se ha creado.  
  
### <a name="remarks"></a>Comentarios  
 Crear el `CEdit` control mediante una llamada a [CMFCToolBarEditBoxButton::CreateEdit](#createedit).  
  
##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd  
 Recupera el identificador de ventana que está asociado con el botón de barra de herramientas.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de ventana que está asociado con el botón.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida el [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) método devolviendo el identificador de ventana de la parte del control de edición del botón de cuadro de edición.  
  
##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect  
 Recupera la región del área cliente del botón que se debe volver a dibujar.  
  
```  
virtual const CRect GetInvalidateRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CRect` objeto que especifica la región que se debe volver a dibujar.  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base, [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), mediante la inclusión en la región del área de la etiqueta de texto.  
  
##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder  
 Determina si un borde del botón se muestra cuando un usuario hace clic en el botón.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si un botón muestra su borde cuando selecciona; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base, [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), devolviendo un valor distinto de cero si el control es visible.  
  
##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode  
 Determina si los botones del cuadro de edición tienen un estilo plano.  
  
```  
static BOOL __stdcall IsFlatMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si los botones tienen un estilo plano; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones del cuadro de edición tienen un estilo plano. Use la [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) método para cambiar la apariencia de estilo plano de la aplicación.  
  
##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand  
 Especifica si el botón procesa el [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iNotifyCode`  
 El mensaje de notificación que está asociado con el comando.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón se procesa la `WM_COMMAND` mensaje, o `FALSE` para indicar que el mensaje debe ser administrado por la barra de herramientas primario.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando está a punto de enviar un [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje a la ventana primaria.  
  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) mediante el procesamiento de la [EN_UPDATE](http://msdn.microsoft.com/library/windows/desktop/bb761687) notificación. Para cada cuadro de edición con el mismo identificador de comando como este objeto, Establece la etiqueta de texto a la etiqueta de texto de este objeto.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage  
 Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) mediante la copia de las propiedades desde el control de cuadro de edición en cualquier barra de herramientas que tiene el mismo identificador de comando como este objeto. Este método no hace nada si ninguna barra de herramientas tiene un control de cuadro de edición que tiene el mismo identificador de comando como este objeto.  
  
 Para obtener más información sobre la **personalizar** cuadro de diálogo, vea [CMFCToolBarsCustomizeDialog clase](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd  
 Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Un puntero a la nueva ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) al volver a crear interno `CEdit` objeto.  
  
##  <a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick  
 Lo llama el marco cuando el usuario hace clic en el botón del mouse.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Sin usar.  
  
 [in] `bDelay`  
 Sin usar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el botón procesa el mensaje haga clic en; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) que devuelva un valor distinto de cero si el fax interno `CEdit` objeto está visible.  
  
##  <a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor  
 Lo llama el marco cuando la barra de herramientas primario controla un `WM_CTLCOLOR` mensaje.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 El contexto de dispositivo que muestra el botón.  
  
 [in] `nCtlColor`  
 Sin usar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el pincel de ventana global.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) al establecer los colores de texto y de fondo del contexto de dispositivo proporcionado en el texto global y los colores de fondo, respectivamente.  
  
 Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged  
 Lo llama el marco de trabajo cuando ha cambiado la fuente global.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), cambie la fuente del control para que la fuente global.  
  
 Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove  
 Llamado por el marco de trabajo cuando se mueve la barra de herramientas primario.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase predeterminada ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) mediante la actualización de la posición de los internos `CEdit` objeto  
  
##  <a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow  
 Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 Especifica si el botón está visible. Si este parámetro es `TRUE`, el botón está visible. En caso contrario, el botón no está visible.  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) que muestre el botón si `bShow` es `TRUE`. En caso contrario, este método oculta el botón.  
  
##  <a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize  
 Lo llama el marco de trabajo cuando la barra de herramientas primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iSize`  
 El nuevo ancho del botón, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase de forma predeterminada, [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), actualizando el tamaño y la posición de interno `CEdit` objeto.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip  
 Llamado por el marco de trabajo cuando la barra de herramientas principal actualiza el texto de información sobre herramientas.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Sin usar.  
  
 [in] `iButtonIndex`  
 Sin usar.  
  
 [in] `wndToolTip`  
 El control que muestra el texto de información sobre herramientas.  
  
 [out] `str`  
 Un `CString` objeto que recibe el texto actualizado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método actualiza el texto de información sobre herramientas; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) al mostrar el texto de información sobre herramientas que está asociado a la parte de edición del botón. Si interno `CEdit` objeto es `NULL` o el identificador de ventana de la `CEdit` objeto no identifica una ventana existente, este método no hace nada y devuelve `FALSE`.  
  
##  <a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents  
 Establece el texto en el control de cuadro de texto.  
  
```  
virtual void SetContents(const CString& sContents);
```  
  
### <a name="parameters"></a>Parámetros  
 `[in] sContents`  
 Especifica el nuevo texto para establecer.  
  
##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll  
 Busca un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objeto que tiene un identificador de comando especificado y establece el texto especificado en su cuadro de texto.  
  
```  
static BOOL SetContentsAll(
    UINT uiCmd,  
    const CString& strContents);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 Especifica el identificador de comando del control para el que se cambiará el texto.  
  
 [in] `strContents`  
 Especifica el nuevo texto para establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha establecido el texto; 0 si el `CMFCToolBarEditBoxButton` control con el identificador de comando especificado no existe.  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID  
 Especifica el identificador de recurso del menú contextual que está asociado con el botón.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de recurso del menú contextual.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario seleccione el botón de barra de herramientas.  
  
##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode  
 Especifica la apariencia de estilo plano de botones del cuadro de edición en la aplicación.  
  
```  
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bFlat`  
 El estilo plano de botones del cuadro de edición. Si este parámetro es `TRUE`, la apariencia de estilo plano está habilitada; en caso contrario, se deshabilita la apariencia de estilo plano.  
  
### <a name="remarks"></a>Comentarios  
 El estilo plano predeterminado para los botones de cuadro de edición es `TRUE`. Use la [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) método para recuperar la apariencia de estilo plano de la aplicación.  
  
##  <a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle  
 Especifica el estilo de una barra de herramientas de control de cuadro de edición.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nStyle`  
 Un estilo nuevo para establecer.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) a `nStyle` también deshabilita el cuadro de texto cuando la aplicación está en modo de personalizar y lo habilita cuando la aplicación no está en modo de personalizar (vea [CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) y [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Vea [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md) para obtener una lista de marcas de estilo válido.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)




