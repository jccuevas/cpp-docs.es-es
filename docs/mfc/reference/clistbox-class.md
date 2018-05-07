---
title: CListBox (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
dev_langs:
- C++
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1101e4115efa3c5c822d0d64b767cdee379a0e0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="clistbox-class"></a>CListBox (clase)
Proporciona la funcionalidad de un cuadro de lista de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|Construye un objeto `CListBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|Agrega una cadena a un cuadro de lista.|  
|[CListBox::CharToItem](#chartoitem)|Invalidación para proporcionar personalizado `WM_CHAR` control dibujado por el propietario para cuadros de lista que no tienen cadenas.|  
|[CListBox::CompareItem](#compareitem)|Lo llama el marco de trabajo para determinar la posición de un nuevo elemento en un cuadro de lista ordenado dibujado por el propietario.|  
|[CListBox::Create](#create)|Crea el cuadro de lista de Windows y lo adjunta a la `CListBox` objeto.|  
|[CListBox::DeleteItem](#deleteitem)|Lo llama el marco cuando el usuario elimina un elemento en un cuadro de lista dibujado por el propietario.|  
|[CListBox::DeleteString](#deletestring)|Elimina una cadena de un cuadro de lista.|  
|[CListBox::Dir](#dir)|Agrega los nombres de archivo, las unidades o ambos desde el directorio actual a un cuadro de lista.|  
|[CListBox::DrawItem](#drawitem)|Lo llama el marco cuando un aspecto visual de un cuadro de lista dibujado por el propietario cambie.|  
|[CListBox::FindString](#findstring)|Busca una cadena en un cuadro de lista.|  
|[CListBox::FindStringExact](#findstringexact)|Busca la primera cadena de cuadro de lista que coincide con una cadena especificada.|  
|[CListBox::GetAnchorIndex](#getanchorindex)|Recupera el índice de base cero del elemento delimitador actual en un cuadro de lista.|  
|[CListBox::GetCaretIndex](#getcaretindex)|Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.|  
|[CListBox::GetCount](#getcount)|Devuelve el número de cadenas en un cuadro de lista.|  
|[CListBox::GetCurSel](#getcursel)|Devuelve el índice de base cero de la cadena actualmente seleccionado en un cuadro de lista.|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Devuelve el ancho en píxeles que un cuadro de lista se puede desplazar horizontalmente.|  
|[CListBox::GetItemData](#getitemdata)|Devuelve el valor de 32 bits asociado con el elemento de cuadro de lista.|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|Devuelve un puntero a un elemento de cuadro de lista.|  
|[CListBox::GetItemHeight](#getitemheight)|Determina el alto de los elementos de un cuadro de lista.|  
|[CListBox::GetItemRect](#getitemrect)|Devuelve el rectángulo delimitador del elemento de cuadro de lista tal y como se muestra actualmente.|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Recupera el número de elementos en cada columna.|  
|[CListBox::GetLocale](#getlocale)|Recupera el identificador de configuración regional de un cuadro de lista.|  
|[CListBox::GetSel](#getsel)|Devuelve el estado de selección de un elemento de cuadro de lista.|  
|[CListBox::GetSelCount](#getselcount)|Devuelve el número de cadenas actualmente seleccionado en un cuadro de lista de selección múltiple.|  
|[CListBox::GetSelItems](#getselitems)|Devuelve los índices de las cadenas actualmente seleccionados en un cuadro de lista.|  
|[CListBox::GetText](#gettext)|Copia un elemento de cuadro de lista en un búfer.|  
|[CListBox::GetTextLen](#gettextlen)|Devuelve la longitud en bytes de un elemento de cuadro de lista.|  
|[CListBox::GetTopIndex](#gettopindex)|Devuelve el índice de la primera cadena visible en un cuadro de lista.|  
|[CListBox::InitStorage](#initstorage)|Preasigna bloques de memoria para cadenas y elementos de cuadro de lista.|  
|[CListBox::InsertString](#insertstring)|Inserta una cadena en una ubicación específica en un cuadro de lista.|  
|[CListBox::ItemFromPoint](#itemfrompoint)|Devuelve el índice del elemento de cuadro de lista más cercano de un punto.|  
|[CListBox::MeasureItem](#measureitem)|Lo llama el marco cuando se crea un cuadro de lista dibujado por el propietario para determinar las dimensiones del cuadro de lista.|  
|[CListBox::ResetContent](#resetcontent)|Borra todas las entradas de un cuadro de lista.|  
|[CListBox::SelectString](#selectstring)|Busca y selecciona una cadena en un cuadro de lista de selección única.|  
|[CListBox::SelItemRange](#selitemrange)|Selecciona o anula la selección de un intervalo de cadenas en un cuadro de lista de selección múltiple.|  
|[CListBox::SetAnchorIndex](#setanchorindex)|Establece el delimitador de un cuadro de lista de selección múltiple para comenzar una selección extendida.|  
|[CListBox::SetCaretIndex](#setcaretindex)|Establece el rectángulo de foco en el elemento situado en el índice especificado en un cuadro de lista de selección múltiple.|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|Establece el ancho de columna de un cuadro de lista de varias columnas.|  
|[CListBox::SetCurSel](#setcursel)|Selecciona una cadena del cuadro de lista.|  
|[CListBox:: SetHorizontalExtent](#sethorizontalextent)|Establece el ancho en píxeles que un cuadro de lista se puede desplazar horizontalmente.|  
|[CListBox::SetItemData](#setitemdata)|Establece el valor de 32 bits asociado con el elemento de cuadro de lista.|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|Establece un puntero al elemento de cuadro de lista.|  
|[CListBox::SetItemHeight](#setitemheight)|Establece el alto de elementos en un cuadro de lista.|  
|[CListBox::SetLocale](#setlocale)|Establece el identificador de configuración regional para un cuadro de lista.|  
|[CListBox::SetSel](#setsel)|Selecciona o anula la selección de un elemento de cuadro de lista en un cuadro de lista de selección múltiple.|  
|[CListBox::SetTabStops](#settabstops)|Establece las posiciones de tabulación en un cuadro de lista.|  
|[CListBox::SetTopIndex](#settopindex)|Establece el índice de base cero de la primera cadena visible en un cuadro de lista.|  
|[CListBox::VKeyToItem](#vkeytoitem)|Invalidación para proporcionar personalizado `WM_KEYDOWN` control para cuadros de lista con el **LBS_WANTKEYBOARDINPUT** conjunto de estilo.|  
  
## <a name="remarks"></a>Comentarios  
 Un cuadro de lista muestra una lista de elementos, como los nombres de archivo, que puede ver y seleccionar el usuario.  
  
 En un cuadro de lista de selección única, el usuario puede seleccionar solo un elemento. En un cuadro de lista de selección múltiple, se puede seleccionar un intervalo de elementos. Cuando el usuario selecciona un elemento, se resalta y el cuadro de lista, envía un mensaje de notificación a la ventana primaria.  
  
 Puede crear un cuadro de lista de una plantilla de cuadro de diálogo o directamente en el código. Para crear directamente, construir la `CListBox` de objeto y después llamar a la [crear](#create) función de miembro para crear el control de cuadro de lista de Windows y adjuntarlo a la `CListBox` objeto. Para usar un cuadro de lista en una plantilla de cuadro de diálogo, declare una variable de cuadro de lista en la clase de cuadro de diálogo y, a continuación, usar `DDX_Control` en la clase de cuadro de diálogo `DoDataExchange` función para conectarse a la variable miembro para el control. (Esto se hace automáticamente automáticamente cuando se agrega una variable de control a la clase de cuadro de diálogo).  
  
 Construcción puede ser un proceso de un paso en una clase derivada de `CListBox`. Escribir un constructor para la clase derivada y llamar a **crear** desde dentro del constructor.  
  
 Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregar una función de miembro de entrada y el controlador de mensajes de mapa de mensajes para la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 `ON_Notification( id, memberFxn )`  
  
 donde `id` especifica el identificador de ventana de secundarios del control de cuadro de lista que se envía la notificación y `memberFxn` es el nombre de la función de miembro primario haya terminado de escribir para controlar la notificación.  
  
 Prototipo de función del elemento primario es el siguiente:  
  
 `afx_msg void memberFxn( );`  
  
 Aquí te mostramos una lista de posibles entradas de mapa de mensajes y una descripción de los casos en que se enviarían al elemento primario:  
  
- **ON_LBN_DBLCLK** el usuario hace doble clic en una cadena en un cuadro de lista. Un cuadro de lista que tiene el [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo enviará este mensaje de notificación.  
  
- **ON_LBN_ERRSPACE** el cuadro de lista no puede asignar memoria suficiente para satisfacer la solicitud.  
  
- **ON_LBN_KILLFOCUS** el cuadro de lista está perdiendo el foco de entrada.  
  
- **ON_LBN_SELCANCEL** se cancela la selección actual del cuadro de lista. Este mensaje sólo se envía cuando un cuadro de lista tiene la **LBS_NOTIFY** estilo.  
  
- **ON_LBN_SELCHANGE** ha cambiado la selección en el cuadro de lista. Esta notificación no se envía si la selección se modifica mediante la [CListBox::SetCurSel](#setcursel) función miembro. Esta notificación sólo se aplica a un cuadro de lista que tiene el **LBS_NOTIFY** estilo. El **LBN_SELCHANGE** mensaje de notificación se envía para un cuadro de lista de selección múltiple siempre que el usuario presiona una tecla de dirección, incluso si la selección no cambia.  
  
- **ON_LBN_SETFOCUS** recibe el foco de entrada en el cuadro de lista.  
  
- **ON_WM_CHARTOITEM** recibe un cuadro de lista dibujado por el propietario con ninguna cadena de un `WM_CHAR` mensaje.  
  
- **ON_WM_VKEYTOITEM** un cuadro de lista con el **LBS_WANTKEYBOARDINPUT** estilo recibe un `WM_KEYDOWN` mensaje.  
  
 Si crea un `CListBox` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CListBox` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un `CListBox` objeto dentro de una ventana, puede que necesite destruir la `CListBox` objeto. Si crea el `CListBox` del objeto en la pila, se destruye automáticamente. Si crea el `CListBox` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** del objeto que se va a destruir cuando el usuario cierra la ventana primaria.  
  
 Si asigna memoria en el `CListBox` objeto, invalide el `CListBox` destructor para eliminar de la asignación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="addstring"></a>  CListBox::AddString  
 Agrega una cadena a un cuadro de lista.  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszItem`  
 Apunta a la cadena terminada en null que se va a agregarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero en la cadena en el cuadro de lista. El valor devuelto es **LB_ERR** si se produce un error; el valor devuelto es **LB_ERRSPACE** si no hay suficiente espacio disponible para almacenar la nueva cadena.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro de lista no se creó con la [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, la cadena se agrega al final de la lista. En caso contrario, la cadena se inserta en la lista y la lista está ordenada. Si el cuadro de lista se creó con la **LBS_SORT** estilo pero no la [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, el marco de trabajo ordena la lista por una o más llamadas a la `CompareItem` función miembro.  
  
 Use [InsertString](#insertstring) para insertar una cadena en una ubicación específica en el cuadro de lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="chartoitem"></a>  CListBox::CharToItem  
 Lo llama el marco de trabajo cuando recibe de la ventana del elemento primario del cuadro de lista un `WM_CHARTOITEM` mensaje en el cuadro de lista.  
  
```  
virtual int CharToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nKey`  
 El código ANSI del carácter escrito por el usuario.  
  
 `nIndex`  
 La posición actual del símbolo de intercalación del cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve - 1 o - 2 para ninguna otra acción o un número no negativo para especificar un índice de un elemento de cuadro de lista en el que se va a realizar la acción predeterminada para la pulsación de tecla. La implementación predeterminada devuelve - 1.  
  
### <a name="remarks"></a>Comentarios  
 El `WM_CHARTOITEM` se envía el mensaje en el cuadro de lista cuando recibe un `WM_CHAR` mensaje, pero solo si el cuadro de lista cumple todos estos criterios:  
  
-   Es un cuadro de lista dibujado por el propietario.  
  
-   No tiene la [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) conjunto de estilo.  
  
-   Tiene al menos un elemento.  
  
 Nunca debe llamar esta función usted mismo. Reemplace esta función para proporcionar su propio control personalizado de mensajes del teclado.  
  
 En la invalidación, debe devolver un valor para indicar el marco de la acción que ha realizado. Un valor devuelto de - 1 o - 2 indica que controla todos los aspectos de seleccionar el elemento y no requiere ninguna acción adicional por el cuadro de lista. Antes de devolver - 1 ó - 2, puede establecer la selección o mover el carácter de intercalación o ambos. Para establecer la selección, utilice [SetCurSel](#setcursel) o [función miembro SetSel](#setsel). Para mover el símbolo de intercalación, use [SetCaretIndex](#setcaretindex).  
  
 Un valor devuelto de 0 o mayor especifica el índice de un elemento en el cuadro de lista y se indica que el cuadro de lista debe realizar la acción predeterminada para la pulsación de tecla en el elemento especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="clistbox"></a>  CListBox::CListBox  
 Construye un objeto `CListBox`.  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CListBox` objeto en dos pasos. En primer lugar, llame al constructor de **ClistBox** y, a continuación, llame a **crear**, que inicializa el cuadro de lista de Windows y lo adjunta a la `CListBox`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="compareitem"></a>  CListBox::CompareItem  
 Lo llama el marco de trabajo para determinar la posición relativa de un nuevo elemento en un cuadro de lista ordenado dibujado por el propietario.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpCompareItemStruct`  
 Un puntero largo a una `COMPAREITEMSTRUCT` estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Indica la posición relativa de los dos elementos se describe en el [COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md) estructura. Puede ser cualquiera de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|-1|Elemento 1 se ordena antes que el elemento 2.|  
|0|Elemento 1 y el elemento 2 ordenan de la misma.|  
|1|Elemento 1 se ordena después del elemento 2.|  
  
 Vea [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) para obtener una descripción de la `COMPAREITEMSTRUCT` estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Si creas un cuadro de lista dibujado por el propietario con el **LBS_SORT** estilo, se debe reemplazar esta función miembro para ayudar a ordenar elementos nuevos agregados al cuadro de lista el marco de trabajo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="create"></a>  CListBox::Create  
 Crea el cuadro de lista de Windows y lo adjunta a la `CListBox` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del cuadro de lista. Aplicar cualquier combinación de [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) al cuadro.  
  
 `rect`  
 Especifica la posición y el tamaño de un cuadro de lista. Puede ser un `CRect` objeto o un `RECT` estructura.  
  
 `pParentWnd`  
 Especifica la ventana del elemento primario del cuadro de lista (normalmente un `CDialog` objeto). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del cuadro de lista  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CListBox` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que inicializa el cuadro de lista de Windows y lo adjunta a la `CListBox` objeto.  
  
 Cuando **crear** se ejecuta, Windows envía la [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) mensajes para el control de cuadro de lista.  
  
 Estos mensajes se controlan de manera predeterminada el [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funciones miembro en la `CWnd` clase base. Para extender el control de mensajes de forma predeterminada, derive una clase de `CListBox`, agregue un mapa de mensajes a la nueva clase y reemplazan las funciones de miembro anterior de controlador de mensajes. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de cuadro de lista.  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
- **WS_VSCROLL** para agregar una barra de desplazamiento vertical  
  
- **WS_HSCROLL** para agregar una barra de desplazamiento horizontal  
  
- **WS_GROUP** a controles de grupo  
  
- **WS_TABSTOP** para permitir a este control de tabulación  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="deleteitem"></a>  CListBox::DeleteItem  
 Lo llama el marco de trabajo cuando el usuario elimina un elemento de un dibujado por el propietario `CListBox` de un objeto o destruye el cuadro de lista.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDeleteItemStruct`  
 Un puntero largo a una ventana de [DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md) estructura que contiene información sobre el elemento eliminado.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Reemplace esta función para volver a dibujar un cuadro de lista dibujado por el propietario, según sea necesario.  
  
 Vea [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) para obtener una descripción de la `DELETEITEMSTRUCT` estructura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="deletestring"></a>  CListBox::DeleteString  
 Elimina el elemento en la posición `nIndex` en el cuadro de lista.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero de la cadena que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un recuento de las cadenas permanecen en la lista. El valor devuelto es **LB_ERR** si `nIndex` especifica un índice mayor que el número de elementos en la lista.  
  
### <a name="remarks"></a>Comentarios  
 Todos los elementos que siguen a `nIndex` ahora Bajar una posición. Por ejemplo, si un cuadro de lista contiene dos elementos, eliminar el primer elemento hará que el resto de producto esté ahora en la primera posición. `nIndex`= 0 para el elemento en la primera posición.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="dir"></a>  CListBox::Dir  
 Agrega una lista de nombres de archivo, las unidades o ambos para un cuadro de lista.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parámetros  
 `attr`  
 Puede ser cualquier combinación de la `enum` describen los valores de **CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus), o cualquier combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|0x0000|Archivo se puede leer o escribir en.|  
|0 x 0001|Archivo pueda leerse desde pero no se escribe en.|  
|0x0002|Archivo está oculto y no aparece en un listado de directorios.|  
|0x0004|Archivo es un archivo de sistema.|  
|0x0010|El nombre especificado por `lpszWildCard` especifica un directorio.|  
|0x0020|Archivo se ha archivado.|  
|0 x 4000|Incluir todas las unidades que coinciden con el nombre especificado por `lpszWildCard`.|  
|0 x 8000|Indicador exclusive. Si se establece la marca exclusiva, se muestran solo los archivos del tipo especificado. En caso contrario, los archivos del tipo especificado se enumeran además de archivos "normales".|  
  
 `lpszWildCard`  
 Apunta a una cadena de especificación de archivo. La cadena puede contener caracteres comodín (por ejemplo, *.\*).  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del último nombre de archivo agregado a la lista. El valor devuelto es **LB_ERR** si se produce un error; el valor devuelto es **LB_ERRSPACE** si no hay suficiente espacio disponible para almacenar las nuevas cadenas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="drawitem"></a>  CListBox::DrawItem  
 Lo llama el marco cuando un aspecto visual de un cuadro de lista dibujado por el propietario cambie.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero largo a una [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura que contiene información sobre el tipo de dibujo necesaria.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** y **itemState** los miembros de la `DRAWITEMSTRUCT` estructura definir la acción de dibujo que va a realizarse.  
  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar el dibujo de un dibujado por el propietario `CListBox` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en `lpDrawItemStruct` antes de este miembro de la función finaliza.  
  
 Vea [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de la `DRAWITEMSTRUCT` estructura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="findstring"></a>  CListBox::FindString  
 Busca la primera cadena en un cuadro de lista que contiene el prefijo especificado sin cambiar la selección del cuadro de lista.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartAfter`  
 Contiene el índice basado en cero del elemento situado delante del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hacia el elemento especificado por `nStartAfter`. Si `nStartAfter` es -1, se busca en el cuadro de lista todo desde el principio.  
  
 `lpszItem`  
 Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda no distingue mayúsculas independiente, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento coincidente, o **LB_ERR** si la búsqueda se realizó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Use la [SelectString](#selectstring) función de miembro para buscar y seleccionar una cadena.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="findstringexact"></a>  CListBox::FindStringExact  
 Busca la primera cadena de cuadro de lista que coincide con la cadena especificada en `lpszFind`.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndexStart`  
 Especifica el índice basado en cero del elemento situado delante del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hacia el elemento especificado por `nIndexStart`. Si `nIndexStart` es -1, se busca en el cuadro de lista todo desde el principio.  
  
 `lpszFind`  
 Apunta a la cadena terminada en null que se buscará. Esta cadena puede contener un nombre de archivo completo, incluida la extensión. La búsqueda no distingue entre mayúsculas y minúsculas, por lo que la cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento coincidente, o **LB_ERR** si la búsqueda se realizó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro de lista se creó con un estilo de dibujo del propietario pero sin la [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, el `FindStringExact` función miembro intenta hacer coincidir el valor de palabra doble con respecto al valor de `lpszFind`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex  
 Recupera el índice de base cero del elemento delimitador actual en el cuadro de lista.  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento delimitador actual, si se realiza correctamente; en caso contrario, **LB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 En un cuadro de lista de selección múltiple, el elemento delimitador es el primer o el último elemento en un bloque de los elementos seleccionados contiguos.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex  
 Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento que tiene el rectángulo de foco en un cuadro de lista. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es el índice del elemento seleccionado, si existe.  
  
### <a name="remarks"></a>Comentarios  
 Puede o no se puede seleccionar el elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::SetCaretIndex](#setcaretindex).  
  
##  <a name="getcount"></a>  CListBox::GetCount  
 Recupera el número de elementos de un cuadro de lista.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el cuadro de lista, o **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El recuento devuelto es una unidad mayor que el valor de índice del último elemento (el índice está basado en cero).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="getcursel"></a>  CListBox::GetCurSel  
 Recupera el índice de base cero del elemento actualmente seleccionado, si existe alguno, en un cuadro de lista de selección única.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento actualmente seleccionado si es un cuadro de lista de selección única. Es `LB_ERR` si no hay ningún elemento está seleccionado actualmente.  
  
 En un cuadro de lista de selección múltiple, el índice del elemento que tiene el foco.  
  
### <a name="remarks"></a>Comentarios  
 No llame a `GetCurSel` para un cuadro de lista de selección múltiple. Use [CListBox::GetSelItems](#getselitems) en su lugar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="gethorizontalextent"></a>  CListBox::GetHorizontalExtent  
 En el cuadro de lista, recupera el ancho en píxeles por el que se puede desplazarse horizontalmente.  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho de desplazamiento del cuadro de lista, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Esto solo es aplicable si el cuadro de lista tiene una barra de desplazamiento horizontal.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="getitemdata"></a>  CListBox::GetItemData  
 Recupera el valor de palabra doble proporcionada por la aplicación asociado con el elemento especificado del cuadro de lista.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de 32 bits asociado con el elemento, o **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El valor de palabra doble era la `dwItemData` parámetro de un [SetItemData](#setitemdata) llamar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr  
 Recupera el valor de 32 bits proporcionada por la aplicación asociado al elemento de cuadro de lista especificada como un puntero ( **void\***).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera un puntero, o -1 si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="getitemheight"></a>  CListBox::GetItemHeight  
 Determina el alto de los elementos de un cuadro de lista.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento en el cuadro de lista. Este parámetro se utiliza sólo si el cuadro de lista tiene la **LBS_OWNERDRAWVARIABLE** estilo; en caso contrario, se debe establecer en 0.  
  
### <a name="return-value"></a>Valor devuelto  
 El alto, en píxeles, de los elementos en el cuadro de lista. Si el cuadro de lista tiene la [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, el valor devuelto es el alto del elemento especificado por `nIndex`. Si se produce un error, el valor devuelto es **LB_ERR**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="getitemrect"></a>  CListBox::GetItemRect  
 Recupera las dimensiones del rectángulo de ese elemento de un cuadro de lista de límites tal y como se muestra actualmente en la ventana de cuadro de lista.  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento.  
  
 `lpRect`  
 Especifica un puntero largo a una [estructura RECT](../../mfc/reference/rect-structure1.md) que recibe las coordenadas de cliente del cuadro de lista del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo  
 Recupera el número de elementos en cada columna.  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos por cada columna de la `CListBox` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208) de mensajes, como se describe en el SDK de Windows.  
  
##  <a name="getlocale"></a>  CListBox::GetLocale  
 Recupera la configuración regional utilizada por el cuadro de lista.  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de identificador (LCID) de configuración regional para las cadenas en el cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, la configuración regional se usa para determinar el criterio de ordenación de las cadenas en un cuadro de lista ordenada.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::SetLocale](#setlocale).  
  
##  <a name="getsel"></a>  CListBox::GetSel  
 Recupera el estado de selección de un elemento.  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un número positivo si se selecciona el elemento especificado; en caso contrario, es 0. El valor devuelto es `LB_ERR` si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro funciona con dos cuadros de lista de selección sencilla y múltiple.  
  
 Para recuperar el índice del elemento de cuadro de lista seleccionado actualmente, utilice [CListBox::GetCurSel](#getcursel).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="getselcount"></a>  CListBox::GetSelCount  
 Recupera el número total de elementos seleccionados en un cuadro de lista de selección múltiple.  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos seleccionados en un cuadro de lista. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es **LB_ERR**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::GetSelItems](#getselitems).  
  
##  <a name="getselitems"></a>  CListBox::GetSelItems  
 Rellena un búfer con una matriz de enteros que especifica los números de producto de los elementos seleccionados en un cuadro de lista de selección múltiple.  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nMaxItems`  
 Especifica el número máximo de elementos seleccionados son cuyos números de producto que se colocarán en el búfer.  
  
 `rgIndex`  
 Especifica un puntero a un búfer lo suficientemente grande como para el número de enteros especificados por `nMaxItems`.  
  
### <a name="return-value"></a>Valor devuelto  
 El número real de elementos se coloca en el búfer. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es `LB_ERR`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="gettext"></a>  CListBox::GetText  
 Obtiene una cadena de un cuadro de lista.  
  
```  
int GetText(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
void GetText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero de la cadena que se va a recuperar.  
  
 `lpszBuffer`  
 Señala al búfer que recibe la cadena. El búfer debe tener espacio suficiente para la cadena y un carácter nulo de terminación. Se puede determinar el tamaño de la cadena de antelación mediante una llamada a la `GetTextLen` función miembro.  
  
 `rString`  
 Referencia a un objeto `CString`.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud (en bytes) de la cadena, sin incluir el carácter nulo de terminación. Si `nIndex` no especifica un índice válido, el valor devuelto es **LB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 La segunda forma de este miembro de función rellena un `CString` objeto con el texto de cadena.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="gettextlen"></a>  CListBox::GetTextLen  
 Obtiene la longitud de una cadena en un elemento de cuadro de lista.  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero de la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la cadena en caracteres, sin incluir el carácter nulo de terminación. Si `nIndex` no especifica un índice válido, el valor devuelto es **LB_ERR**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::GetText](#gettext).  
  
##  <a name="gettopindex"></a>  CListBox::GetTopIndex  
 Recupera el índice de base cero del primer elemento visible en un cuadro de lista.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del primer elemento visible en un cuadro de lista si se realiza correctamente, **LB_ERR** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Inicialmente, el elemento 0 se encuentra en la parte superior del cuadro de lista, pero si se desplaza el cuadro de lista, puede ser otro elemento en la parte superior.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="initstorage"></a>  CListBox::InitStorage  
 Asigna memoria para almacenar los elementos de cuadro de lista.  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `nItems`  
 Especifica el número de elementos que se va a agregar.  
  
 `nBytes`  
 Especifica la cantidad de memoria, en bytes, que se asignan para las cadenas de elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, el número máximo de elementos que puede almacenar el cuadro de lista antes de que se necesita una reasignación de memoria, en caso contrario, **LB_ERRSPACE**, lo que significa que no hay suficiente memoria está disponible.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función antes de agregar un gran número de elementos a un `CListBox`.  
  
 Esta función le ayuda a acelerar la inicialización de los cuadros de lista que tiene un gran número de elementos (más de 100). Preasigna la cantidad especificada de memoria para que las siguientes [AddString](#addstring), [InsertString](#insertstring), y [Dir](#dir) funciones toman el menor tiempo posible. Puede utilizar las estimaciones para los parámetros. Si sobrestimar, se asigna memoria adicional; Si subestimar, la asignación normal se usa para los elementos que superan la cantidad preasignada.  
  
 Windows 95 ó 98 sólo: el `nItems` parámetro está limitado a los valores de 16 bits. Esto significa que los cuadros de lista no pueden contener más de 32.767 elementos. Aunque el número de elementos está restringido, el tamaño total de los elementos de un cuadro de lista está limitado únicamente por la memoria disponible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="insertstring"></a>  CListBox::InsertString  
 Inserta una cadena en el cuadro de lista.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero de la posición para insertar la cadena. Si este parámetro es -1, la cadena se agrega al final de la lista.  
  
 `lpszItem`  
 Apunta a la cadena terminada en null que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la posición donde se insertó la cadena. El valor devuelto es **LB_ERR** si se produce un error; el valor devuelto es **LB_ERRSPACE** si no hay suficiente espacio disponible para almacenar la nueva cadena.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de la [AddString](#addstring) función miembro, `InsertString` no provoca una lista con los [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo que se va a ordenar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint  
 Determina el elemento de cuadro de lista más cercano al punto especificado en `pt`.  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pt`  
 Seleccione esta opción para que se va a buscar el elemento más cercano, especificado con respecto a la esquina superior izquierda del área cliente del cuadro de lista.  
  
 `bOutside`  
 Referencia a un `BOOL` variable que se establecerá en `TRUE` si `pt` está fuera del área cliente del elemento de cuadro de lista más cercano, `FALSE` si `pt` está dentro del área cliente del elemento de cuadro de lista más cercano.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento más cercano al punto especificado en `pt`.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar esta función para determinar qué elemento de cuadro de lista, el cursor del mouse se mueve sobre.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="measureitem"></a>  CListBox::MeasureItem  
 Lo llama el marco cuando se crea un cuadro de lista con un estilo de dibujo del propietario.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMeasureItemStruct`  
 Un puntero largo a una [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de las dimensiones del cuadro de lista. Si el cuadro de lista se crea con el [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. En caso contrario, este miembro se llama solo una vez.  
  
 Para obtener más información sobre el uso de la [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo en un cuadro de lista dibujado por el propietario, creado con la `SubclassDlgItem` función miembro de `CWnd`, vea la explicación en [14 de nota técnica](../../mfc/tn014-custom-controls.md).  
  
 Vea [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de la `MEASUREITEMSTRUCT` estructura **.**  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="resetcontent"></a>  CListBox::ResetContent  
 Quita todos los elementos de un cuadro de lista.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="selectstring"></a>  CListBox::SelectString  
 Busca un elemento de cuadro de lista que coincide con la cadena especificada y, si se encuentra un elemento coincidente, selecciona el elemento.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartAfter`  
 Contiene el índice basado en cero del elemento situado delante del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hacia el elemento especificado por `nStartAfter`. Si `nStartAfter` es -1, se busca en el cuadro de lista todo desde el principio.  
  
 `lpszItem`  
 Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda no distingue mayúsculas independiente, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento seleccionado si la búsqueda se realizó correctamente. Si la búsqueda se realizó correctamente, el valor devuelto es **LB_ERR** y no se cambia la selección actual.  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de lista se desplaza, si es necesario, para mostrar el elemento seleccionado en la vista.  
  
 No se puede usar esta función miembro con un cuadro de lista que tiene el [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo.  
  
 Se selecciona un elemento solo si sus caracteres iniciales (desde el punto inicial) coincide con los caracteres de la cadena especificada por `lpszItem`.  
  
 Use la `FindString` función de miembro para encontrar una cadena sin seleccionar el elemento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="selitemrange"></a>  CListBox::SelItemRange  
 Selecciona varios elementos consecutivos en un cuadro de lista de selección múltiple.  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `bSelect`  
 Especifica cómo se establece la selección. Si `bSelect` es **TRUE**, la cadena está seleccionada y resaltada; si **FALSE**, se quita el resaltado y ya no está seleccionada la cadena.  
  
 `nFirstItem`  
 Especifica el índice de base cero del primer elemento para establecer.  
  
 `nLastItem`  
 Especifica el índice basado en cero del último elemento que se va a establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro solo con cuadros de lista de selección múltiple. Si tiene que seleccionar un solo elemento en un cuadro de lista de selección múltiple, es decir, si `nFirstItem` es igual a `nLastItem` : llame a la [función miembro SetSel](#setsel) función miembro en su lugar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex  
 Establece el delimitador de un cuadro de lista de selección múltiple para comenzar una selección extendida.  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento del cuadro de lista que será el delimitador.  
  
### <a name="remarks"></a>Comentarios  
 En un cuadro de lista de selección múltiple, el elemento delimitador es el primer o el último elemento en un bloque de los elementos seleccionados contiguos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex  
 Establece el rectángulo de foco en el elemento situado en el índice especificado en un cuadro de lista de selección múltiple.  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice basado en cero del elemento que se va a recibir el rectángulo de foco en el cuadro de lista.  
  
 *bScroll*  
 Si este valor es 0, el elemento se desplaza hasta que esté totalmente visible. Si este valor no es 0, el elemento se desplaza hasta que sea al menos parcialmente visible.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento no está visible, se desplaza en la vista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth  
 Establece el ancho en píxeles de todas las columnas en un cuadro de lista de varias columnas (creado con la [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo).  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 `cxWidth`  
 Especifica el ancho en píxeles de todas las columnas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="setcursel"></a>  CListBox::SetCurSel  
 Selecciona una cadena y se desplaza en la vista, si es necesario.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSelect`  
 Especifica el índice de base cero de la cadena que se seleccione. Si `nSelect` es -1, el cuadro de lista se define para no tener ninguna selección.  
  
### <a name="return-value"></a>Valor devuelto  
 `LB_ERR` Si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se selecciona la nueva cadena, en el cuadro de lista se quita el resaltado de la cadena seleccionada anteriormente.  
  
 Utilice esta función miembro solo con cuadros de lista de selección única.  
  
 Para establecer o quitar una selección en un cuadro de lista de selección múltiple, utilice [CListBox::SetSel](#setsel).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="sethorizontalextent"></a>  CListBox:: SetHorizontalExtent  
 Establece el ancho, en píxeles, por el que se puede desplazar horizontalmente un cuadro de lista.  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>Parámetros  
 *cxExtent*  
 Especifica el número de píxeles por el que se puede desplazar horizontalmente el cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño del cuadro de lista es menor que este valor, la barra de desplazamiento horizontal desplazará horizontalmente los elementos en el cuadro de lista. Si el cuadro de lista es grande o superior a este valor, se oculta la barra de desplazamiento horizontal.  
  
 Para responder a una llamada a `SetHorizontalExtent`, debe haber definido el cuadro de lista con el [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) estilo.  
  
 Esta función miembro no es útil para los cuadros de lista de varias columnas. Para cuadros de lista de varias columnas, llame a la `SetColumnWidth` función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="setitemdata"></a>  CListBox::SetItemData  
 Establece un valor de 32 bits asociado con el elemento especificado en un cuadro de lista.  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento.  
  
 `dwItemData`  
 Especifica el valor que se asociará con el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr  
 Establece el valor de 32 bits asociado con el elemento especificado en un cuadro de lista para ser el puntero especificado ( **void\***).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento.  
  
 `pData`  
 Especifica el puntero que se asociará con el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Este puntero es válido durante la vida del cuadro de lista, incluso si la posición del elemento relativa en el cuadro de lista podría cambiar conforme se agregan o quitan elementos. Por lo tanto, puede cambiar el índice del elemento en el cuadro, pero el puntero es confiable.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="setitemheight"></a>  CListBox::SetItemHeight  
 Establece el alto de elementos en un cuadro de lista.  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento en el cuadro de lista. Este parámetro se utiliza sólo si el cuadro de lista tiene la **LBS_OWNERDRAWVARIABLE** estilo; en caso contrario, se debe establecer en 0.  
  
 `cyItemHeight`  
 Especifica el alto, en píxeles, del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si el índice o el alto no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro de lista tiene la [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, esta función establece el alto del elemento especificado por `nIndex`. En caso contrario, esta función establece el alto de todos los elementos en el cuadro de lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="setlocale"></a>  CListBox::SetLocale  
 Establece el identificador de configuración regional de este cuadro de lista.  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNewLocale`  
 El nuevo valor de identificador (LCID) de configuración regional para establecer para el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de identificador (LCID) de configuración regional anterior de este cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 Si **SetLocale** no se llama, el valor predeterminado se obtiene la configuración regional del sistema. Esta configuración regional predeterminada del sistema puede modificarse mediante el uso del Panel de Control de aplicación de configuración Regional (o internacional).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="setsel"></a>  CListBox::SetSel  
 Selecciona una cadena en un cuadro de lista de selección múltiple.  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el índice de base cero de la cadena debe establecerse. Si -1, la selección se agrega o se quita de todas las cadenas, dependiendo del valor de `bSelect`.  
  
 `bSelect`  
 Especifica cómo se establece la selección. Si `bSelect` es `TRUE`, se selecciona y se resalta; si la cadena `FALSE`, se quita el resaltado y ya no está seleccionada la cadena. La cadena especificada se selecciona y se resalta de forma predeterminada.  
  
### <a name="return-value"></a>Valor devuelto  
 `LB_ERR` Si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro solo con cuadros de lista de selección múltiple.  
  
 Para seleccionar un elemento de un cuadro de lista de selección única, use [CListBox::SetCurSel](#setcursel).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="settabstops"></a>  CListBox::SetTabStops  
 Establece las posiciones de tabulación en un cuadro de lista.  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>Parámetros  
 `cxEachStop`  
 Posiciones de tabulación se establecen en cada `cxEachStop` unidades de cuadro de diálogo. Vea *rgTabStops* para obtener una descripción de una unidad de cuadro de diálogo.  
  
 `nTabStops`  
 Especifica el número de posiciones de tabulación en el cuadro de lista.  
  
 `rgTabStops`  
 Señala el primer miembro de una matriz de enteros que contiene las posiciones de tabulación en unidades de cuadro de diálogo. Una unidad de cuadro de diálogo es una distancia horizontal o vertical. Una unidad de cuadro de diálogo horizontal equivale a una cuarta parte de la unidad de base de ancho del cuadro de diálogo actual y una unidad de cuadro de diálogo vertical equivale a una octava parte de la unidad de alto de la base de cuadro de diálogo actual. Las unidades de base del cuadro de diálogo se calculan basándose en el alto y ancho de la fuente del sistema actual. El **GetDialogBaseUnits** la función de Windows devuelve el cuadro de diálogo actual unidades base en píxeles. Las posiciones de tabulación se deben ordenar en sentido ascendente; no se permiten las tabulaciones hacia atrás.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se establecieron todas las fichas; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer las posiciones de tabulación en el tamaño predeterminado de 2 unidades de cuadro de diálogo, llame a la versión de esta función miembro sin parámetros. Para establecer las posiciones de tabulación en un tamaño distinto de 2, llame a la versión con el `cxEachStop` argumento.  
  
 Para establecer las posiciones de tabulación en una matriz de tamaños, utilice la versión con el `rgTabStops` y `nTabStops` argumentos. Se establecerá una tabulación para cada valor de `rgTabStops`, hasta el número especificado por `nTabStops`.  
  
 Para responder a una llamada a la `SetTabStops` función miembro, el cuadro de lista debe haber creado con la [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="settopindex"></a>  CListBox::SetTopIndex  
 Garantiza que un elemento de cuadro de lista determinado esté visible.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento de cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si es correcto, o **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El sistema desplaza el cuadro de lista hasta que el elemento o especificado por `nIndex` aparece en la parte superior de la lista se ha alcanzado cuadro o el intervalo de desplazamiento máximo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem  
 Lo llama el marco de trabajo cuando recibe de la ventana del elemento primario del cuadro de lista un `WM_VKEYTOITEM` mensaje en el cuadro de lista.  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nKey`  
 El código de tecla virtual de la clave que el usuario presionó. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h  
  
 `nIndex`  
 La posición actual del símbolo de intercalación del cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve - 2 para ninguna otra acción, - 1 para la acción predeterminada o un número no negativo para especificar un índice de un elemento de cuadro de lista en el que se va a realizar la acción predeterminada para la pulsación de tecla.  
  
### <a name="remarks"></a>Comentarios  
 El `WM_VKEYTOITEM` se envía el mensaje en el cuadro de lista cuando recibe un `WM_KEYDOWN` mensaje, pero solo si el cuadro de lista cumple las dos opciones siguientes:  
  
-   Tiene la [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) conjunto de estilo.  
  
-   Tiene al menos un elemento.  
  
 Nunca debe llamar esta función usted mismo. Reemplace esta función para proporcionar su propio control personalizado de mensajes del teclado.  
  
 Debe devolver un valor para indicar el marco de la acción que realiza el reemplazo. Un valor devuelto de - 2 indica que la aplicación controla todos los aspectos de seleccionar el elemento y no requiere ninguna acción adicional por el cuadro de lista. Antes de devolver - 2, se puede establecer la selección o mover el carácter de intercalación o ambos. Para establecer la selección, utilice [SetCurSel](#setcursel) o [función miembro SetSel](#setsel). Para mover el símbolo de intercalación, use [SetCaretIndex](#setcaretindex).  
  
 Un valor devuelto de - 1 indica que el cuadro de lista debe realizar la acción predeterminada en respuesta a la pulsación de tecla. La implementación predeterminada devuelve - 1.  
  
 Un valor devuelto de 0 o mayor especifica el índice de un elemento en el cuadro de lista y se indica que el cuadro de lista debe realizar la acción predeterminada para la pulsación de tecla en el elemento especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC CTRLTEST](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Clase CButton](../../mfc/reference/cbutton-class.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [Clase CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [CStatic (clase)](../../mfc/reference/cstatic-class.md)
