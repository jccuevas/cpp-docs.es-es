---
title: CTabCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTabCtrl
dev_langs:
- C++
helpviewer_keywords:
- tab controls
- CTabCtrl class, common controls
- CTabCtrl class
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
caps.latest.revision: 21
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
ms.openlocfilehash: e1d8497b444e4dd5ee1e2803c1a763f67e2e0054
ms.lasthandoff: 02/24/2017

---
# <a name="ctabctrl-class"></a>CTabCtrl (clase)
Proporciona la funcionalidad del control de pestaña común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTabCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTabCtrl::CTabCtrl](#ctabctrl)|Construye un objeto `CTabCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTabCtrl::AdjustRect](#adjustrect)|Calcula el área de presentación de un control de ficha tiene un rectángulo de la ventana, o calcula el rectángulo de ventana que corresponde a un área de presentación determinado.|  
|[CTabCtrl::Create](#create)|Crea un control de pestaña y lo adjunta a una instancia de un `CTabCtrl` objeto.|  
|[CTabCtrl::CreateEx](#createex)|Crea un control de ficha con los estilos extendidos de Windows especificados y lo asocia a una instancia de un `CTabCtrl` objeto.|  
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Quita todos los elementos de un control de ficha.|  
|[CTabCtrl::DeleteItem](#deleteitem)|Quita un elemento de un control de ficha.|  
|[CTabCtrl::DeselectAll](#deselectall)|Restablece los elementos en un control de ficha, desactivación que se presionaron.|  
|[CTabCtrl::DrawItem](#drawitem)|Dibuja un elemento especificado de un control de ficha.|  
|[CTabCtrl::GetCurFocus](#getcurfocus)|Recupera la ficha con el foco actual del control de ficha.|  
|[CTabCtrl::GetCurSel](#getcursel)|Determina la ficha actualmente seleccionada en un control de ficha.|  
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que están actualmente en uso para el control de ficha.|  
|[CTabCtrl::GetImageList](#getimagelist)|Recupera la lista de imágenes asociada a un control de ficha.|  
|[CTabCtrl::GetItem](#getitem)|Recupera información sobre una ficha en un control de ficha.|  
|[CTabCtrl::GetItemCount](#getitemcount)|Recupera el número de fichas del control de ficha.|  
|[CTabCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador de una ficha en un control de ficha.|  
|[CTabCtrl::GetItemState](#getitemstate)|Recupera el estado del elemento de control de ficha indicado.|  
|[CTabCtrl::GetRowCount](#getrowcount)|Recupera el número actual de filas de las fichas en un control de ficha.|  
|[CTabCtrl::GetToolTips](#gettooltips)|Recupera el identificador del control de información sobre herramienta asociado a un control de ficha.|  
|[CTabCtrl::HighlightItem](#highlightitem)|Establece el estado de resaltado de un elemento de ficha.|  
|[CTabCtrl::HitTest](#hittest)|Determina qué ficha, si existe, está en una posición de pantalla especificada.|  
|[CTabCtrl:: InsertItem](#insertitem)|Inserta una nueva pestaña en un control de ficha.|  
|[CTabCtrl::RemoveImage](#removeimage)|Quita una imagen de la lista de imágenes de un control de ficha.|  
|[CTabCtrl::SetCurFocus](#setcurfocus)|Establece el foco en una ficha especificada en un control de ficha.|  
|[CTabCtrl::SetCurSel](#setcursel)|Selecciona una ficha en un control de ficha.|  
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para un control de ficha.|  
|[CTabCtrl::SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de ficha.|  
|[CTabCtrl::SetItem](#setitem)|Establece algunos o todos los atributos de la ficha.|  
|[CTabCtrl::SetItemExtra](#setitemextra)|Establece el número de bytes por ficha reservado para los datos definidos por la aplicación en un control de ficha.|  
|[CTabCtrl::SetItemSize](#setitemsize)|Establece el ancho y alto de un elemento.|  
|[CTabCtrl::SetItemState](#setitemstate)|Establece el estado del elemento de control de ficha indicado.|  
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Establece el ancho mínimo de elementos en un control de ficha.|  
|[CTabCtrl::SetPadding](#setpadding)|Establece la cantidad de espacio (relleno) en torno a cada ficha icono y una etiqueta de un control de ficha.|  
|[CTabCtrl::SetToolTips](#settooltips)|Asigna un control de información sobre herramientas a un control de ficha.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control de pestaña" es análogo a los divisores de un bloc de notas o las etiquetas de un archivador. Mediante el uso de un control de ficha, una aplicación puede definir varias páginas para la misma área de un cuadro de diálogo o de una ventana. Cada página consta de un conjunto de información o un grupo de controles que muestra la aplicación cuando el usuario selecciona la pestaña correspondiente. Un tipo especial de control de pestaña muestra las fichas que parecen botones. Al hacer clic en un botón debe realizar inmediatamente un comando en lugar de mostrar una página.  
  
 Este control (y por tanto la `CTabCtrl` clase) está disponible sólo para los programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Para obtener más información sobre el uso de `CTabCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [utilizar CTabCtrl](../../mfc/using-ctabctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="a-nameadjustrecta--ctabctrladjustrect"></a><a name="adjustrect"></a>CTabCtrl::AdjustRect  
 Calcula el área de presentación de un control de ficha tiene un rectángulo de la ventana, o calcula el rectángulo de ventana que corresponde a un área de presentación determinado.  
  
```  
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `bLarger`  
 Indica qué operación debe realizar. Si este parámetro es **TRUE**, `lpRect` especifica un rectángulo de presentación y recibe el rectángulo de la ventana correspondiente. Si este parámetro es **FALSE**, `lpRect` especifica un rectángulo de la ventana y recibe el rectángulo de presentación correspondiente.  
  
 `lpRect`  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que especifica el rectángulo especificado y recibe el rectángulo calculado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CTabCtrl](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]  
  
##  <a name="a-namecreatea--ctabctrlcreate"></a><a name="create"></a>CTabCtrl::Create  
 Crea un control de pestaña y lo adjunta a una instancia de un `CTabCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de ficha. Aplicar cualquier combinación de [estilos de control de ficha](http://msdn.microsoft.com/library/windows/desktop/bb760549), descrita en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Consulte **comentarios** para obtener una lista de estilos de ventana que también se pueden aplicar al control.  
  
 `rect`  
 Especifica el tamaño y la posición del control de ficha. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.  
  
 `pParentWnd`  
 Especifica la ventana primaria del control de ficha, normalmente un `CDialog`. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control de ficha  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la inicialización del objeto es correcto; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CTabCtrl` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de pestaña y lo adjunta a la `CTabCtrl` objeto.  
  
 Además de los estilos de control de ficha, puede aplicar los siguientes estilos de ventana para un control de ficha:  
  
- **WS_CHILD** crea una ventana secundaria que representa el control de ficha. No se puede usar con el `WS_POPUP` estilo.  
  
- **WS_VISIBLE** crea un control de ficha que esté visible inicialmente.  
  
- **WS_DISABLED** crea una ventana que está inicialmente deshabilitada.  
  
- **WS_GROUP** especifica el primer control de un grupo de controles en la que el usuario puede mover de un control a la siguiente con las teclas de dirección. Todos los controles definidos con el **WS_GROUP** después de que el primer control pertenecen al mismo grupo de estilos. El siguiente control con el **WS_GROUP** estilo finaliza el grupo de estilo y comienza el siguiente grupo (es decir, finaliza un grupo donde comienza la siguiente).  
  
- **WS_TABSTOP** especifica cualquier número de controles a través del cual el usuario puede mover mediante la tecla TAB. La tecla TAB mueve el usuario al siguiente control especificado por la **WS_TABSTOP** estilo.  
  
 Para crear un control de ficha con estilos de ventana extendidos, llame a [CTabCtrl::CreateEx](#createex) en lugar de **crear**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTabCtrl&#2;](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]  
  
##  <a name="a-namecreateexa--ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CTabCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Especifica el estilo del control de ficha. Aplicar cualquier combinación de [estilos de control de ficha](http://msdn.microsoft.com/library/windows/desktop/bb760549), descrita en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Consulte **comentarios** en [crear](#create) para obtener una lista de estilos de ventana que también se pueden aplicar al control.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente `pParentWnd`.  
  
 `pParentWnd`  
 Puntero a la ventana que es principal el control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 0 en caso contrario, es distinto de cero si se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
 `CreateEx`crea el control con los estilos extendidos de Windows especificados por `dwExStyle`. Conjunto específico de un control mediante estilos extendidos [SetExtendedStyle](#setextendedstyle). Por ejemplo, utilice `CreateEx` para establecer estos estilos como **WS_EX_CONTEXTHELP**, pero usar `SetExtendedStyle` para establecer estos estilos como **TCS_EX_FLATSEPARATORS**. Para obtener más información, consulte los estilos que se describe en [estilos extendidos de Control de ficha](http://msdn.microsoft.com/library/windows/desktop/bb760546) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namectabctrla--ctabctrlctabctrl"></a><a name="ctabctrl"></a>CTabCtrl::CTabCtrl  
 Construye un objeto `CTabCtrl`.  
  
```  
CTabCtrl();
```  
  
##  <a name="a-namedeleteallitemsa--ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl::DeleteAllItems  
 Quita todos los elementos de un control de ficha.  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-namedeleteitema--ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl::DeleteItem  
 Quita el elemento especificado de un control de ficha.  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 Valor de base cero del elemento que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTabCtrl&3;](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]  
  
##  <a name="a-namedeselectalla--ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl::DeselectAll  
 Restablece los elementos en un control de ficha, desactivación que se presionaron.  
  
```  
void DeselectAll(BOOL fExcludeFocus);
```  
  
### <a name="parameters"></a>Parámetros  
 *fExcludeFocus*  
 Indicador que especifica el ámbito de la desactivación del elemento. Si este parámetro se establece en **FALSE**, se restablecerán todos los botones de ficha. Si se establece en **TRUE**, a continuación, se restablecerán todos los elementos de ficha, excepto la seleccionada actualmente.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32, [TCM_DESELECTALL](http://msdn.microsoft.com/library/windows/desktop/bb760579), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namedrawitema--ctabctrldrawitem"></a><a name="drawitem"></a>CTabCtrl::DrawItem  
 Llamado por el marco cuando un aspecto visual de un cambios de control de ficha dibujado por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero a un [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) estructura que describe el elemento que se va a pintar.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza.  
  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar un dibujados por el propietario del dibujo `CTabCtrl` objeto.  
  
 La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para el contexto de presentación proporcionado en `lpDrawItemStruct` antes de este miembro de función termina.  
  
##  <a name="a-namegetcurfocusa--ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CTabCtrl::GetCurFocus  
 Recupera el índice de la pestaña con el foco actual.  
  
```  
int GetCurFocus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la ficha con el foco actual.  
  
##  <a name="a-namegetcursela--ctabctrlgetcursel"></a><a name="getcursel"></a>CTabCtrl::GetCurSel  
 Recupera la ficha actualmente seleccionada en un control de ficha.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la ficha seleccionada si se realiza correctamente o – 1 si ninguna ficha está seleccionada.  
  
##  <a name="a-namegetextendedstylea--ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle  
 Recupera los estilos extendidos que están actualmente en uso para el control de ficha.  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Representa los estilos extendidos actualmente en uso para el control de ficha. Este valor es una combinación de [estilos extendidos de control de ficha](http://msdn.microsoft.com/library/windows/desktop/bb760546), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760585), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetimagelista--ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl::GetImageList  
 Recupera la lista de imágenes asociada a un control de pestaña.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un puntero a la lista de imágenes de la pestaña de control; de lo contrario, **NULL**.  
  
##  <a name="a-namegetitema--ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl::GetItem  
 Recupera información sobre una ficha en un control de ficha.  
  
```  
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 Índice de base cero de la ficha.  
  
 `pTabCtrlItem`  
 Puntero a un [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) estructura que se utiliza para especificar la información para recuperar. También se utiliza para recibir información acerca de la ficha. Esta estructura se utiliza con la `InsertItem`, `GetItem`, y `SetItem` funciones miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si es correcto; **FALSE** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se envía el mensaje, el **máscara** miembro especifica qué atributos se devolverán. Si el **máscara** miembro especifica la `TCIF_TEXT` valor, el **pszText** miembro debe contener la dirección del búfer que recibe el texto del elemento y el **cchTextMax** miembro debe especificar el tamaño del búfer.  
  
 **máscara**  
 Valor que especifica qué `TCITEM` miembros para recuperar o establecer de estructura. Este miembro puede ser cero o una combinación de los siguientes valores:  
  
- `TCIF_TEXT`El **pszText** miembro es válido.  
  
- `TCIF_IMAGE`El `iImage` miembro es válido.  
  
- `TCIF_PARAM`El **lParam** miembro es válido.  
  
- `TCIF_RTLREADING`El texto de **pszText** se muestra con orden de lectura de derecha a izquierda en los sistemas hebreo o árabe.  
  
- `TCIF_STATE`El **"_mfc_CTabCtrl.3a3a.GetItem"** miembro es válido.  
  
 **pszText**  
 Puntero a una cadena terminada en null que contiene el texto de la ficha si la estructura contiene información sobre una pestaña. Si está recibiendo información de la estructura, este miembro especifica la dirección del búfer que recibe el texto de la ficha.  
  
 **cchTextMax**  
 Tamaño del búfer que señala **pszText**. Este miembro se omite si la estructura no está recibiendo información.  
  
 `iImage`  
 Índice en el control de pestaña lista de imágenes, o – 1 si no hay ninguna imagen de la ficha.  
  
 **lParam**  
 Datos definidos por la aplicación asociadas a la ficha. Si hay más de cuatro bytes de datos definidos por la aplicación por ficha, una aplicación debe definir la estructura y usarla en lugar de la `TCITEM` (estructura). El primer miembro de la estructura de aplicación debe ser un [TCITEMHEADER](http://msdn.microsoft.com/library/windows/desktop/bb760556)estructura. El **TCITEMHEADER** estructura es idéntica a la `TCITEM` estructura, pero sin la **lParam** miembro. La diferencia entre el tamaño de la estructura y el tamaño de la **TCITEMHEADER** estructura es igual al número de bytes adicionales por ficha.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTabCtrl Nº&4;](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]  
  
##  <a name="a-namegetitemcounta--ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl::GetItemCount  
 Recupera el número de fichas del control de ficha.  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos del control de ficha.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="a-namegetitemrecta--ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl::GetItemRect  
 Recupera el rectángulo delimitador de la ficha especificada en un control de ficha.  
  
```  
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 Índice de base cero del elemento de ficha.  
  
 `lpRect`  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe el rectángulo delimitador de la ficha. Estas coordenadas Usar modo de asignación de la ventanilla actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="a-namegetitemstatea--ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl::GetItemState  
 Recupera el estado del elemento de control de ficha identificado por `nItem`.  
  
```  
DWORD GetItemState(
    int nItem,  
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 El número de índice de base cero del elemento para el que se va a recuperar la información de estado.  
  
 `dwMask`  
 Máscara que especifica cuál de estado del elemento de la marca para devolver. Para obtener una lista de valores, vea el miembro de la máscara de la [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) estructura, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un `DWORD` valor recibir la información de estado. Puede presentar uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|Se selecciona el elemento de control de ficha.|  
|**TCIS_HIGHLIGHTED**|Se resalta el elemento de control de ficha y la ficha y el texto se dibujan utilizando el color de resaltado actual. Cuando se utiliza el color de resaltado, se trata de una interpolación es true, no un color interpolado.|  
  
### <a name="remarks"></a>Comentarios  
 Estado de un elemento especificado por la **"_mfc_CTabCtrl.3a3a.GetItem"** miembro de la `TCITEM` estructura.  
  
##  <a name="a-namegetrowcounta--ctabctrlgetrowcount"></a><a name="getrowcount"></a>CTabCtrl::GetRowCount  
 Recupera el número actual de filas en un control de ficha.  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas de fichas del control de ficha.  
  
### <a name="remarks"></a>Comentarios  
 Ficha sólo los controles que tienen la **TCS_MULTILINE** estilo puede tener varias filas de fichas.  
  
##  <a name="a-namegettooltipsa--ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl::GetToolTips  
 Recupera el identificador del control de información sobre herramienta asociado a un control de ficha.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del control de información sobre herramientas si se realiza correctamente; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Un control de ficha crea un control de información sobre herramienta si tiene la **TCS_TOOLTIPS** estilo. También puede asignar un control de información sobre herramientas a un control de ficha mediante el `SetToolTips` función miembro.  
  
##  <a name="a-namehighlightitema--ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl::HighlightItem  
 Establece el estado de resaltado de un elemento de ficha.  
  
```  
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `idItem`  
 Índice de base cero de un elemento de control de ficha.  
  
 `fHighlight`  
 Valor que especifica la configuración del estado de resaltado. Si este valor es **TRUE**, se resalta la pestaña; si **FALSE**, la ficha se establece en su estado predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el mensaje de Win32 [TCM_HIGHLIGHTITEM](http://msdn.microsoft.com/library/windows/desktop/bb760602), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namehittesta--ctabctrlhittest"></a><a name="hittest"></a>CTabCtrl::HitTest  
 Determina qué ficha, si existe, está en la posición de pantalla especificada.  
  
```  
int HitTest(TCHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pHitTestInfo`  
 Puntero a un [TCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760553) estructura, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)], que especifica la posición de la pantalla para probar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el índice de base cero de la ficha o – 1 si ninguna ficha está en la posición especificada.  
  
##  <a name="a-nameinsertitema--ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl:: InsertItem  
 Inserta una nueva pestaña en un control de ficha existente.  
  
```  
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

 
LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

 
LONG InsertItem(
    UINT nMask,  
    int nItem,  
    LPCTSTR lpszItem,  
    int nImage,  
    LPARAM lParam,  
    DWORD dwState,  
    DWORD dwStateMask);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 Índice de base cero de la nueva pestaña.  
  
 `pTabCtrlItem`  
 Puntero a un [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) estructura que especifica los atributos de la ficha.  
  
 `lpszItem`  
 Dirección de una cadena terminada en null que contiene el texto de la ficha.  
  
 `nImage`  
 Índice de base cero de una imagen para insertar una lista de imágenes.  
  
 `nMask`  
 Especifica qué `TCITEM` estructura atributos van a establecer. Puede ser cero o una combinación de los siguientes valores:  
  
- `TCIF_TEXT`El **pszText** miembro es válido.  
  
- `TCIF_IMAGE`El `iImage` miembro es válido.  
  
- `TCIF_PARAM`El **lParam** miembro es válido.  
  
- `TCIF_RTLREADING`El texto de **pszText** se muestra con orden de lectura de derecha a izquierda en los sistemas hebreo o árabe.  
  
- `TCIF_STATE`El **"_mfc_CTabCtrl.3a3a.GetItem"** miembro es válido.  
  
 `lParam`  
 Datos definidos por la aplicación asociadas a la ficha.  
  
 `dwState`  
 Especifica los valores de los Estados del elemento. Para obtener más información, consulte [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *dwStateMask*  
 Especifica que los Estados que se van a establecer. Para obtener más información, consulte [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la nueva pestaña, si es correcto; de lo contrario,-1.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTabCtrl&#5;](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]  
  
##  <a name="a-nameremoveimagea--ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl::RemoveImage  
 Quita la imagen especificada de la lista de imágenes de un control de ficha.  
  
```  
void RemoveImage(int nImage);
```  
  
### <a name="parameters"></a>Parámetros  
 `nImage`  
 Índice de base cero de la imagen para quitar.  
  
### <a name="remarks"></a>Comentarios  
 El control de pestaña actualiza el índice de la imagen de la ficha para que cada ficha permanece asociado a la misma imagen.  
  
##  <a name="a-namesetcurfocusa--ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CTabCtrl::SetCurFocus  
 Establece el foco en una ficha especificada en un control de ficha.  
  
```  
void SetCurFocus(int nItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 Especifica el índice de la pestaña que recibe el foco.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETCURFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb760610), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetcursela--ctabctrlsetcursel"></a><a name="setcursel"></a>CTabCtrl::SetCurSel  
 Selecciona una ficha en un control de ficha.  
  
```  
int SetCurSel(int nItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 Índice de base cero del elemento que va a seleccionar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la ficha seleccionada anteriormente, si se realiza correctamente, de lo contrario,-1.  
  
### <a name="remarks"></a>Comentarios  
 Un control de ficha no envía una **TCN_SELCHANGING** o **TCN_SELCHANGE** recibe un mensaje de notificación cuando se selecciona una ficha utilizando esta función. Estas notificaciones se envían mediante **WM_NOTIFY**, cuando el usuario hace clic o utiliza el teclado para cambiar de ficha.  
  
##  <a name="a-namesetextendedstylea--ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle  
 Establece los estilos extendidos para un control de ficha.  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwNewStyle`  
 Valor que especifica una combinación de ficha control estilos extendidos.  
  
 `dwExMask`  
 Un `DWORD` valor que indica qué estilos en `dwNewStyle` a verse afectado. Sólo los estilos extendidos en `dwExMask` se van a cambiar. Todos los demás estilos se conservará tal cual. Si este parámetro es cero, entonces todos los estilos en `dwNewStyle` se verá afectado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `DWORD` valor que contiene el anterior [estilos extendidos de control de ficha](http://msdn.microsoft.com/library/windows/desktop/bb760546), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760627), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetimagelista--ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl::SetImageList  
 Asigna una lista de imágenes a un control de ficha.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 `pImageList`  
 Puntero a la lista de imágenes que se asignará al control de ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la lista de la imagen anterior o **NULL** si no hay ninguna lista de imágenes anteriores.  
  
##  <a name="a-namesetitema--ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl::SetItem  
 Establece algunos o todos los atributos de la ficha.  
  
```  
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 Índice de base cero del elemento.  
  
 `pTabCtrlItem`  
 Puntero a un [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) estructura que contiene los atributos del elemento nuevo. El **máscara** miembro especifica qué atributos que se van a establecer. Si el **máscara** miembro especifica la `TCIF_TEXT` valor, el **pszText** miembro es la dirección de una cadena terminada en null y el **cchTextMax** miembro se omite.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [GetItem](#getitem).  
  
##  <a name="a-namesetitemextraa--ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl::SetItemExtra  
 Establece el número de bytes por ficha reservado para los datos definidos por la aplicación en un control de ficha.  
  
```  
BOOL SetItemExtra(int nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 El número de bytes adicionales que se va a establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETITEMEXTRA](http://msdn.microsoft.com/library/windows/desktop/bb760633), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetitemsizea--ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl::SetItemSize  
 Establece el ancho y alto de los elementos de control de pestaña.  
  
```  
CSize SetItemSize(CSize size);
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 El nuevo ancho y alto, en píxeles, de los elementos de control de pestaña.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el ancho y el alto antiguos de los elementos de control de pestaña.  
  
##  <a name="a-namesetitemstatea--ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl::SetItemState  
 Establece el estado del elemento de control de ficha identificado por `nItem`.  
  
```  
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItem`  
 El número de índice de base cero del elemento para el que se va a establecer información de estado.  
  
 `dwMask`  
 Especifica cuál de estado del elemento marcas para establecer la máscara. Para obtener una lista de valores, vea el miembro de la máscara de la [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) estructura, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwState`  
 Una referencia a un `DWORD` valor que contiene la información de estado. Puede presentar uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|Se selecciona el elemento de control de ficha.|  
|**TCIS_HIGHLIGHTED**|Se resalta el elemento de control de ficha y la ficha y el texto se dibujan utilizando el color de resaltado actual. Cuando se utiliza el color de resaltado, se trata de una interpolación es true, no un color interpolado.|  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-namesetmintabwidtha--ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth  
 Establece el ancho mínimo de elementos en un control de ficha.  
  
```  
int SetMinTabWidth(int cx);
```  
  
### <a name="parameters"></a>Parámetros  
 `cx`  
 Ancho mínimo que se establezca para un elemento de control de ficha. Si este parámetro se establece en -1, el control utiliza el ancho de tabulación predeterminada.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho mínimo de ficha anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETMINTABWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760637), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetpaddinga--ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl::SetPadding  
 Establece la cantidad de espacio (relleno) en torno a cada ficha icono y una etiqueta de un control de ficha.  
  
```  
void SetPadding(CSize size);
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 Establece la cantidad de espacio (relleno) en torno a cada ficha icono y una etiqueta de un control de ficha.  
  
##  <a name="a-namesettooltipsa--ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl::SetToolTips  
 Asigna un control de información sobre herramientas a un control de ficha.  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndTip`  
 Identificador del control de información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Puede obtener el control de información sobre herramientas asociado a un control de ficha mediante una llamada a `GetToolTips`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CHeaderCtrl (clase)](../../mfc/reference/cheaderctrl-class.md)   
 [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)

