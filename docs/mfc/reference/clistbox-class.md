---
title: CListBox (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListBox
dev_langs:
- C++
helpviewer_keywords:
- CListBox class
- list boxes
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
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
ms.openlocfilehash: f4df970f2df35d399c0c700cf504a76482ad3f6d
ms.lasthandoff: 02/24/2017

---
# <a name="clistbox-class"></a>CListBox (clase)
Proporciona la funcionalidad de un cuadro de lista de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|Construye un objeto `CListBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|Agrega una cadena a un cuadro de lista.|  
|[CListBox::CharToItem](#chartoitem)|Invalidación para proporcionar personalizada `WM_CHAR` control para cuadros de lista dibujados por el propietario que no tienen cadenas.|  
|[CListBox::CompareItem](#compareitem)|Llamado por el marco de trabajo para determinar la posición de un nuevo elemento en un cuadro de lista dibujados ordenado.|  
|[CListBox::Create](#create)|Crea el cuadro de lista de Windows y lo adjunta a la `CListBox` objeto.|  
|[CListBox::DeleteItem](#deleteitem)|Llamado por el marco de trabajo cuando el usuario elimina un elemento de un cuadro de lista dibujado por el propietario.|  
|[CListBox::DeleteString](#deletestring)|Elimina una cadena en un cuadro de lista.|  
|[CListBox::Dir](#dir)|Agrega los nombres de archivo, las unidades o desde el directorio actual a un cuadro de lista.|  
|[CListBox::DrawItem](#drawitem)|Llamado por el marco cuando un aspecto visual de un cuadro de lista dibujado por el propietario cambie.|  
|[CListBox::FindString](#findstring)|Busca una cadena en un cuadro de lista.|  
|[CListBox::FindStringExact](#findstringexact)|Busca la primera cadena de cuadro de lista que coincide con una cadena especificada.|  
|[CListBox::GetAnchorIndex](#getanchorindex)|Recupera el índice de base cero del elemento delimitador actual en un cuadro de lista.|  
|[CListBox::GetCaretIndex](#getcaretindex)|Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.|  
|[CListBox::GetCount](#getcount)|Devuelve el número de cadenas en un cuadro de lista.|  
|[CListBox::GetCurSel](#getcursel)|Devuelve el índice de base cero de la cadena actualmente seleccionado en un cuadro de lista.|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Devuelve el ancho en píxeles que un cuadro de lista puede desplazarse horizontalmente.|  
|[CListBox::GetItemData](#getitemdata)|Devuelve el valor de 32 bits asociado al elemento de cuadro de lista.|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|Devuelve un puntero a un elemento de cuadro de lista.|  
|[CListBox::GetItemHeight](#getitemheight)|Determina el alto de los elementos de un cuadro de lista.|  
|[CListBox::GetItemRect](#getitemrect)|Devuelve el rectángulo delimitador del elemento de cuadro de lista que se muestra actualmente.|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Recupera el número de elementos por columna.|  
|[CListBox::GetLocale](#getlocale)|Recupera el identificador de configuración regional de un cuadro de lista.|  
|[CListBox::GetSel](#getsel)|Devuelve el estado de selección de un elemento de cuadro de lista.|  
|[CListBox::GetSelCount](#getselcount)|Devuelve el número de cadenas actualmente seleccionado en un cuadro de lista de selección múltiple.|  
|[CListBox::GetSelItems](#getselitems)|Devuelve los índices de las cadenas actualmente seleccionados en un cuadro de lista.|  
|[CListBox::GetText](#gettext)|Copia un elemento de cuadro de lista en un búfer.|  
|[CListBox::GetTextLen](#gettextlen)|Devuelve la longitud en bytes de un elemento de cuadro de lista.|  
|[CListBox::GetTopIndex](#gettopindex)|Devuelve el índice de la primera cadena visible en un cuadro de lista.|  
|[CListBox::InitStorage](#initstorage)|Preasigna los bloques de memoria para elementos de cuadro de lista y cadenas.|  
|[CListBox::InsertString](#insertstring)|Inserta una cadena en una ubicación específica en un cuadro de lista.|  
|[CListBox::ItemFromPoint](#itemfrompoint)|Devuelve el índice del elemento más cercano de un punto de cuadro de lista.|  
|[CListBox::MeasureItem](#measureitem)|Llamado por el marco de trabajo cuando se crea un cuadro de lista dibujado por el propietario para determinar las dimensiones del cuadro de lista.|  
|[CListBox::ResetContent](#resetcontent)|Borra todas las entradas de un cuadro de lista.|  
|[CListBox::SelectString](#selectstring)|Busca y selecciona una cadena en un cuadro de lista de selección única.|  
|[CListBox::SelItemRange](#selitemrange)|Selecciona o anula la selección de un intervalo de cadenas en un cuadro de lista de selección múltiple.|  
|[CListBox::SetAnchorIndex](#setanchorindex)|Establece el delimitador de un cuadro de lista de selección múltiple para comenzar una selección extendida.|  
|[CListBox::SetCaretIndex](#setcaretindex)|Establece el rectángulo de foco en el elemento en el índice especificado en un cuadro de lista de selección múltiple.|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|Establece el ancho de columna de un cuadro de lista de varias columnas.|  
|[CListBox::SetCurSel](#setcursel)|Selecciona una cadena del cuadro de lista.|  
|[CListBox:: SetHorizontalExtent](#sethorizontalextent)|Establece el ancho en píxeles que un cuadro de lista puede desplazarse horizontalmente.|  
|[CListBox::SetItemData](#setitemdata)|Establece el valor de 32 bits asociado al elemento de cuadro de lista.|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|Establece un puntero al elemento de cuadro de lista.|  
|[CListBox::SetItemHeight](#setitemheight)|Establece el alto de los elementos en un cuadro de lista.|  
|[CListBox::SetLocale](#setlocale)|Establece el identificador de configuración regional para un cuadro de lista.|  
|[CListBox::SetSel](#setsel)|Selecciona o anula la selección de un elemento de cuadro de lista en un cuadro de lista de selección múltiple.|  
|[CListBox::SetTabStops](#settabstops)|Establece las posiciones de tabulación en un cuadro de lista.|  
|[CListBox::SetTopIndex](#settopindex)|Establece el índice de base cero de la primera cadena visible en un cuadro de lista.|  
|[CListBox::VKeyToItem](#vkeytoitem)|Invalidación para proporcionar personalizada `WM_KEYDOWN` control para cuadros de lista con el **LBS_WANTKEYBOARDINPUT** conjunto de estilos.|  
  
## <a name="remarks"></a>Comentarios  
 Un cuadro de lista muestra una lista de elementos, como nombres de archivo, que puede ver y seleccionar el usuario.  
  
 En un cuadro de lista de selección única, el usuario puede seleccionar un único elemento. En un cuadro de lista de selección múltiple, se puede seleccionar un intervalo de elementos. Cuando el usuario selecciona un elemento, se resalta y el cuadro de lista, envía un mensaje de notificación a la ventana primaria.  
  
 Puede crear un cuadro de lista desde una plantilla de cuadro de diálogo o directamente en el código. Para crear directamente, construir la `CListBox` objeto, a continuación, llame a la [crear](#create) función de miembro para crear el control de cuadro de lista de Windows y adjuntarlo a la `CListBox` objeto. Para utilizar un cuadro de lista en una plantilla de cuadro de diálogo, declare una variable de cuadro de lista en la clase de cuadro de diálogo y, a continuación, usar `DDX_Control` en la clase de cuadro de diálogo `DoDataExchange` (función) para conectarse a la variable miembro para el control. (Esto se hace por usted automáticamente cuando se agrega una variable de control a la clase de cuadro de diálogo).  
  
 Construcción puede ser un proceso de un paso en una clase derivada de `CListBox`. Escribir un constructor para la clase derivada y llamada **crear** desde dentro del constructor.  
  
 Si desea controlar mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregar una función de miembro de entrada y el controlador de mensajes del mapa de mensajes a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes toma la forma siguiente:  
  
 `ON_Notification( id, memberFxn )`  
  
 donde `id` especifica el identificador de ventana secundaria del control de cuadro de lista que se envía la notificación y `memberFxn` es el nombre de la función de miembro primario que ha escrito para controlar la notificación.  
  
 Prototipo de función del elemento primario es el siguiente:  
  
 `afx_msg void memberFxn( );`  
  
 Siguiente es una lista de posibles entradas de mapa de mensajes y una descripción de los casos en que se enviará al elemento primario:  
  
- **ON_LBN_DBLCLK** el usuario hace doble clic en una cadena en un cuadro de lista. Un cuadro de lista que tiene el [LBS_NOTIFY](../../mfc/reference/list-box-styles.md) estilo enviará este mensaje de notificación.  
  
- **ON_LBN_ERRSPACE** el cuadro de lista no puede asignar memoria suficiente para satisfacer la solicitud.  
  
- **ON_LBN_KILLFOCUS** el cuadro de lista está perdiendo el foco de entrada.  
  
- **ON_LBN_SELCANCEL** se cancela la selección actual del cuadro de lista. Este mensaje sólo se envía cuando un cuadro de lista tiene la **LBS_NOTIFY** estilo.  
  
- **ON_LBN_SELCHANGE** ha cambiado la selección en el cuadro de lista. Esta notificación no se envía si se modifica la selección mediante la [CListBox::SetCurSel](#setcursel) función miembro. Esta notificación sólo se aplica a un cuadro de lista que tiene el **LBS_NOTIFY** estilo. El **LBN_SELCHANGE** mensaje de notificación se envía para un cuadro de lista de selección múltiple cuando el usuario presiona una tecla de dirección, incluso si no cambia la selección.  
  
- **ON_LBN_SETFOCUS** recibe el foco de entrada en el cuadro de lista.  
  
- **ON_WM_CHARTOITEM** recibe un cuadro de lista dibujados con ningún cadenas un `WM_CHAR` mensaje.  
  
- **ON_WM_VKEYTOITEM** un cuadro de lista con el **LBS_WANTKEYBOARDINPUT** estilo recibe un `WM_KEYDOWN` mensaje.  
  
 Si crea un `CListBox` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CListBox` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un `CListBox` objeto dentro de una ventana, puede que necesite destruir el `CListBox` objeto. Si crea la `CListBox` objeto en la pila, se destruye automáticamente. Si crea el `CListBox` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** en el objeto destruirla cuando el usuario cierra la ventana primaria.  
  
 Si asigna memoria en el `CListBox` objeto, invalide el `CListBox` destructor desechar la asignación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameaddstringa--clistboxaddstring"></a><a name="addstring"></a>CListBox::AddString  
 Agrega una cadena a un cuadro de lista.  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszItem`  
 Apunta a la cadena terminada en null que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero en la cadena en el cuadro de lista. El valor devuelto es **LB_ERR** si se produce un error; el valor devuelto es **LB_ERRSPACE** si no hay suficiente espacio disponible para almacenar la nueva cadena.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro de lista no se creó con el [LBS_SORT](../../mfc/reference/list-box-styles.md) estilo, la cadena se agrega al final de la lista. De lo contrario, la cadena se inserta en la lista y la lista está ordenada. Si el cuadro de lista se creó con el **LBS_SORT** estilo pero no el [LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md) estilo, el marco de trabajo ordena la lista por una o más llamadas a la `CompareItem` función miembro.  
  
 Utilice [InsertString](#insertstring) para insertar una cadena en una ubicación específica en el cuadro de lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&3;](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="a-namechartoitema--clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::CharToItem  
 Llamado por el marco de trabajo cuando recibe de la ventana del elemento primario del cuadro de lista un `WM_CHARTOITEM` mensaje del cuadro de lista.  
  
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
 Devuelve – 1 o – 2 para ninguna otra acción o un número no negativo para especificar un índice de un elemento de cuadro de lista en la que se va a realizar la acción predeterminada para la pulsación de tecla. La implementación predeterminada devuelve – 1.  
  
### <a name="remarks"></a>Comentarios  
 El `WM_CHARTOITEM` se envía el mensaje en el cuadro de lista cuando recibe un `WM_CHAR` mensaje, pero sólo si el cuadro de lista cumple todos estos criterios:  
  
-   Es un cuadro de lista dibujado por el propietario.  
  
-   No tiene la [LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md) conjunto de estilos.  
  
-   Tiene al menos un elemento.  
  
 Nunca debe llamar esta función por sí mismo. Reemplazar esta función para proporcionar su propio control personalizado de mensajes del teclado.  
  
 En el reemplazo, debe devolver un valor para indicar el marco de la acción que ha realizado. Un valor devuelto de – 1 o – 2 indica que controla todos los aspectos de seleccionando el elemento y no requiere ninguna acción por el cuadro de lista. Antes de devolver – 1 o – 2, podría establecer la selección o mover el símbolo de intercalación o ambos. Para establecer la selección, utilice [SetCurSel](#setcursel) o [función miembro SetSel](#setsel). Para mover el símbolo de intercalación, use [SetCaretIndex](#setcaretindex).  
  
 Un valor devuelto de 0 o superior especifica el índice de un elemento en el cuadro de lista y se indica que el cuadro de lista debe realizar la acción predeterminada para la pulsación de tecla en el elemento especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&4;](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="a-nameclistboxa--clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox  
 Construye un objeto `CListBox`.  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CListBox` objeto en dos pasos. En primer lugar, llame al constructor de **ClistBox** y, a continuación, llame a **crear**, que inicializa el cuadro de lista de Windows y lo adjunta a la `CListBox`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CListBox](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="a-namecompareitema--clistboxcompareitem"></a><a name="compareitem"></a>CListBox::CompareItem  
 Llamado por el marco de trabajo para determinar la posición relativa de un nuevo elemento en un cuadro de lista dibujados ordenado.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpCompareItemStruct`  
 Un puntero largo a una `COMPAREITEMSTRUCT` estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Indica la posición relativa de los dos elementos que se describe en el [COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md) estructura. Puede ser cualquiera de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|–1|Elemento 1 se ordena antes que el elemento 2.|  
|0|Elemento 1 y 2 del artículo ordenan de la misma.|  
|1|Elemento 1 se ordena después del elemento 2.|  
  
 Consulte [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) para obtener una descripción de la `COMPAREITEMSTRUCT` estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Si crea un cuadro de lista dibujado por el propietario con el **LBS_SORT** estilo, debe reemplazar esta función miembro para ayudarle a ordenar elementos nuevos agregados a la lista el marco de trabajo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#5;](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="a-namecreatea--clistboxcreate"></a><a name="create"></a>CListBox::Create  
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
 Especifica el estilo del cuadro de lista. Aplicar cualquier combinación de [estilos de cuadro de lista](../../mfc/reference/list-box-styles.md) al cuadro.  
  
 `rect`  
 Especifica la posición y el tamaño del cuadro de lista. Puede ser un `CRect` objeto o un `RECT` estructura.  
  
 `pParentWnd`  
 Especifica la ventana primaria del cuadro de lista (normalmente un `CDialog` objeto). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del cuadro de lista  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CListBox` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que inicializa el cuadro de lista de Windows y lo adjunta a la `CListBox` objeto.  
  
 Cuando **crear** se ejecuta, Windows envía la [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) mensajes para el control de cuadro de lista.  
  
 Estos mensajes se controlan de manera predeterminada el [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funciones miembro en la `CWnd` clase base. Para extender el control de mensajes de forma predeterminada, derive una clase de `CListBox`, agregue un mapa de mensajes a la nueva clase y reemplazar las funciones miembro de controlador de mensaje anterior. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/window-styles.md) a un control de cuadro de lista.  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
- **WS_VSCROLL** para agregar una barra de desplazamiento vertical  
  
- **WS_HSCROLL** para agregar una barra de desplazamiento horizontal  
  
- **WS_GROUP** para agrupar controles  
  
- **WS_TABSTOP** para permitir que este control de tabulación  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#2;](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="a-namedeleteitema--clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem  
 Llamado por el marco de trabajo cuando el usuario elimina un elemento de un dibujo propietario `CListBox` de objeto o destruye el cuadro de lista.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDeleteItemStruct`  
 Un puntero largo a Windows [DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md) estructura que contiene información sobre el elemento eliminado.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Reemplazar esta función para volver a dibujar un cuadro de lista dibujado por el propietario, según sea necesario.  
  
 Consulte [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) para obtener una descripción de la `DELETEITEMSTRUCT` estructura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&6;](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="a-namedeletestringa--clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString  
 Elimina el elemento en la posición `nIndex` del cuadro de lista.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero de la cadena que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 Recuento de las cadenas restantes en la lista. El valor devuelto es **LB_ERR** si `nIndex` especifica un índice mayor que el número de elementos de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Todos los elementos que siguen a `nIndex` ahora Bajar una posición. Por ejemplo, si un cuadro de lista contiene dos elementos, eliminar el primer elemento hará que el resto de producto estar en la primera posición. `nIndex`=&0; para el elemento en la primera posición.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#7;](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="a-namedira--clistboxdir"></a><a name="dir"></a>CListBox::Dir  
 Agrega una lista de nombres de archivo, las unidades o ambos en un cuadro de lista.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parámetros  
 `attr`  
 Puede ser cualquier combinación de los `enum` valores que se describen en **CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus), o cualquier combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|0x0000|Archivo se puede leer o escribir.|  
|0 x&0001;|Pueden leer desde pero no escriben en el archivo.|  
|0 x&0002;|Archivo está oculto y no aparece en una lista de directorios.|  
|0 x&0004;|Es un archivo de sistema.|  
|0x0010|El nombre especificado por `lpszWildCard` especifica un directorio.|  
|0x0020|Archivo se ha archivado.|  
|0 x&4000;|Incluir todas las unidades que coinciden con el nombre especificado por `lpszWildCard`.|  
|0 x&8000;|Indicador exclusive. Si se establece el indicador exclusive, se muestran sólo los archivos del tipo especificado. De lo contrario, los archivos del tipo especificado se enumeran además de los archivos "normales".|  
  
 `lpszWildCard`  
 Apunta a una cadena de la especificación de archivo. La cadena puede contener caracteres comodín (por ejemplo, *.\*).  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del nombre del último archivo agregado a la lista. El valor devuelto es **LB_ERR** si se produce un error; el valor devuelto es **LB_ERRSPACE** si no hay suficiente espacio disponible para almacenar las nuevas cadenas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&8;](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="a-namedrawitema--clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem  
 Llamado por el marco cuando un aspecto visual de un cuadro de lista dibujado por el propietario cambie.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero largo a una [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura que contiene información sobre el tipo de dibujo necesario.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** y **itemState** los miembros de la `DRAWITEMSTRUCT` estructura definir la acción de dibujo que se realiza.  
  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar un dibujados por el propietario del dibujo `CListBox` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para el contexto de presentación proporcionado en `lpDrawItemStruct` antes de este miembro de función termina.  
  
 Consulte [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de la `DRAWITEMSTRUCT` estructura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#9;](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="a-namefindstringa--clistboxfindstring"></a><a name="findstring"></a>CListBox::FindString  
 Busca la primera cadena en un cuadro de lista que contiene el prefijo especificado sin cambiar la selección del cuadro de lista.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartAfter`  
 Contiene el índice de base cero del elemento delante del primer elemento que se buscará. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa en la parte superior del cuadro de lista hasta el elemento especificado por `nStartAfter`. Si `nStartAfter` es –&1;, se busca en el cuadro de lista todo desde el principio.  
  
 `lpszItem`  
 Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es el caso independiente, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento coincidente, o **LB_ERR** si la búsqueda se realizó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [SelectString](#selectstring) función de miembro para buscar y seleccionar una cadena.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#10;](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="a-namefindstringexacta--clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact  
 Busca la primera cadena de cuadro de lista que coincide con la cadena especificada en `lpszFind`.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndexStart`  
 Especifica el índice de base cero del elemento delante del primer elemento que se buscará. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa en la parte superior del cuadro de lista hasta el elemento especificado por `nIndexStart`. Si `nIndexStart` es –&1;, se busca en el cuadro de lista todo desde el principio.  
  
 `lpszFind`  
 Apunta a la cadena terminada en null para buscar. Esta cadena puede contener un nombre de archivo completo, incluida la extensión. La búsqueda no distingue mayúsculas de minúsculas, por lo que la cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento coincidente, o **LB_ERR** si la búsqueda se realizó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Si el cuadro de lista se creó con un estilo de dibujo de propietario pero sin la [LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md) estilo, el `FindStringExact` función miembro intenta hacer coincidir el valor de palabra doble con el valor de `lpszFind`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#11;](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="a-namegetanchorindexa--clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex  
 Recupera el índice de base cero del elemento delimitador actual en el cuadro de lista.  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento delimitador actual, si es correcto; de lo contrario, **LB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 En un cuadro de lista de selección múltiple, el elemento de anclaje es el primer o el último elemento en un bloque contiguo elementos seleccionados.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="a-namegetcaretindexa--clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex  
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
  
##  <a name="a-namegetcounta--clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount  
 Recupera el número de elementos de un cuadro de lista.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el cuadro de lista o **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El recuento devuelto es una unidad mayor que el valor de índice del último elemento (el índice está basado en cero).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#12;](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="a-namegetcursela--clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel  
 Recupera el índice de base cero del elemento actualmente seleccionado, si existe alguno, en un cuadro de lista de selección única.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento actualmente seleccionado si es un cuadro de lista de selección única. Es `LB_ERR` si ningún elemento seleccionado actualmente.  
  
 En un cuadro de lista de selección múltiple, el índice del elemento que tiene el foco.  
  
### <a name="remarks"></a>Comentarios  
 No llame a `GetCurSel` para un cuadro de lista de selección múltiple. Utilice [CListBox::GetSelItems](#getselitems) en su lugar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#13;](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="a-namegethorizontalextenta--clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent  
 En el cuadro de lista, recupera el ancho en píxeles por el que se puede desplazarse horizontalmente.  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho de desplazamiento del cuadro de lista, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Esto sólo es aplicable si el cuadro de lista tiene una barra de desplazamiento horizontal.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#14;](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="a-namegetitemdataa--clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData  
 Recupera el valor de palabra doble proporcionada por la aplicación asociado con el elemento especificado del cuadro de lista.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de 32 bits asociado al elemento o **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El valor de palabra doble era la `dwItemData` parámetro de un [SetItemData](#setitemdata) llamar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#15;](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="a-namegetitemdataptra--clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr  
 Recupera el valor de 32 bits proporcionada por la aplicación asociado con el elemento de cuadro de lista especificado como un puntero ( **void\***).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera un puntero, o –&1; si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&16;](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="a-namegetitemheighta--clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight  
 Determina el alto de los elementos de un cuadro de lista.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento en el cuadro de lista. Este parámetro se utiliza sólo si el cuadro de lista tiene la **LBS_OWNERDRAWVARIABLE** estilo; en caso contrario, se debe establecer en 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Alto, en píxeles, de los elementos en el cuadro de lista. Si el cuadro de lista tiene la [LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md) estilo, el valor devuelto es el alto del elemento especificado por `nIndex`. Si se produce un error, el valor devuelto es **LB_ERR**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#17;](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="a-namegetitemrecta--clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect  
 Recupera las dimensiones del rectángulo de ese elemento de un cuadro de lista de límites como se muestra actualmente en la ventana de cuadro de lista.  
  
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
 [!code-cpp[NVC_MFC_CListBox&#18;](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="a-namegetlistboxinfoa--clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo  
 Recupera el número de elementos por columna.  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos por la columna de la `CListBox` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208) de mensajes, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetlocalea--clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale  
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
  
##  <a name="a-namegetsela--clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel  
 Recupera el estado de selección de un elemento.  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un número positivo si está seleccionado el elemento especificado; de lo contrario, es 0. El valor devuelto es `LB_ERR` si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro funciona con dos cuadros de lista de selección única y múltiple.  
  
 Para recuperar el índice del elemento de cuadro de lista seleccionado actualmente, utilice [CListBox::GetCurSel](#getcursel).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&19;](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="a-namegetselcounta--clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount  
 Recupera el número total de elementos seleccionados en un cuadro de lista de selección múltiple.  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos seleccionados en un cuadro de lista. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es **LB_ERR**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::GetSelItems](#getselitems).  
  
##  <a name="a-namegetselitemsa--clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems  
 Llena un búfer con una matriz de enteros que especifica los números de producto de los elementos seleccionados en un cuadro de lista de selección múltiple.  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nMaxItems`  
 Especifica el número máximo de elementos seleccionados son cuyos números de elemento que se colocarán en el búfer.  
  
 `rgIndex`  
 Especifica un puntero a un búfer suficientemente grande para el número de enteros especificados por `nMaxItems`.  
  
### <a name="return-value"></a>Valor devuelto  
 El número real de elementos se coloca en el búfer. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es `LB_ERR`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#20;](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="a-namegettexta--clistboxgettext"></a><a name="gettext"></a>CListBox::GetText  
 Obtiene una cadena en un cuadro de lista.  
  
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
 Señala al búfer que recibe la cadena. El búfer debe tener espacio suficiente para la cadena y un carácter nulo de terminación. Se puede determinar el tamaño de la cadena de antemano llamando el `GetTextLen` función miembro.  
  
 `rString`  
 Referencia a un objeto `CString`.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud (en bytes) de la cadena, excepto el carácter nulo de terminación. Si `nIndex` no especifica un índice válido, el valor devuelto es **LB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 La segunda forma de este miembro de función llena un `CString` objeto con el texto de la cadena.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFC_CListBox](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="a-namegettextlena--clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen  
 Obtiene la longitud de una cadena en un elemento de cuadro de lista.  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero de la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la cadena de caracteres, excepto el carácter nulo de terminación. Si `nIndex` no especifica un índice válido, el valor devuelto es **LB_ERR**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::GetText](#gettext).  
  
##  <a name="a-namegettopindexa--clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GetTopIndex  
 Recupera el índice de base cero del primer elemento visible en un cuadro de lista.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del primer elemento visible en un cuadro de lista si se realiza correctamente, **LB_ERR** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Inicialmente, es el elemento 0 en la parte superior del cuadro de lista, pero si se desplaza el cuadro de lista, puede ser otro elemento en la parte superior.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#22;](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="a-nameinitstoragea--clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage  
 Asigna memoria para almacenar los elementos de cuadro de lista.  
  
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
 Si tiene éxito, el número máximo de elementos que puede almacenar el cuadro de lista antes de que es necesaria una reasignación de memoria, de lo contrario, **LB_ERRSPACE**, lo que significa que no hay suficiente memoria está disponible.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función antes de agregar un gran número de elementos a un `CListBox`.  
  
 Esta función le ayuda a acelerar la inicialización de los cuadros de lista que tiene un gran número de elementos (más de 100). Preasigna la cantidad especificada de memoria para que las siguientes [AddString](#addstring), [InsertString](#insertstring), y [Dir](#dir) funciones toman el menor tiempo posible. Puede utilizar las estimaciones para los parámetros. Si sobrestimar, se asigna memoria adicional; Si subestimar, la asignación normal se usa para los elementos que superan la cantidad preasignada.  
  
 Sólo Windows 95 ó 98: el `nItems` parámetro está limitado a los valores de 16 bits. Esto significa que los cuadros de lista no pueden contener más de 32.767 elementos. Aunque el número de elementos está restringido, el tamaño total de los elementos de un cuadro de lista está limitado sólo por la memoria disponible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFC_CListBox #](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="a-nameinsertstringa--clistboxinsertstring"></a><a name="insertstring"></a>CListBox::InsertString  
 Inserta una cadena en el cuadro de lista.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero de la posición para insertar la cadena. Si este parámetro es –1, la cadena se agrega al final de la lista.  
  
 `lpszItem`  
 Apunta a la cadena terminada en null que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la posición donde se insertó la cadena. El valor devuelto es **LB_ERR** si se produce un error; el valor devuelto es **LB_ERRSPACE** si no hay suficiente espacio disponible para almacenar la nueva cadena.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de la [AddString](#addstring) función miembro, `InsertString` no provoca una lista con los [LBS_SORT](../../mfc/reference/list-box-styles.md) estilo que se va a ordenar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#24;](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="a-nameitemfrompointa--clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemFromPoint  
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
 Hacer referencia a un `BOOL` variable que se establecerá en `TRUE` si `pt` está fuera del área cliente del elemento más cercano de cuadro de lista, `FALSE` si `pt` está dentro del área cliente del elemento más cercano de cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento más cercano al punto especificado en `pt`.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar esta función para determinar qué elemento de cuadro de lista, el cursor del mouse se mueve sobre.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="a-namemeasureitema--clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem  
 Lo llama el marco de trabajo cuando se crea un cuadro de lista con un estilo de dibujo del propietario.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMeasureItemStruct`  
 Un puntero largo a una [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de las dimensiones del cuadro de lista. Si el cuadro de lista se crea con el [LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md) estilo, el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. De lo contrario, este miembro se llama solo una vez.  
  
 Para obtener más información acerca del uso de la [LBS_OWNERDRAWFIXED](../../mfc/reference/list-box-styles.md) estilo en un cuadro de lista dibujado por el propietario, creado con el `SubclassDlgItem` función miembro de `CWnd`, vea la explicación en [14 de nota técnica](../../mfc/tn014-custom-controls.md).  
  
 Consulte [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de la `MEASUREITEMSTRUCT` estructura **.**  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#25;](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="a-nameresetcontenta--clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent  
 Quita todos los elementos de un cuadro de lista.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFC_CListBox #](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="a-nameselectstringa--clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString  
 Busca un elemento de cuadro de lista que coincide con la cadena especificada y, si se encuentra un elemento coincidente, selecciona el elemento.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartAfter`  
 Contiene el índice de base cero del elemento delante del primer elemento que se buscará. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa en la parte superior del cuadro de lista hasta el elemento especificado por `nStartAfter`. Si `nStartAfter` es –&1;, se busca en el cuadro de lista todo desde el principio.  
  
 `lpszItem`  
 Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es el caso independiente, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento seleccionado, si la búsqueda se realizó correctamente. Si la búsqueda se realizó correctamente, el valor devuelto es **LB_ERR** y no se cambia la selección actual.  
  
### <a name="remarks"></a>Comentarios  
 Se desplaza el cuadro de lista, si es necesario, para mostrar el elemento seleccionado.  
  
 Esta función miembro no se puede usar con un cuadro de lista que tiene el [LBS_MULTIPLESEL](../../mfc/reference/list-box-styles.md) estilo.  
  
 Se selecciona un elemento sólo si sus caracteres iniciales (desde el punto inicial) coinciden con los caracteres de la cadena especificada por `lpszItem`.  
  
 Utilice la `FindString` función de miembro para buscar una cadena sin seleccionar el elemento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&27;](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="a-nameselitemrangea--clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange  
 Selecciona varios elementos consecutivos en un cuadro de lista de selección múltiple.  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `bSelect`  
 Especifica cómo se establece la selección. Si `bSelect` es **TRUE**, está seleccionada y resaltada; si la cadena **FALSE**, se quita el resaltado y la cadena ya no está seleccionada.  
  
 `nFirstItem`  
 Especifica el índice de base cero del primer elemento para establecer.  
  
 `nLastItem`  
 Especifica el índice de base cero del último elemento para establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro sólo con cuadros de lista de selección múltiple. Si necesita seleccionar un único elemento en un cuadro de lista de selección múltiple, es decir, si `nFirstItem` es igual a `nLastItem` : llame a la [función miembro SetSel](#setsel) función miembro en su lugar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#28;](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="a-namesetanchorindexa--clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex  
 Establece el delimitador de un cuadro de lista de selección múltiple para comenzar una selección extendida.  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento de cuadro de lista que será el delimitador.  
  
### <a name="remarks"></a>Comentarios  
 En un cuadro de lista de selección múltiple, el elemento de anclaje es el primer o el último elemento en un bloque contiguo elementos seleccionados.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#29;](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="a-namesetcaretindexa--clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex  
 Establece el rectángulo de foco en el elemento en el índice especificado en un cuadro de lista de selección múltiple.  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento que se va a recibir el rectángulo de foco en el cuadro de lista.  
  
 *bScroll*  
 Si este valor es 0, el elemento se desplaza hasta que esté totalmente visible. Si este valor no es 0, el elemento se desplaza hasta que sea al menos parcialmente visible.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento no está visible, se desplaza en la vista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&30;](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="a-namesetcolumnwidtha--clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth  
 Establece el ancho en píxeles de todas las columnas en un cuadro de lista de varias columnas (creado con la [LBS_MULTICOLUMN](../../mfc/reference/list-box-styles.md) estilo).  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 `cxWidth`  
 Especifica el ancho en píxeles de todas las columnas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#31;](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="a-namesetcursela--clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel  
 Selecciona una cadena y se desplaza en la vista, si es necesario.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSelect`  
 Especifica el índice de base cero de la cadena que va a seleccionar. Si `nSelect` es -1, el cuadro de lista se configura para no tener ninguna selección.  
  
### <a name="return-value"></a>Valor devuelto  
 `LB_ERR`Si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se selecciona la nueva cadena, en el cuadro de lista se quita el resaltado de la cadena seleccionada anteriormente.  
  
 Utilice esta función miembro sólo con cuadros de lista de selección única.  
  
 Para establecer o quitar una selección en un cuadro de lista de selección múltiple, utilice [CListBox::SetSel](#setsel).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#32;](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="a-namesethorizontalextenta--clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox:: SetHorizontalExtent  
 Establece el ancho, en píxeles, por el que un cuadro de lista puede desplazarse horizontalmente.  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>Parámetros  
 *cxExtent*  
 Especifica el número de píxeles que el cuadro de lista puede desplazarse horizontalmente.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño del cuadro de lista es menor que este valor, la barra de desplazamiento horizontal desplazará horizontalmente elementos en el cuadro de lista. Si el cuadro de lista es tan grande o superior a este valor, se oculta la barra de desplazamiento horizontal.  
  
 Para responder a una llamada a `SetHorizontalExtent`, debe haber definido el cuadro de lista con el [WS_HSCROLL](../../mfc/reference/window-styles.md) estilo.  
  
 Esta función miembro no es útil para los cuadros de lista de varias columnas. Cuadros de lista de varias columnas, llame a la `SetColumnWidth` función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&33;](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="a-namesetitemdataa--clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData  
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
 Especifica el valor asociado con el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#34;](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="a-namesetitemdataptra--clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr  
 Establece el valor de 32 bits asociado con el elemento especificado en un cuadro de lista sea el puntero especificado ( **void\***).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento.  
  
 `pData`  
 Especifica el puntero para asociarse con el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Este puntero es válido durante la vida del cuadro de lista, aunque la posición relativa del elemento del cuadro de lista podría cambiar conforme se agregan o quitan elementos. Por lo tanto, puede cambiar el índice del elemento dentro del cuadro, pero el puntero permanece confiable.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#35;](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="a-namesetitemheighta--clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight  
 Establece el alto de los elementos en un cuadro de lista.  
  
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
 Si el cuadro de lista tiene la [LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md) estilo, esta función establece el alto del elemento especificado por `nIndex`. De lo contrario, esta función establece el alto de todos los elementos en el cuadro de lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#36;](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="a-namesetlocalea--clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale  
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
 Si **SetLocale** no se llama, el valor predeterminado se obtiene la configuración regional del sistema. Se puede modificar esta configuración regional predeterminada del sistema mediante el uso del Panel de Control Configuración Regional (o internacional) de aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#37;](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="a-namesetsela--clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel  
 Selecciona una cadena en un cuadro de lista de selección múltiple.  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el índice de base cero de la cadena que se establece. Si -1, la selección se agrega o se quita de todas las cadenas, dependiendo del valor de `bSelect`.  
  
 `bSelect`  
 Especifica cómo se establece la selección. Si `bSelect` es `TRUE`, está seleccionada y resaltada; si la cadena `FALSE`, se quita el resaltado y la cadena ya no está seleccionada. La cadena especificada está seleccionada y resaltada de forma predeterminada.  
  
### <a name="return-value"></a>Valor devuelto  
 `LB_ERR`Si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro sólo con cuadros de lista de selección múltiple.  
  
 Para seleccionar un elemento de un cuadro de lista de selección única, use [CListBox::SetCurSel](#setcursel).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#38;](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="a-namesettabstopsa--clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabStops  
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
 Las tabulaciones se establecen en cada `cxEachStop` unidades de cuadro de diálogo. Consulte *rgTabStops* para obtener una descripción de una unidad de cuadro de diálogo.  
  
 `nTabStops`  
 Especifica el número de posiciones de tabulación en el cuadro de lista.  
  
 `rgTabStops`  
 Señala el primer miembro de una matriz de enteros que contiene las posiciones de tabulación en unidades de cuadro de diálogo. Una unidad de cuadro de diálogo es una distancia horizontal o vertical. Una unidad de cuadro de diálogo horizontal equivale a una cuarta parte de la unidad base de ancho de cuadro de diálogo actual y una unidad de cuadro de diálogo vertical equivale a una octava parte de la unidad de alto de la base del cuadro de diálogo actual. Las unidades de base del cuadro de diálogo se calculan basándose en el alto y ancho de la fuente del sistema actual. El **GetDialogBaseUnits** función Windows devuelve el cuadro de diálogo actual unidades base en píxeles. Las tabulaciones deben estar ordenadas en sentido ascendente; no se permiten las tabulaciones hacia atrás.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se han establecido todas las fichas; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer las tabulaciones en el tamaño predeterminado de 2 unidades de cuadro de diálogo, llame a la versión de esta función miembro sin parámetros. Para establecer tabulaciones en un tamaño distinto de 2, llame a la versión con el `cxEachStop` argumento.  
  
 Para establecer tabulaciones en una matriz de tamaños, utilice la versión con el `rgTabStops` y `nTabStops` argumentos. Se establecerá una tabulación para cada valor de `rgTabStops`, hasta el número especificado por `nTabStops`.  
  
 Para responder a una llamada a la `SetTabStops` función miembro, el cuadro de lista debe haber creado con el [LBS_USETABSTOPS](../../mfc/reference/list-box-styles.md) estilo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox&#39;](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="a-namesettopindexa--clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SetTopIndex  
 Garantiza que un elemento concreto del cuadro de lista es visible.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el índice de base cero del elemento de cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si es correcto, o **LB_ERR** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El sistema desplaza el cuadro de lista hasta que el elemento o especificado por `nIndex` aparece en la parte superior de la lista se ha alcanzado cuadro o el intervalo máximo de desplazamiento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox Nº&40;](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="a-namevkeytoitema--clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem  
 Llamado por el marco de trabajo cuando recibe de la ventana del elemento primario del cuadro de lista un `WM_VKEYTOITEM` mensaje del cuadro de lista.  
  
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
 Devuelve – 2 para ninguna otra acción, – 1 para la acción predeterminada o un número no negativo para especificar un índice de un elemento de cuadro de lista en la que se va a realizar la acción predeterminada para la pulsación de tecla.  
  
### <a name="remarks"></a>Comentarios  
 El `WM_VKEYTOITEM` se envía el mensaje en el cuadro de lista cuando recibe un `WM_KEYDOWN` mensaje, pero sólo si el cuadro de lista cumple las dos opciones siguientes:  
  
-   Tiene la [LBS_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md) conjunto de estilos.  
  
-   Tiene al menos un elemento.  
  
 Nunca debe llamar esta función por sí mismo. Reemplazar esta función para proporcionar su propio control personalizado de mensajes del teclado.  
  
 Debe devolver un valor para indicar el marco de la acción que realiza el reemplazo. Un valor devuelto de – 2 indica que la aplicación controla todos los aspectos de seleccionando el elemento y no requiere ninguna acción por el cuadro de lista. Devolver antes – 2, se puede establecer la selección o mover el símbolo de intercalación o ambos. Para establecer la selección, utilice [SetCurSel](#setcursel) o [función miembro SetSel](#setsel). Para mover el símbolo de intercalación, use [SetCaretIndex](#setcaretindex).  
  
 Un valor devuelto de – 1 indica que el cuadro de lista debe realizar la acción predeterminada en respuesta a la pulsación de tecla. La implementación predeterminada devuelve – 1.  
  
 Un valor devuelto de 0 o superior especifica el índice de un elemento en el cuadro de lista y se indica que el cuadro de lista debe realizar la acción predeterminada para la pulsación de tecla en el elemento especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CListBox nº&41;](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC CTRLTEST](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CButton (clase)](../../mfc/reference/cbutton-class.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [Clase CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Clase CStatic](../../mfc/reference/cstatic-class.md)

