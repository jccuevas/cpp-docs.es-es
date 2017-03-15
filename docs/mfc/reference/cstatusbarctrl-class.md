---
title: CStatusBarCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CStatusBarCtrl
- CStatusBarCtrl class
- status bar controls
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: 20
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
ms.openlocfilehash: 619fb88b96f60ab2dc0911cb8ea0b66574ea4287
ms.lasthandoff: 02/24/2017

---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl (clase)
Proporciona la funcionalidad del control de barra de estado común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Construye un objeto `CStatusBarCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|Crea un control de barra de estado y lo adjunta a un `CStatusBarCtrl` objeto.|  
|[CStatusBarCtrl::CreateEx](#createex)|Crea un control de barra de estado con los estilos extendidos de Windows especificados y lo adjunta a un `CStatusBarCtrl` objeto.|  
|[CStatusBarCtrl::DrawItem](#drawitem)|Se llama cuando la apariencia de una barra de estado dibujados por el propietario cambia control.|  
|[CStatusBarCtrl::GetBorders](#getborders)|Recupera el ancho actual de los bordes verticales y horizontales de un control de barra de estado.|  
|[CStatusBarCtrl::GetIcon](#geticon)|Recupera el icono de un elemento (también conocido como un panel) en el control de barra de estado actual.|  
|[CStatusBarCtrl::GetParts](#getparts)|Recupera un recuento de los elementos de un control de barra de estado.|  
|[CStatusBarCtrl::GetRect](#getrect)|Recupera el rectángulo delimitador de un elemento en un control de barra de estado.|  
|[CStatusBarCtrl::GetText](#gettext)|Recupera el texto de la parte determinada de un control de barra de estado.|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Recuperar la longitud, en caracteres, del texto de la parte determinada de un control de barra de estado.|  
|[CStatusBarCtrl:: GetTipText](#gettiptext)|Recupera el texto de información sobre herramientas para un panel en una barra de estado.|  
|[CStatusBarCtrl::IsSimple](#issimple)|Comprueba que un control de la ventana de estado para determinar si está en modo simple.|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo de una barra de estado.|  
|[CStatusBarCtrl::SetIcon](#seticon)|Establece el icono de un panel en una barra de estado.|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Establece el alto mínimo de un estado de la barra del área de dibujo del control.|  
|[CStatusBarCtrl::SetParts](#setparts)|Establece el número de elementos en un control y la coordenada del borde derecho de cada parte de la barra de estado.|  
|[CStatusBarCtrl::SetSimple](#setsimple)|Especifica si un control de barra de estado muestra el texto simple o todos los elementos de control establecidos por una llamada anterior a `SetParts`.|  
|[CStatusBarCtrl::SetText](#settext)|Establece el texto en un elemento determinado de un control de barra de estado.|  
|[CStatusBarCtrl:: SetTipText](#settiptext)|Establece el texto de información sobre herramientas para un panel en una barra de estado.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control de barra de estado" es una ventana horizontal, que habitualmente se muestra en la parte inferior de una ventana principal, en el que una aplicación puede mostrar varios tipos de información de estado. El control de barra de estado se puede dividir en partes para mostrar más de un tipo de información.  
  
 Este control (y por tanto la `CStatusBarCtrl` clase) está disponible sólo para los programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Para obtener más información sobre el uso de `CStatusBarCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [utilizando CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="a-namecreatea--cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl::Create  
 Crea un control de barra de estado y lo adjunta a un `CStatusBarCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de barra de estado. Aplicar cualquier combinación de estilos de control que aparece en la barra de estado [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Este parámetro debe incluir la **WS_CHILD** estilo. También debe incluir el **WS_VISIBLE** estilo.  
  
 `rect`  
 Especifica el tamaño y la posición del control de barra de estado. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.  
  
 `pParentWnd`  
 Especifica el estado de la barra de la ventana primaria del control, normalmente un `CDialog`. No debe ser **NULL.**  
  
 `nID`  
 Especifica el identificador. del control de barra de estado  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CStatusBarCtrl` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de barra de estado y lo adjunta a la `CStatusBarCtrl` objeto.  
  
 Es la posición predeterminada de una ventana de estado en la parte inferior de la ventana primaria, pero puede especificar el `CCS_TOP` estilo para que aparezca en la parte superior del área de cliente de la ventana primaria. Puede especificar el **SBARS_SIZEGRIP** estilo para incluir un control de tamaño en el extremo derecho de la ventana de estado. Combinar el `CCS_TOP` y **SBARS_SIZEGRIP** estilos no se recomienda, porque el control de tamaño resultante no es funcional incluso aunque el sistema lo dibuja en la ventana de estado.  
  
 Para crear una barra de estado con los estilos de ventana extendidos, llame a [CStatusBarCtrl::CreateEx](#createex) en lugar de **crear**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CStatusBarCtrl](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="a-namecreateexa--cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CStatusBarCtrl` objeto.  
  
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
 Especifica el estilo del control de barra de estado. Aplicar cualquier combinación de estilos de control que aparece en la barra de estado [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Este parámetro debe incluir la **WS_CHILD** estilo. También debe incluir el **WS_VISIBLE** estilo.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente `pParentWnd`.  
  
 `pParentWnd`  
 Puntero a la ventana que es principal el control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="a-namecstatusbarctrla--cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl  
 Construye un objeto `CStatusBarCtrl`.  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="a-namedrawitema--cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::DrawItem  
 Llamado por el marco de trabajo cuando la apariencia de una barra de estado dibujados por el propietario cambia control.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero largo a una [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) estructura que contiene información sobre el tipo de dibujo necesario.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza.  
  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar un dibujados por el propietario del dibujo `CStatusBarCtrl` objeto.  
  
 La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para el contexto de presentación proporcionado en `lpDrawItemStruct` antes de este miembro de función termina.  
  
##  <a name="a-namegetbordersa--cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarCtrl::GetBorders  
 Recupera el ancho actual del control de barra de estado de los bordes horizontales y verticales y el espacio entre los rectángulos.  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pBorders*  
 Dirección de una matriz de enteros con tres elementos. El primer elemento recibe el ancho del borde horizontal, la segunda recibe el ancho del borde vertical y el tercero recibe el ancho del borde entre rectángulos.  
  
 *nHorz*  
 Referencia a un entero que recibe el ancho del borde horizontal.  
  
 *nvertir*  
 Referencia a un entero que recibe el ancho del borde vertical.  
  
 *nSpacing*  
 Referencia a un entero que recibe el ancho del borde entre rectángulos.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Estos límites determinan el espaciado entre el borde exterior del control y los rectángulos dentro del control que contienen texto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&#2;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="a-namegeticona--cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarCtrl::GetIcon  
 Recupera el icono de un elemento (también conocido como un panel) en el control de barra de estado actual.  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iPart`|Índice de base cero del elemento que contiene el icono que se va a recuperar. Si este parámetro es -1, se supone que la barra de estado es una barra de estado de modo sencillo.|  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del icono si el método correcto; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Un control de barra de estado se compone de una fila de paneles de salida de texto, que también se conoce como partes. Para obtener más información acerca de la barra de estado, consulte [implementación de la barra de estado en MFC](../../mfc/status-bar-implementation-in-mfc.md) y [establecer el modo de un objeto CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_statusBar`, que se utiliza para tener acceso al control de barra de estado actual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[1 NVC_MFC_CStatusBarCtrl_s1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se copia un icono en dos paneles de control de barra de estado actual. En una sección anterior del ejemplo de código se crea un control de barra de estado con tres paneles y, a continuación, se agrega un icono al primer panel. Este ejemplo recupera el icono de la primera sección y, a continuación, agrega al panel de segundo y tercero.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s&#1;2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="a-namegetpartsa--cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarCtrl::GetParts  
 Recupera un recuento de los elementos de un control de barra de estado.  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nParts`  
 Número de elementos para los que se va a recuperar coordenadas. Si este parámetro es mayor que el número de elementos en el control, el mensaje recupera coordenadas para que sólo los elementos existentes.  
  
 *pParts*  
 Dirección de una matriz de enteros con el mismo número de elementos como el número de elementos especificado por `nParts`. Cada elemento de la matriz recibe las coordenadas de cliente del borde derecho de la parte correspondiente. Si un elemento está establecido en – 1, la posición del borde derecho para esa parte amplía hasta el borde derecho de la barra de estado.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el control si se realiza correctamente, o cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro también recupera la coordenada del borde derecho del número especificado de elementos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&3;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="a-namegetrecta--cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarCtrl::GetRect  
 Recupera el rectángulo delimitador de un elemento en un control de barra de estado.  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nPane`  
 Índice de base cero del elemento cuyo rectángulo delimitador es va a recuperar.  
  
 `lpRect`  
 Dirección de un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe el rectángulo delimitador.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl Nº&4;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="a-namegettexta--cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarCtrl::GetText  
 Recupera el texto de la parte determinada de un control de barra de estado.  
  
```  
CString GetText(
    int nPane,  
    int* pType = NULL) const;  
  
int GetText(
    LPCTSTR lpszText,  
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Dirección del búfer que recibe el texto. Este parámetro es una cadena terminada en null.  
  
 `nPane`  
 Índice de base cero del elemento en el que se va a recuperar el texto.  
  
 `pType`  
 Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:  
  
- **0** el texto se dibuja con un borde que aparezca menor que el plano de la barra de estado.  
  
- `SBT_NOBORDERS`El texto se dibuja sin bordes.  
  
- `SBT_POPOUT`El texto se dibuja con un borde que aparezca más arriba que el plano de la barra de estado.  
  
- `SBT_OWNERDRAW`Si el texto tiene el `SBT_OWNERDRAW` tipo, de dibujo `pType` recibe este mensaje y devuelve el valor de 32 bits asociado con el texto en lugar del tipo de operación y la longitud.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud, en caracteres, del texto o un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el texto actual.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&#5;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="a-namegettextlengtha--cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarCtrl::GetTextLength  
 Recupera la longitud, en caracteres, del texto de la parte determinada de un control de barra de estado.  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nPane`  
 Índice de base cero del elemento en el que se va a recuperar el texto.  
  
 `pType`  
 Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:  
  
- **0** el texto se dibuja con un borde que aparezca menor que el plano de la barra de estado.  
  
- `SBT_NOBORDERS`El texto se dibuja sin bordes.  
  
- `SBT_OWNERDRAW`El texto se dibuja en la ventana principal.  
  
- `SBT_POPOUT`El texto se dibuja con un borde que aparezca más arriba que el plano de la barra de estado.  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud, en caracteres, del texto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl Nº&6;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="a-namegettiptexta--cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStatusBarCtrl:: GetTipText  
 Recupera el texto de información sobre herramientas para un panel en una barra de estado.  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nPane`  
 Índice de base cero del panel de barra de estado para recibir el texto de información sobre herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto que se usará en la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&#7;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="a-nameissimplea--cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarCtrl::IsSimple  
 Comprueba que un control de la ventana de estado para determinar si está en modo simple.  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el control de la ventana de estado se encuentra en modo simple; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetbkcolora--cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor  
 Establece el color de fondo de una barra de estado.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parámetros  
 `cr`  
 **COLORREF** valor que especifica el nuevo color de fondo. Especifique la `CLR_DEFAULT` valor para hacer que la barra de estado utilizar su color de fondo predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que representa el color de fondo predeterminado anterior.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl Nº&8;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="a-nameseticona--cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarCtrl::SetIcon  
 Establece el icono de un panel en una barra de estado.  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPane`  
 Índice de base cero del panel que va a recibir el icono. Si este parámetro es -1, se supone que la barra de estado es una barra de estado simple.  
  
 `hIcon`  
 Controlar el icono de establecerse. Si este valor es **NULL**, se quita el icono de la parte.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CStatusBarCtrl::SetBkColor](#setbkcolor).  
  
##  <a name="a-namesetminheighta--cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarCtrl::SetMinHeight  
 Establece el alto mínimo de un estado de la barra del área de dibujo del control.  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMin`  
 Alto mínimo, en píxeles, del control.  
  
### <a name="remarks"></a>Comentarios  
 El alto mínimo es la suma de `nMin` y dos veces el ancho, en píxeles, del borde vertical del control de barra de estado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&#9;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="a-namesetpartsa--cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarCtrl::SetParts  
 Establece el número de elementos en un control y la coordenada del borde derecho de cada parte de la barra de estado.  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>Parámetros  
 `nParts`  
 Número de elementos para establecer. El número de partes no puede ser mayor de 255.  
  
 *pWidths*  
 Dirección de una matriz de enteros con el mismo número de elementos como elementos especificados por `nParts`. Cada elemento de la matriz especifica la posición del borde derecho de la parte correspondiente, en coordenadas de cliente. Si un elemento es – 1, la posición del borde derecho para esa parte se amplía hasta el borde derecho del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&#10;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="a-namesetsimplea--cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarCtrl::SetSimple  
 Especifica si un control de barra de estado muestra el texto simple o todos los elementos de control establecidos por una llamada anterior a [SetParts](#setparts).  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSimple`  
 Indicador de tipo de presentación. Si este parámetro es `TRUE`, el control muestra texto simple; si es `FALSE`, muestra varias partes.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación cambia el control de barra de estado de no simple a simple, o viceversa, el sistema actualiza inmediatamente el control.  
  
##  <a name="a-namesettexta--cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarCtrl::SetText  
 Establece el texto en un elemento determinado de un control de barra de estado.  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Dirección de una cadena terminada en null que especifica el texto que se debe establecer. Si `nType` es `SBT_OWNERDRAW`, `lpszText` representa 32 bits de datos.  
  
 `nPane`  
 El índice de base cero del elemento que se debe establecer. Si este valor es 255, se asume que el control de barra de estado es un control simple que solo contiene un elemento.  
  
 `nType`  
 Tipo de operación de dibujo. Consulte [mensaje SB_SETTEXT](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx) para obtener una lista de valores posibles.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El mensaje invalida la parte del control que ha cambiado y se muestra el texto nuevo cuando el control siguiente recibe el mensaje `WM_PAINT`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&#11;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="a-namesettiptexta--cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStatusBarCtrl:: SetTipText  
 Establece el texto de información sobre herramientas para un panel en una barra de estado.  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPane`  
 Índice de base cero del panel de barra de estado para recibir el texto de información sobre herramientas.  
  
 *pszTipText*  
 Un puntero a una cadena que contiene el texto de información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatusBarCtrl&#12;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl (clase)](../../mfc/reference/ctoolbarctrl-class.md)

