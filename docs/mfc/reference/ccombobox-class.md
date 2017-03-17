---
title: CComboBox (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
dev_langs:
- C++
helpviewer_keywords:
- combo boxes, CComboBox objects
- CComboBox class
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: 25
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
ms.openlocfilehash: 5328c245e0d662c4701042b37c16870d6b1e33c7
ms.lasthandoff: 02/24/2017

---
# <a name="ccombobox-class"></a>CComboBox (clase)
Proporciona la funcionalidad de un cuadro combinado de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CComboBox : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComboBox::CComboBox](#ccombobox)|Construye un objeto `CComboBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComboBox:: AddString](#addstring)|Agrega una cadena al final de la lista en el cuadro de lista de un cuadro combinado o en la posición ordenada para cuadros de lista con el **CBS_SORT** estilo.|  
|[CComboBox::Clear](#clear)|Elimina (borra) la selección actual, si existe alguno, en el control de edición.|  
|[CComboBox::CompareItem](#compareitem)|Llamado por el marco de trabajo para determinar la posición relativa de un nuevo elemento de lista en un cuadro combinado ordenado dibujado por el propietario.|  
|[CComboBox::Copy](#copy)|Copia la selección actual, si hay alguno, en el Portapapeles en **CF_TEXT** formato.|  
|[CComboBox::Create](#create)|Crea el cuadro combinado y lo adjunta a la `CComboBox` objeto.|  
|[CComboBox::Cut](#cut)|(Cortes) se elimina la selección actual, si existe alguno, en la edición controlar y copia el texto eliminado en el Portapapeles en **CF_TEXT** formato.|  
|[CComboBox::DeleteItem](#deleteitem)|Lo llama el marco de trabajo cuando se elimina un elemento de lista de un cuadro combinado dibujado por el propietario.|  
|[CComboBox::DeleteString](#deletestring)|Elimina una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::Dir](#dir)|Agrega una lista de nombres de archivo en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::DrawItem](#drawitem)|Llamado por el marco cuando un aspecto visual de cambia de un cuadro combinado dibujado por el propietario.|  
|[CComboBox::FindString](#findstring)|Busca la primera cadena que contiene el prefijo especificado en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::FindStringExact](#findstringexact)|Busca la primera cadena de cuadro de lista (en un cuadro combinado) que coincide con la cadena especificada.|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Recupera información sobre la `CComboBox` objeto.|  
|[CComboBox::GetCount](#getcount)|Recupera el número de elementos en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::GetCueBanner](#getcuebanner)|Obtiene el texto de indicación que se muestra para un control de cuadro combinado.|  
|[CComboBox::GetCurSel](#getcursel)|Recupera el índice del elemento actualmente seleccionado, si existe alguno, en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Recupera las coordenadas de pantalla del cuadro de lista (desplegable) visible de un cuadro combinado desplegable.|  
|[CComboBox::GetDroppedState](#getdroppedstate)|Determina si el cuadro de lista de un cuadro combinado desplegable está visible (desplegada).|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Recupera el ancho mínimo permitido para la parte de cuadro de lista desplegable de un cuadro combinado.|  
|[CComboBox::GetEditSel](#geteditsel)|Obtiene las posiciones de carácter inicial y final de la selección actual del control de edición de un cuadro combinado.|  
|[CComboBox::GetExtendedUI](#getextendedui)|Determina si un cuadro combinado tiene la interfaz de usuario predeterminada o la interfaz de usuario extendida.|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Devuelve el ancho en píxeles que la parte de cuadro de lista del cuadro combinado se puede desplazar horizontalmente.|  
|[CComboBox::GetItemData](#getitemdata)|Recupera el valor de 32 bits proporcionada por la aplicación asociado con el elemento de cuadro combinado especificado.|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Recupera el puntero de 32 bits proporcionada por la aplicación que está asociado con el elemento de cuadro combinado especificado.|  
|[CComboBox::GetItemHeight](#getitemheight)|Recupera el alto de los elementos de lista en un cuadro combinado.|  
|[CComboBox::GetLBText](#getlbtext)|Obtiene una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|Obtiene la longitud de una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::GetLocale](#getlocale)|Recupera el identificador de configuración regional para un cuadro combinado.|  
|[CComboBox::GetMinVisible](#getminvisible)|Obtiene el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|  
|[CComboBox::GetTopIndex](#gettopindex)|Devuelve el índice del primer elemento visible en la parte de cuadro de lista del cuadro combinado.|  
|[CComboBox::InitStorage](#initstorage)|Preasigna los bloques de memoria para los elementos y las cadenas en la parte de cuadro de lista del cuadro combinado.|  
|[CComboBox::InsertString](#insertstring)|Inserta una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::LimitText](#limittext)|Limita la longitud del texto que el usuario puede escribir en el control de edición de un cuadro combinado.|  
|[CComboBox::MeasureItem](#measureitem)|Llamado por el marco de trabajo para determinar las dimensiones del cuadro combinado cuando se crea un cuadro combinado dibujado por el propietario.|  
|[CComboBox::Paste](#paste)|Inserta los datos del Portapapeles en el control de edición en la posición actual del cursor. Los datos se insertan sólo si el Portapapeles contiene datos en **CF_TEXT** formato.|  
|[CComboBox::ResetContent](#resetcontent)|Quita todos los elementos de la lista cuadro y edición control de un cuadro combinado.|  
|[CComboBox::SelectString](#selectstring)|Busca una cadena en el cuadro de lista de un cuadro combinado y, si se encuentra la cadena, selecciona la cadena en el cuadro de lista y copia la cadena en el control de edición.|  
|[CComboBox::SetCueBanner](#setcuebanner)|Establece el texto de indicación que se muestra para un control de cuadro combinado.|  
|[CComboBox::SetCurSel](#setcursel)|Selecciona una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Establece el ancho mínimo permitido para la parte de cuadro de lista desplegable de un cuadro combinado.|  
|[CComboBox::SetEditSel](#seteditsel)|Selecciona caracteres en el control de edición de un cuadro combinado.|  
|[CComboBox::SetExtendedUI](#setextendedui)|Selecciona la interfaz de usuario predeterminada o la interfaz de usuario extendida para un cuadro combinado que tiene el **CBS_DROPDOWN** o **CBS_DROPDOWNLIST** estilo.|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Establece el ancho en píxeles que la parte de cuadro de lista del cuadro combinado se puede desplazar horizontalmente.|  
|[CComboBox::SetItemData](#setitemdata)|Establece el valor de 32 bits asociado con el elemento especificado en un cuadro combinado.|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Establece el puntero de 32 bits asociado con el elemento especificado en un cuadro combinado.|  
|[CComboBox::SetItemHeight](#setitemheight)|Establece el alto de los elementos de lista en un cuadro combinado o el alto de la parte de un cuadro combinado de control de edición (o texto estático).|  
|[CComboBox::SetLocale](#setlocale)|Establece el identificador de configuración regional para un cuadro combinado.|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Establece el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|  
|[CComboBox::SetTopIndex](#settopindex)|Indica la parte de cuadro de lista del cuadro combinado para mostrar el elemento con el índice especificado en la parte superior.|  
|[CComboBox::ShowDropDown](#showdropdown)|Muestra u oculta el cuadro de lista de un cuadro combinado que tiene el **CBS_DROPDOWN** o **CBS_DROPDOWNLIST** estilo.|  
  
## <a name="remarks"></a>Comentarios  
 Un cuadro combinado consta de un cuadro de lista combinado con un control estático o un control de edición. La parte de cuadro de lista del control puede mostrarse en todo momento o sólo puede desplegable cuando el usuario selecciona la flecha de lista desplegable situada junto al control.  
  
 El elemento seleccionado actualmente (si existe) en el cuadro de lista se muestra en estático o control de edición. Además, si el cuadro combinado tiene el estilo de lista desplegable, el usuario puede escribir el carácter inicial de uno de los elementos en la lista y el cuadro de lista, si está visible, resalte el elemento siguiente con ese carácter inicial.  
  
 La tabla siguiente compara el cuadro combinado tres [estilos](../../mfc/reference/combo-box-styles.md).  
  
|Estilo|Cuando está visible el cuadro de lista|Control estático o de edición|  
|-----------|-------------------------------|-----------------------------|  
|Sencillo|Always|Editar|  
|Drop-down|Cuando quita hacia abajo|Editar|  
|Lista desplegable|Cuando quita hacia abajo|Estático|  
  
 Puede crear un `CComboBox` objeto desde una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, llame primero al constructor de `CComboBox` para construir la `CComboBox` objeto; a continuación, llame a la [crear](#create) función de miembro para crear el control y adjuntarlo a la `CComboBox` objeto.  
  
 Si desea controlar mensajes de notificación de Windows enviados por un cuadro combinado a su elemento primario (normalmente una clase derivada de `CDialog`), agregar una función de miembro de entrada y el controlador de mensajes del mapa de mensajes a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes toma la forma siguiente:  
  
 **ON_**Notification **(**`id`**,**`memberFxn`**)**  
  
 donde `id` especifica el identificador de ventana secundaria del control de cuadro combinado que se envía la notificación y `memberFxn` es el nombre de la función de miembro primario que ha escrito para controlar la notificación.  
  
 Prototipo de función del elemento primario es el siguiente:  
  
 **afx_msg** `void` `memberFxn` **( );**  
  
 No se puede predecir el orden en el que se enviará ciertas notificaciones. En concreto, un **CBN_SELCHANGE** notificación puede producirse antes o después de un **CBN_CLOSEUP** notificación.  
  
 Posibles entradas de mapa de mensajes son los siguientes:  
  
- **ON_CBN_CLOSEUP** (Windows 3.1 y versiones posteriores). Se cerró el cuadro de lista de un cuadro combinado. Este mensaje de notificación no se envía para un cuadro combinado que tuviera la [CBS_SIMPLE](../../mfc/reference/combo-box-styles.md) estilo.  
  
- **ON_CBN_DBLCLK** el usuario hace doble clic en una cadena en el cuadro de lista de un cuadro combinado. Este mensaje de notificación sólo se envía para un cuadro combinado con el **CBS_SIMPLE** estilo. Para un cuadro combinado con el [CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md) o [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) estilo, no se puede producir un doble clic porque un solo clic oculta el cuadro de lista.  
  
- **ON_CBN_DROPDOWN** el cuadro de lista de un cuadro combinado está a punto de lista desplegable (hacerse visibles). Puede producirse este mensaje de notificación sólo por un cuadro combinado con el **CBS_DROPDOWN** o **CBS_DROPDOWNLIST** estilo.  
  
- **ON_CBN_EDITCHANGE** el usuario ha realizado una acción que puede haber modificado el texto en la parte del control de edición de un cuadro combinado. A diferencia de la **CBN_EDITUPDATE** mensaje, este mensaje se envía después de la pantalla de actualizaciones de Windows. No se envía si el cuadro combinado tiene la **CBS_DROPDOWNLIST** estilo.  
  
- **ON_CBN_EDITUPDATE** la parte del control de edición de un cuadro combinado está a punto de mostrar el texto modificado. Este mensaje de notificación se envía después de que el control ha dado formato al texto, pero antes de que se muestre el texto. No se envía si el cuadro combinado tiene la **CBS_DROPDOWNLIST** estilo.  
  
- **ON_CBN_ERRSPACE** el cuadro combinado no puede asignar memoria suficiente para satisfacer una solicitud específica.  
  
- **ON_CBN_SELENDCANCEL** (Windows 3.1 y versiones posteriores). Indica que se debe cancelar la selección del usuario. El usuario hace clic en un elemento y, a continuación, hace clic en otra ventana o control para ocultar el cuadro de lista de un cuadro combinado. Este mensaje de notificación se envía antes de la **CBN_CLOSEUP** mensaje de notificación para indicar que se debe omitir la selección del usuario. El **CBN_SELENDCANCEL** o **CBN_SELENDOK** envía el mensaje de notificación incluso si la **CBN_CLOSEUP** no se envía el mensaje de notificación (como en el caso de un cuadro combinado con el **CBS_SIMPLE** estilo).  
  
- **ON_CBN_SELENDOK** el usuario selecciona un elemento y, a continuación, presione la tecla ENTRAR o haga clic en la tecla de flecha abajo para ocultar el cuadro de lista de un cuadro combinado. Este mensaje de notificación se envía antes de la **CBN_CLOSEUP** mensaje para indicar que la selección del usuario debe considerarse válida. El **CBN_SELENDCANCEL** o **CBN_SELENDOK** envía el mensaje de notificación incluso si la **CBN_CLOSEUP** no se envía el mensaje de notificación (como en el caso de un cuadro combinado con el **CBS_SIMPLE** estilo).  
  
- **ON_CBN_KILLFOCUS** el cuadro combinado está perdiendo el foco de entrada.  
  
- **ON_CBN_SELCHANGE** la selección en el cuadro de lista de un cuadro combinado está a punto de cambiarse cuando el usuario haga clic en el cuadro de lista o cambiar la selección mediante las teclas de dirección. Al procesar este mensaje, sólo se puede recuperar el texto del control de edición del cuadro combinado a través de `GetLBText` u otra función similar. `GetWindowText`no se puede usar.  
  
- **ON_CBN_SETFOCUS** el cuadro combinado recibe el foco de entrada.  
  
 Si crea un `CComboBox` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CComboBox` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si incrusta un `CComboBox` objeto dentro de otra ventana de objetos, no necesitará destruirlo. Si crea la `CComboBox` objeto en la pila, se destruye automáticamente. Si crea el `CComboBox` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** en el objeto destruirla cuando se destruye el cuadro combinado de Windows.  
  
 **Nota** si desea controlar `WM_KEYDOWN` y `WM_CHAR` mensajes, tendrá que subclase del cuadro combinado editar y controles de cuadro de lista, derivar las clases de `CEdit` y `CListBox`, y agregar controladores para estos mensajes a las clases derivadas. Para obtener más información, consulte [http://support.microsoft.com/default.aspxscid=kb;en-us; Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667) y [CWnd:: SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="addstring"></a>CComboBox:: AddString  
 Agrega una cadena al cuadro de lista de un cuadro combinado.  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Apunta a la cadena terminada en null que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es mayor o igual que 0, es el índice de base cero de la cadena en el cuadro de lista. El valor devuelto es **CB_ERR** si se produce un error; el valor devuelto es **CB_ERRSPACE** si no hay suficiente espacio disponible para almacenar la nueva cadena.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro de lista no se creó con el [CBS_SORT](../../mfc/reference/combo-box-styles.md) estilo, la cadena se agrega al final de la lista. De lo contrario, la cadena se inserta en la lista y la lista está ordenada.  
  
> [!NOTE]
>  Esta función no es compatible con el control **ComboBoxEx** de Windows. Para obtener más información sobre este control, consulte [controles de ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para insertar una cadena en una ubicación específica dentro de la lista, utilice la [InsertString](#insertstring) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&3;](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>CComboBox::CComboBox  
 Construye un objeto `CComboBox`.  
  
```  
CComboBox();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CComboBox](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>CComboBox::Clear  
 Elimina (borra) la selección actual, si existe alguno, en el control de edición del cuadro combinado.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 Para eliminar la selección actual y coloca el contenido eliminado en el Portapapeles, utilice la [cortar](#cut) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&4;](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CComboBox::CompareItem  
 Llamado por el marco de trabajo para determinar la posición relativa de un elemento nuevo en la parte de cuadro de lista de un cuadro combinado de ordenado dibujados por el propietario.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpCompareItemStruct`  
 Un puntero largo a una [COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Indica la posición relativa de los dos elementos que se describe en el `COMPAREITEMSTRUCT` estructura. Puede ser cualquiera de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|– 1|Elemento 1 se ordena antes que el elemento 2.|  
|0|Elemento 1 y 2 del artículo ordenan de la misma.|  
|1|Elemento 1 se ordena después del elemento 2.|  
  
 Consulte [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) para obtener una descripción de `COMPAREITEMSTRUCT`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Si crea un cuadro combinado de dibujados con el **LBS_SORT** estilo, debe reemplazar esta función miembro para ayudarle a ordenar elementos nuevos agregados a la lista el marco de trabajo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#5;](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>CComboBox::Copy  
 Copia la selección actual, si existe alguno, en el control de edición del cuadro combinado en el Portapapeles en **CF_TEXT** formato.  
  
```  
void Copy();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&6;](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="create"></a>CComboBox::Create  
 Crea el cuadro combinado y lo adjunta a la `CComboBox` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del cuadro combinado. Aplicar cualquier combinación de [estilos de cuadro combinado](../../mfc/reference/combo-box-styles.md) al cuadro.  
  
 `rect`  
 Señala la posición y el tamaño del cuadro combinado. Puede ser un [estructura RECT](../../mfc/reference/rect-structure1.md) o un `CRect` objeto.  
  
 `pParentWnd`  
 Especifica la ventana primaria del cuadro combinado (normalmente un `CDialog`). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del cuadro combinado  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CComboBox` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el cuadro combinado de Windows y lo adjunta a la `CComboBox` objeto.  
  
 Cuando **crear** se ejecuta, Windows envía la [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) mensajes al cuadro combinado.  
  
 Estos mensajes se controlan de manera predeterminada el [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funciones miembro en la `CWnd` clase base. Para extender el control de mensajes de forma predeterminada, derive una clase de `CComboBox`, agregue un mapa de mensajes a la nueva clase y reemplazar las funciones miembro de controlador de mensaje anterior. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/window-styles.md) a un control de cuadro combinado. :  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
- **WS_VSCROLL** para agregar el desplazamiento vertical en el cuadro de lista en el cuadro combinado  
  
- **WS_HSCROLL** para agregar el desplazamiento horizontal del cuadro de lista en el cuadro combinado  
  
- **WS_GROUP** para agrupar controles  
  
- **WS_TABSTOP** para incluir el cuadro combinado en el orden de tabulación  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#2;](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>CComboBox::Cut  
 Elimina (cortes) la selección actual, si existe alguno, en el cuadro combinado editar control y copia el texto eliminado en el Portapapeles en **CF_TEXT** formato.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Comentarios  
 Para eliminar la selección actual sin colocar el texto eliminado en el Portapapeles, llame a la [borrar](#clear) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#7;](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>CComboBox::DeleteItem  
 Llamado por el marco de trabajo cuando el usuario elimina un elemento de un dibujo propietario `CComboBox` de objeto o destruye el cuadro combinado.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDeleteItemStruct`  
 Un puntero largo a Windows [DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md) estructura que contiene información sobre el elemento eliminado. Consulte [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) para obtener una descripción de esta estructura.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Reemplazar esta función para volver a dibujar el cuadro combinado, según sea necesario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&8;](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>CComboBox::DeleteString  
 Elimina el elemento en la posición `nIndex` en el cuadro combinado.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de la cadena que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es mayor o igual que 0, es un recuento de las cadenas restantes en la lista. El valor devuelto es **CB_ERR** si `nIndex` especifica un índice mayor que el número de elementos de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Todos los elementos que siguen a `nIndex` ahora Bajar una posición. Por ejemplo, si un cuadro combinado contiene dos elementos, eliminar el primer elemento hará que el resto de producto estar en la primera posición. `nIndex`=&0; para el elemento en la primera posición.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#9;](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>CComboBox::Dir  
 Agrega una lista de nombres de archivo o las unidades en el cuadro de lista de un cuadro combinado.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parámetros  
 `attr`  
 Puede ser cualquier combinación de los `enum` valores que se describen en [CFile:: GetStatus](../../mfc/reference/cfile-class.md#getstatus) o cualquier combinación de los siguientes valores:  
  
- **DDL_READWRITE** archivo se puede leer o escribir.  
  
- **DDL_READONLY** se puede leer desde pero no escriben en el archivo.  
  
- **DDL_HIDDEN** archivo está oculto y no aparece en una lista de directorios.  
  
- **DDL_SYSTEM** es un archivo de sistema.  
  
- **DDL_DIRECTORY** el nombre especificado por `lpszWildCard` especifica un directorio.  
  
- **DDL_ARCHIVE** archivo se ha archivado.  
  
- **DDL_DRIVES** incluyen todas las unidades que coinciden con el nombre especificado por `lpszWildCard`.  
  
- **DDL_EXCLUSIVE** indicador Exclusive. Si se establece el indicador exclusive, se muestran sólo los archivos del tipo especificado. De lo contrario, los archivos del tipo especificado se enumeran además de los archivos "normales".  
  
 `lpszWildCard`  
 Apunta a una cadena de la especificación de archivo. La cadena puede contener caracteres comodín (por ejemplo, *.\*).  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es mayor o igual que 0, es el índice de base cero del nombre del último archivo agregado a la lista. El valor devuelto es **CB_ERR** si se produce un error; el valor devuelto es **CB_ERRSPACE** si no hay suficiente espacio disponible para almacenar las nuevas cadenas.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no es compatible con el control **ComboBoxEx** de Windows. Para obtener más información sobre este control, consulte [controles de ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#10;](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>CComboBox::DrawItem  
 Llamado por el marco cuando un aspecto visual de un cuadro combinado cambia de dibujados por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero a un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura que contiene información sobre el tipo de dibujo necesario.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza. Consulte [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de esta estructura.  
  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar un dibujados por el propietario del dibujo `CComboBox` objeto. Antes de que finalice esta función miembro, la aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para el contexto de presentación proporcionado en `lpDrawItemStruct`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#11;](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>CComboBox::FindString  
 Detecte, pero no se selecciona, la primera cadena que contiene el prefijo especificado en el cuadro de lista de un cuadro combinado.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartAfter`  
 Contiene el índice de base cero del elemento delante del primer elemento que se buscará. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa en la parte superior del cuadro de lista hasta el elemento especificado por `nStartAfter`. Si-1, se busca el cuadro de lista todo desde el principio.  
  
 `lpszString`  
 Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es el caso independiente, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es mayor o igual que 0, es el índice de base cero del elemento coincidente. Es **CB_ERR** si la búsqueda se realizó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no es compatible con el control **ComboBoxEx** de Windows. Para obtener más información sobre este control, consulte [controles de ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#12;](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>CComboBox::FindStringExact  
 Llame a la `FindStringExact` función de miembro para buscar la primera cadena de cuadro de lista (en un cuadro combinado) que coincide con la cadena especificada en `lpszFind`.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndexStart`  
 Especifica el índice de base cero del elemento delante del primer elemento que se buscará. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa en la parte superior del cuadro de lista hasta el elemento especificado por `nIndexStart`. Si `nIndexStart` es –&1;, se busca en el cuadro de lista todo desde el principio.  
  
 `lpszFind`  
 Apunta a la cadena terminada en null para buscar. Esta cadena puede contener un nombre de archivo completo, incluida la extensión. La búsqueda no distingue mayúsculas de minúsculas, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento coincidente, o **CB_ERR** si la búsqueda se realizó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro combinado se creó con un estilo de dibujo de propietario pero sin la [CBS_HASSTRINGS](../../mfc/reference/combo-box-styles.md) estilo, `FindStringExact` intenta hacer coincidir el valor de palabra doble con el valor de `lpszFind`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#13;](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo  
 Recupera información de la `CComboBox` objeto.  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pcbi*  
 Un puntero a la [COMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775798) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [CB_GETCOMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775839) de mensajes, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getcount"></a>CComboBox::GetCount  
 Llame a esta función miembro para recuperar el número de elementos de la parte de cuadro de lista de un cuadro combinado.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos. El recuento devuelto es una unidad mayor que el valor de índice del último elemento (el índice está basado en cero). Es **CB_ERR** si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#14;](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="getcuebanner"></a>CComboBox::GetCueBanner  
 Obtiene el texto de indicación que se muestra para un control de cuadro combinado.  
  
```  
CString GetCueBanner() const;  
  
BOOL GetCueBanner(
    LPTSTR lpszText,   
    int cchText) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `lpszText`|Puntero a un búfer que recibe el texto de titular de indicación.|  
|[in] `cchText`|Tamaño del búfer que el `lpszText` parámetro señala a.|  
  
### <a name="return-value"></a>Valor devuelto  
 En la primera sobrecarga, un [CString](../../atl-mfc-shared/using-cstring.md) objeto que contiene el texto de titular de indicación de si existe; de lo contrario, un `CString` objeto que tiene una longitud cero.  
  
 O bien  
  
 En la segunda sobrecarga, `true` si este método es correcta; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Texto de indicación es un mensaje que se muestra en el área de entrada del control de cuadro combinado. Se muestra el texto de la indicación hasta que el usuario proporciona una entrada.  
  
 Este método envía el [CB_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775843) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getcursel"></a>CComboBox::GetCurSel  
 Llame a esta función miembro para determinar qué elemento del cuadro combinado está seleccionado.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento actualmente seleccionado en el cuadro de lista de un cuadro combinado, o **CB_ERR** si se selecciona ningún elemento.  
  
### <a name="remarks"></a>Comentarios  
 `GetCurSel`Devuelve un índice en la lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#15;](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect  
 Llame a la `GetDroppedControlRect` la función miembro para recuperar las coordenadas de pantalla del cuadro visible (quita) de lista desplegable de un cuadro combinado desplegable.  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *lprect*  
 Apunta a la [estructura RECT](../../mfc/reference/rect-structure1.md) que va a recibir las coordenadas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&16;](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>CComboBox::GetDroppedState  
 Llame a la `GetDroppedState` la función miembro para determinar si está visible el cuadro de lista de un cuadro combinado desplegable (desplegada).  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cuadro de lista está visible; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#17;](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth  
 Llame a esta función para recuperar el ancho mínimo permitido, en píxeles, del cuadro de lista de un cuadro combinado.  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el ancho mínimo permitido, en píxeles. de lo contrario, **CB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función sólo se aplica a los cuadros combinados con el [CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md) o [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) estilo.  
  
 De forma predeterminada, el ancho mínimo permitido del cuadro de lista desplegable es 0. Se puede establecer el ancho mínimo permitido mediante una llamada a [SetDroppedWidth](#setdroppedwidth). Cuando se muestra la parte de cuadro de lista del cuadro combinado, su ancho es mayor el ancho mínimo permitido o el ancho del cuadro combinado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [SetDroppedWidth](#setdroppedwidth).  
  
##  <a name="geteditsel"></a>CComboBox::GetEditSel  
 Obtiene las posiciones de carácter inicial y final de la selección actual del control de edición de un cuadro combinado.  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de 32 bits que contiene la posición inicial de la palabra de orden inferior y la posición del primer carácter después del final de la selección de la palabra de orden superior. Si esta función se utiliza en un cuadro combinado sin un control de edición **CB_ERR** se devuelve.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#18;](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>CComboBox::GetExtendedUI  
 Llame a la `GetExtendedUI` la función miembro para determinar si un cuadro combinado tiene la interfaz de usuario predeterminada o la interfaz de usuario extendida.  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el cuadro combinado tiene la interfaz de usuario extendida; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz de usuario extendida puede identificarse de las maneras siguientes:  
  
-   Al hacer clic en el control estático muestra el cuadro de lista solo para los cuadros combinados con el [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) estilo.  
  
-   Al presionar la tecla flecha abajo, muestra el cuadro de lista (F4 está deshabilitado).  
  
 Desplazamiento en el control estático se deshabilita cuando la lista de elementos no es visible (flecha claves están deshabilitadas).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&19;](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent  
 En el cuadro combinado, recupera el ancho en píxeles por el que se puede desplazar horizontalmente la parte de cuadro de lista del cuadro combinado.  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho de desplazamiento de la parte de cuadro de lista del cuadro combinado, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Esto sólo es aplicable si la parte de cuadro de lista del cuadro combinado tiene una barra de desplazamiento horizontal.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#20;](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>CComboBox::GetItemData  
 Recupera el valor de 32 bits proporcionada por la aplicación asociado con el elemento de cuadro combinado especificado.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el índice de base cero de un elemento de cuadro de lista del cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de 32 bits asociado al elemento o **CB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Se puede establecer el valor de 32 bits con la `dwItemData` parámetro de un [SetItemData](#setitemdata) llamada a función miembro. Utilice la `GetItemDataPtr` función de miembro si el valor de 32 bits que se va a recuperar un puntero ( **void\***).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFC_CComboBox](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>CComboBox::GetItemDataPtr  
 Recupera el valor de 32 bits proporcionada por la aplicación asociado con el elemento de cuadro combinado especificado como un puntero ( **void\***).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el índice de base cero de un elemento de cuadro de lista del cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera un puntero, o –&1; si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#22;](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>CComboBox::GetItemHeight  
 Llame a la `GetItemHeight` la función miembro para recuperar el alto de los elementos de lista en un cuadro combinado.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el componente del cuadro combinado es cuyo alto se va a recuperar. Si el `nIndex` parámetro es -1, se recupera el alto de la parte del control de edición (o texto estático) del cuadro combinado. Si el cuadro combinado tiene la [CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md) estilo, `nIndex` especifica el índice de base cero del elemento lista cuyo alto se va a recuperar. De lo contrario, `nIndex` debe establecerse en 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Alto, en píxeles, del elemento especificado en un cuadro combinado. El valor devuelto es **CB_ERR** si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFC_CComboBox #](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>CComboBox::GetLBText  
 Obtiene una cadena en el cuadro de lista de un cuadro combinado.  
  
```  
int GetLBText(
    int nIndex,  
    LPTSTR lpszText) const;  
  
void GetLBText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el índice de base cero de la cadena del cuadro de lista para copiarse.  
  
 `lpszText`  
 Señala a un búfer que va a recibir la cadena. El búfer debe tener espacio suficiente para la cadena y un carácter nulo de terminación.  
  
 `rString`  
 Una referencia a un `CString`.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud (en bytes) de la cadena, excepto el carácter nulo de terminación. Si `nIndex` no especifica un índice válido, el valor devuelto es **CB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 La segunda forma de este miembro de función llena un `CString` objeto con el texto del elemento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#24;](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>CComboBox::GetLBTextLen  
 Obtiene la longitud de una cadena en el cuadro de lista de un cuadro combinado.  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el índice de base cero de la cadena del cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la cadena en bytes, sin incluir el carácter nulo de terminación. Si `nIndex` no especifica un índice válido, el valor devuelto es **CB_ERR**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CComboBox::GetLBText](#getlbtext).  
  
##  <a name="getlocale"></a>CComboBox::GetLocale  
 Recupera la configuración regional utilizada por el cuadro combinado.  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de identificador (LCID) de configuración regional para las cadenas en el cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, la configuración regional se usa para determinar el criterio de ordenación de las cadenas en un cuadro combinado ordenado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CComboBox::SetLocale](#setlocale).  
  
##  <a name="getminvisible"></a>CComboBox::GetMinVisible  
 Obtiene el número mínimo de elementos visibles en la lista desplegable del control de cuadro combinado actual.  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número mínimo de elementos visibles en la lista actual de la lista desplegable.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [CB_GETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettopindex"></a>CComboBox::GetTopIndex  
 Recupera el índice de base cero del primer elemento visible en la parte de cuadro de lista del cuadro combinado.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del primer elemento visible en la parte de cuadro de lista del cuadro combinado, si es correcto, **CB_ERR** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Inicialmente, es el elemento 0 en la parte superior del cuadro de lista, pero si se desplaza el cuadro de lista, puede ser otro elemento en la parte superior.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#25;](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>CComboBox::InitStorage  
 Asigna memoria para almacenar elementos de cuadro de lista en la parte de cuadro de lista del cuadro combinado.  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItems`  
 Especifica el número de elementos que desea agregar.  
  
 `nBytes`  
 Especifica la cantidad de memoria, en bytes, que se asignan para las cadenas de elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, el número máximo de elementos que puede almacenar la parte de cuadro de lista del cuadro combinado antes, en caso contrario, se necesita una reasignación de memoria **CB_ERRSPACE**, lo que significa que no hay suficiente memoria está disponible.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función antes de agregar un gran número de elementos a la parte de cuadro de lista de la `CComboBox`.  
  
 Sólo Windows 95 ó 98: el `wParam` parámetro está limitado a los valores de 16 bits. Esto significa que los cuadros de lista no pueden contener más de 32.767 elementos. Aunque el número de elementos está restringido, el tamaño total de los elementos de un cuadro de lista está limitado sólo por la memoria disponible.  
  
 Esta función le ayuda a acelerar la inicialización de los cuadros de lista que tiene un gran número de elementos (más de 100). Preasigna la cantidad especificada de memoria para que las siguientes [AddString](#addstring), [InsertString](#insertstring), y [Dir](#dir) funciones toman el menor tiempo posible. Puede utilizar las estimaciones para los parámetros. Si sobrestimar, se asigna memoria adicional; Si subestimar, la asignación normal se usa para los elementos que superan la cantidad preasignada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFC_CComboBox #](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>CComboBox::InsertString  
 Inserta una cadena en el cuadro de lista de un cuadro combinado.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el índice de base cero de la posición en el cuadro de lista que recibirá la cadena. Si este parámetro es –1, la cadena se agrega al final de la lista.  
  
 `lpszString`  
 Apunta a la cadena terminada en null que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la posición donde se insertó la cadena. El valor devuelto es **CB_ERR** si se produce un error. El valor devuelto es **CB_ERRSPACE** si no hay suficiente espacio disponible para almacenar la nueva cadena.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de la [AddString](#addstring) función miembro, el `InsertString` función miembro no provoca una lista con los [CBS_SORT](../../mfc/reference/combo-box-styles.md) estilo que se va a ordenar.  
  
> [!NOTE]
>  Esta función no es compatible con el control **ComboBoxEx** de Windows. Para obtener más información sobre este control, consulte [controles de ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&27;](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>CComboBox::LimitText  
 Limita la longitud en bytes del texto que el usuario puede escribir en el control de edición de un cuadro combinado.  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMaxChars`  
 Especifica la longitud (en bytes) del texto que el usuario puede escribir. Si este parámetro es 0, se establece la longitud del texto a 65.535 bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente. Si llama a un cuadro combinado con el estilo [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) o un cuadro combinado sin un control de edición, el valor devuelto es **CB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro combinado no tiene el estilo [CBS_AUTOHSCROLL](../../mfc/reference/combo-box-styles.md), establecer el límite del texto sea mayor que el tamaño del control de edición no tiene ningún efecto.  
  
 `LimitText`limita sólo el texto que el usuario puede escribir. No tiene ningún efecto en cualquier texto ya en el control de edición cuando se envía el mensaje, ni afecta a la longitud del texto que se copia en el control de edición cuando se selecciona una cadena en el cuadro de lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#28;](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>CComboBox::MeasureItem  
 Lo llama el marco de trabajo cuando se crea un cuadro combinado con un estilo de dibujo del propietario.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMeasureItemStruct`  
 Un puntero largo a una [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de las dimensiones de la lista de cuadro en el cuadro combinado. Si se crea el cuadro combinado con el [CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md) estilo, el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. De lo contrario, este miembro se llama solo una vez.  
  
 Mediante la **CBS_OWNERDRAWFIXED** estilo en un cuadro combinado de dibujados creado con el [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) función miembro de `CWnd` incluye consideraciones de programación adicional. Vea la explicación en [14 de nota técnica](../../mfc/tn014-custom-controls.md).  
  
 Consulte [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de la `MEASUREITEMSTRUCT` estructura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#29;](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>CComboBox::Paste  
 Inserta los datos del Portapapeles en el control de edición del cuadro combinado en la posición actual del cursor.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Comentarios  
 Los datos se insertan sólo si el Portapapeles contiene datos en **CF_TEXT** formato.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&30;](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>CComboBox::ResetContent  
 Quita todos los elementos de la lista cuadro y edición control de un cuadro combinado.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#31;](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>CComboBox::SelectString  
 Busca una cadena en el cuadro de lista de un cuadro combinado y, si se encuentra la cadena, selecciona la cadena en el cuadro de lista y lo copia en el control de edición.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartAfter`  
 Contiene el índice de base cero del elemento delante del primer elemento que se buscará. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa en la parte superior del cuadro de lista hasta el elemento especificado por `nStartAfter`. Si-1, se busca el cuadro de lista todo desde el principio.  
  
 `lpszString`  
 Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es el caso independiente, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento seleccionado si se encuentra la cadena. Si la búsqueda se realizó correctamente, el valor devuelto es **CB_ERR** y no se cambia la selección actual.  
  
### <a name="remarks"></a>Comentarios  
 Sólo si sus caracteres iniciales (desde el punto inicial) coinciden con los caracteres de la cadena de prefijo, se selecciona una cadena.  
  
 Tenga en cuenta que el `SelectString` y `FindString` funciones miembro buscar una cadena, pero la `SelectString` función miembro también selecciona la cadena.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#32;](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>CComboBox::SetCueBanner  
 Establece el texto de indicación que se muestra para un control de cuadro combinado.  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *lpszText*|Puntero a un búfer terminado en null que contiene el texto de indicación.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el método es correcto; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Texto de indicación es un mensaje que se muestra en el área de entrada del control de cuadro combinado. Se muestra el texto de la indicación hasta que el usuario proporciona una entrada.  
  
 Este método envía el [CB_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775897) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_combobox`, que se utiliza para obtener acceso al control de cuadro combinado. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[1 NVC_MFC_CComboBox_s1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el titular de indicación para el control de cuadro combinado.  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>CComboBox::SetCurSel  
 Selecciona una cadena en el cuadro de lista de un cuadro combinado.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSelect`  
 Especifica el índice de base cero de la cadena que seleccione. Si-1, se quita cualquier selección actual en el cuadro de lista y se borra el control de edición.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento seleccionado si el mensaje es correcto. El valor devuelto es **CB_ERR** si `nSelect` es mayor que el número de elementos de la lista o si `nSelect` se establece en -1, que borra la selección.  
  
### <a name="remarks"></a>Comentarios  
 Si es necesario, el cuadro de lista desplaza la cadena en la vista (si está visible el cuadro de lista). El texto del control de edición del cuadro combinado se cambia para reflejar la nueva selección. Se quita la selección anterior en el cuadro de lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&33;](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth  
 Llame a esta función para establecer el ancho mínimo permitido, en píxeles, del cuadro de lista de un cuadro combinado.  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 El ancho mínimo permitido de la parte de cuadro de lista del cuadro combinado, en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, el nuevo ancho de la lista de cuadro, de lo contrario **CB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función sólo se aplica a los cuadros combinados con el [CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md) o [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) estilo.  
  
 De forma predeterminada, el ancho mínimo permitido del cuadro de lista desplegable es 0. Cuando se muestra la parte de cuadro de lista del cuadro combinado, su ancho es mayor el ancho mínimo permitido o el ancho del cuadro combinado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#34;](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>CComboBox::SetEditSel  
 Selecciona caracteres en el control de edición de un cuadro combinado.  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartChar`  
 Especifica la posición inicial. Si la posición inicial se establece en -1, se quita cualquier selección existente.  
  
 `nEndChar`  
 Especifica la posición final. Si la posición final se establece en -1, a continuación, todo el texto desde la posición inicial hasta el último carácter en el control de edición está seleccionada.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función miembro se realiza correctamente; en caso contrario, 0. Es **CB_ERR** si `CComboBox` tiene la [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) estilo o no tiene un cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 Las posiciones son de base cero. Para seleccionar el primer carácter del control de edición, especifique una posición inicial de 0. La posición final es el carácter inmediatamente después del último carácter que seleccione. Por ejemplo, para seleccionar los primeros cuatro caracteres de control de edición, usaría una posición inicial de 0 y una posición final de 4.  
  
> [!NOTE]
>  Esta función no es compatible con el control **ComboBoxEx** de Windows. Para obtener más información sobre este control, consulte [controles de ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CComboBox::GetEditSel](#geteditsel).  
  
##  <a name="setextendedui"></a>CComboBox::SetExtendedUI  
 Llame a la `SetExtendedUI` función miembro para seleccionar la interfaz de usuario predeterminada o la interfaz de usuario extendida para un cuadro combinado que tiene el [CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md) o [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) estilo.  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEl*  
 Especifica si el cuadro combinado debe utilizar la interfaz de usuario extendida o la interfaz de usuario predeterminada. Un valor de **TRUE** selecciona extendido interfaz de usuario; un valor de **FALSE** selecciona la interfaz de usuario estándar.  
  
### <a name="return-value"></a>Valor devuelto  
 **CB_OKAY** si la operación se realiza correctamente, o **CB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz de usuario extendida puede identificarse de las maneras siguientes:  
  
-   Al hacer clic en el control estático muestra el cuadro de lista solo para los cuadros combinados con el **CBS_DROPDOWNLIST** estilo.  
  
-   Al presionar la tecla flecha abajo, muestra el cuadro de lista (F4 está deshabilitado).  
  
 Desplazamiento en el control estático está deshabilitado cuando no está visible la lista de elementos (se deshabilitan las teclas de dirección).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CComboBox::GetExtendedUI](#getextendedui).  
  
##  <a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent  
 Establece el ancho, en píxeles, por el que se puede desplazar horizontalmente la parte de cuadro de lista del cuadro combinado.  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>Parámetros  
 *nExtent*  
 Especifica el número de píxeles que se puede desplazar horizontalmente la parte de cuadro de lista del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Si el ancho del cuadro de lista es menor que este valor, la barra de desplazamiento horizontal desplazará horizontalmente elementos en el cuadro de lista. Si el ancho del cuadro de lista es igual o mayor que este valor, la barra de desplazamiento horizontal está oculta o, si el cuadro combinado tiene la [CBS_DISABLENOSCROLL](../../mfc/reference/combo-box-styles.md) estilo, deshabilitado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#35;](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>CComboBox::SetItemData  
 Establece el valor de 32 bits asociado con el elemento especificado en un cuadro combinado.  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene un índice de base cero para el elemento que se va a establecer.  
  
 `dwItemData`  
 Contiene el nuevo valor para asociar al elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **CB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `SetItemDataPtr` función de miembro si el elemento de 32 bits es un puntero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#36;](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>CComboBox::SetItemDataPtr  
 Establece el valor de 32 bits asociado con el elemento especificado en un cuadro combinado como el puntero especificado ( **void\***).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene un índice basado en cero del elemento.  
  
 `pData`  
 Contiene el puntero a asociar al elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **CB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Este puntero es válido durante la vida del cuadro combinado, incluso aunque la posición relativa del elemento del cuadro combinado se podría cambiar conforme se agregan o quitan elementos. Por lo tanto, puede cambiar el índice del elemento dentro del cuadro, pero el puntero permanece confiable.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#37;](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>CComboBox::SetItemHeight  
 Llame a la `SetItemHeight` la función miembro para establecer el alto de los elementos de lista en un cuadro combinado o el alto de la parte de un cuadro combinado de control de edición (o texto estático).  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica si se establece el alto de los elementos de lista o el alto de la parte del control de edición (o texto estático) del cuadro combinado.  
  
 Si el cuadro combinado tiene la [CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md) estilo, `nIndex` especifica el índice basado en cero del elemento de lista cuyo alto se puede establecer; de lo contrario, `nIndex` debe ser 0 y el alto de la lista de todos los elementos que se establecerá.  
  
 Si `nIndex` es -1, el alto del control de edición o la parte de texto estático de un cuadro combinado que se va a establecer.  
  
 `cyItemHeight`  
 Especifica el alto, en píxeles, del componente de cuadro combinado identificado por `nIndex`.  
  
### <a name="return-value"></a>Valor devuelto  
 **CB_ERR** si el índice o el alto no es válido; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Independientemente de la altura de los elementos de lista, se establece el alto de la parte del control de edición (o texto estático) del cuadro combinado. Una aplicación debe asegurarse de que el alto de la parte del control de edición (o texto estático) no es menor que el alto de un elemento concreto del cuadro de lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#38;](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>CComboBox::SetLocale  
 Establece el identificador de configuración regional de este cuadro combinado.  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNewLocale`  
 El nuevo valor de identificador (LCID) de configuración regional para establecer para el cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de identificador (LCID) de configuración regional anterior de este cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Si **SetLocale** no se llama, el valor predeterminado se obtiene la configuración regional del sistema. Se puede modificar esta configuración regional predeterminada del sistema mediante el uso del Panel de Control Configuración Regional (o internacional) de aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox&#39;](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems  
 Establece al número mínimo de elementos visibles en la lista desplegable el combinado actual de control de cuadro.  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iMinVisible`|Especifica el número mínimo de elementos visibles.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [CB_SETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_combobox`, que se utiliza para obtener acceso al control de cuadro combinado. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[1 NVC_MFC_CComboBox_s1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se inserta 20 elementos en la lista desplegable de un control de cuadro combinado. A continuación, especifica que se muestre un mínimo de 10 elementos cuando el usuario presiona la flecha de lista desplegable.  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>CComboBox::SetTopIndex  
 Garantiza que un determinado elemento está visible en la parte de cuadro de lista del cuadro combinado.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento de cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si es correcto, o **CB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El sistema desplaza el cuadro de lista hasta que el elemento o especificado por `nIndex` aparece en la parte superior de la lista se ha alcanzado cuadro o el intervalo máximo de desplazamiento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CComboBox Nº&40;](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>CComboBox::ShowDropDown  
 Muestra u oculta el cuadro de lista de un cuadro combinado que tiene el [CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md) o [CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) estilo.  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bShowIt*  
 Especifica si el cuadro de lista desplegable se deben mostrarse u ocultarse. Un valor de **TRUE** muestra el cuadro de lista. Un valor de **FALSE** oculta el cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, un cuadro combinado de este estilo mostrará el cuadro de lista.  
  
 Esta función miembro no tiene ningún efecto en un cuadro combinado que se crean con el [CBS_SIMPLE](../../mfc/reference/combo-box-styles.md) estilo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CComboBox::GetDroppedState](#getdroppedstate).  
  
## <a name="see-also"></a>Vea también  
 [CTRLBARS de ejemplo de MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CButton (clase)](../../mfc/reference/cbutton-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Clase CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Clase CStatic](../../mfc/reference/cstatic-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)

