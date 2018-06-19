---
title: Clase CCheckListBox | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
dev_langs:
- C++
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4129da35eca5aecfb1e976361d1716d1cd78e906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358204"
---
# <a name="cchecklistbox-class"></a>Clase CCheckListBox
Proporciona la funcionalidad de un cuadro de lista de comprobación de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCheckListBox : public CListBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Construye un objeto `CCheckListBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCheckListBox::Create](#create)|Crea el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox` objeto.|  
|[CCheckListBox::DrawItem](#drawitem)|Lo llama el marco cuando un aspecto visual de un cuadro de lista dibujado por el propietario cambie.|  
|[CCheckListBox::Enable](#enable)|Habilita o deshabilita un elemento de cuadro de lista de comprobación.|  
|[CCheckListBox::GetCheck](#getcheck)|Obtiene el estado de la casilla de verificación de un elemento.|  
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtiene el estilo de casillas de verificación del control.|  
|[CCheckListBox::IsEnabled](#isenabled)|Determina si un elemento está habilitado.|  
|[CCheckListBox::MeasureItem](#measureitem)|Lo llama el marco cuando se crea un cuadro de lista con un estilo de dibujo del propietario.|  
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Lo llama el marco para obtener la posición de la casilla de verificación de un elemento.|  
|[CCheckListBox::SetCheck](#setcheck)|Establece el estado de la casilla de verificación de un elemento.|  
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Establece el estilo de casillas de verificación del control.|  
  
## <a name="remarks"></a>Comentarios  
 "Cuadro de lista de comprobación" muestra una lista de elementos, como los nombres de archivo. Cada elemento de la lista tiene una casilla de verificación situada junto a la que el usuario puede activar o desactivar.  
  
 `CCheckListBox` es solo para controles dibujados por el propietario porque la lista contiene más de las cadenas de texto. En su forma más sencilla, un cuadro de lista de comprobación contiene cadenas de texto y casillas, pero no es necesario para que el texto en absoluto. Por ejemplo, podría tener una lista de mapas de bits pequeños con una casilla de verificación junto a cada elemento.  
  
 Para crear su propio cuadro de lista de comprobación, debe derivar su propia clase de `CCheckListBox`. Al derivar su propia clase, escribir un constructor de la clase derivada, a continuación, llame a **crear**.  
  
 Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregar una función de miembro de entrada y el controlador de mensajes de mapa de mensajes para la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 **ON_** notificación **(**`id`, `memberFxn` **)**  
  
 donde `id` especifica el identificador de ventana de secundarios del control que envía la notificación y `memberFxn` es el nombre de la función de miembro primario haya terminado de escribir para controlar la notificación.  
  
 Prototipo de función del elemento primario es el siguiente:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Hay sólo una entrada de mapa de mensajes que se aplica específicamente a **CCheckListBox** (pero Vea también las entradas del mapa de mensajes para [CListBox](../../mfc/reference/clistbox-class.md)):  
  
- **ON_CLBN_CHKCHANGE** el usuario ha cambiado el estado de la casilla de verificación de un elemento.  
  
 Si el cuadro de lista de comprobación es un cuadro de lista de comprobación predeterminado (una lista de cadenas con las casillas de verificación de tamaño predeterminado a la izquierda de cada uno), puede usar el valor predeterminado [CCheckListBox::DrawItem](#drawitem) para dibujar el cuadro de lista de comprobación. En caso contrario, es necesario reemplazar el [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) función y la [CCheckListBox::DrawItem](#drawitem) y [CCheckListBox::MeasureItem](#measureitem) funciones.  
  
 Puede crear un cuadro de lista de comprobación de una plantilla de cuadro de diálogo o directamente en el código.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox  
 Construye un objeto `CCheckListBox`.  
  
```  
CCheckListBox();
```  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CCheckListBox` objeto en dos pasos. Definir una clase derivada de `CCheckListBox`, a continuación, llame a **crear**, que inicializa el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]  
  
##  <a name="create"></a>  CCheckListBox::Create  
 Crea el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del cuadro de lista de comprobación. El estilo debe ser **LBS_HASSTRINGS** y **LBS_OWNERDRAWFIXED** (todos los elementos de la lista tienen el mismo alto) o **LBS_OWNERDRAWVARIABLE** (elementos de la lista están de diferentes alturas). Este estilo se puede combinar con otras [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) excepto **LBS_USETABSTOPS**.  
  
 `rect`  
 Especifica la posición y el tamaño de un cuadro de lista de comprobación. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
 `pParentWnd`  
 Especifica la lista de comprobación ventana del cuadro primario (normalmente un `CDialog` objeto). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del cuadro de lista de comprobación  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CCheckListBox` objeto en dos pasos. En primer lugar, defina una clase derivada de **CcheckListBox** y, a continuación, llame a **crear**, que inicializa el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox`. Vea [CCheckListBox::CCheckListBox](#cchecklistbox) para obtener un ejemplo.  
  
 Cuando **crear** se ejecuta, Windows envía la [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) mensajes para el control de cuadro de lista de comprobación.  
  
 Estos mensajes se controlan de manera predeterminada el [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funciones miembro en la `CWnd` clase base. Para extender el control de mensajes de forma predeterminada, agregue un mapa de mensajes para el su clase derivada y las funciones de miembro de reemplazo anterior controlador de mensajes. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de cuadro de lista de comprobación:  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
- **WS_VSCROLL** para agregar una barra de desplazamiento vertical  
  
- **WS_HSCROLL** para agregar una barra de desplazamiento horizontal  
  
- **WS_GROUP** a controles de grupo  
  
- **WS_TABSTOP** para permitir a este control de tabulación  
  
##  <a name="drawitem"></a>  CCheckListBox::DrawItem  
 Lo llama el marco cuando un aspecto visual de cambia de un cuadro de lista de comprobación dibujado por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero largo a una [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura que contiene información sobre el tipo de dibujo necesaria.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** y **itemState** los miembros de la `DRAWITEMSTRUCT` estructura definir la acción de dibujo que va a realizarse.  
  
 De forma predeterminada, esta función dibuja una lista de casilla de verificación de forma predeterminada, que consta de una lista de cadenas con una casilla de verificación tamaño predeterminado a la izquierda. El tamaño de la lista de casilla es el especificado en [crear](#create).  
  
 Reemplace esta función miembro para implementar operaciones de dibujo de los cuadros de lista de comprobación de dibujado por el propietario que no son los predeterminados, como cuadros de lista de comprobación con las listas que no son cadenas, con elementos de alto variable o con las casillas de verificación que no están en la parte izquierda. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en `lpDrawItemStruct` antes de la finalización de esta función miembro.  
  
 Si los elementos de cuadro de lista de comprobación no son la misma altura, la lista de comprobación cuadro Estilo (especificado en **crear**) debe ser **LBS_OWNERVARIABLE**, y es necesario reemplazar el [MeasureItem](#measureitem) función.  
  
##  <a name="enable"></a>  CCheckListBox::Enable  
 Llame a esta función para habilitar o deshabilitar un elemento de cuadro de lista de comprobación.  
  
```  
void Enable(
    int nIndex,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del elemento de cuadro de lista de comprobación para habilitarse.  
  
 `bEnabled`  
 Especifica si el elemento está habilitado o deshabilitado.  
  
##  <a name="getcheck"></a>  CCheckListBox::GetCheck  
 Recupera el estado de la casilla de verificación especificada.  
  
```  
int GetCheck(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero de una casilla de verificación que se encuentra en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de la casilla de verificación especificada. En la tabla siguiente se enumera los valores posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`BST_CHECKED`|La casilla de verificación está activada.|  
|`BST_UNCHECKED`|No se comprueba la casilla de verificación.|  
|`BST_INDETERMINATE`|El estado de la casilla de verificación es indeterminado.|  
  
##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle  
 Llame a esta función para obtener el estilo del cuadro de lista de comprobación.  
  
```  
UINT GetCheckStyle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estilo de casillas de verificación del control.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información sobre posibles estilos, consulte [SetCheckStyle](#setcheckstyle).  
  
##  <a name="isenabled"></a>  CCheckListBox::IsEnabled  
 Llame a esta función para determinar si un elemento está habilitado.  
  
```  
BOOL IsEnabled(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento está habilitado; en caso contrario es 0.  
  
##  <a name="measureitem"></a>  CCheckListBox::MeasureItem  
 Lo llama el marco cuando se crea un cuadro de lista de comprobación con un estilo no predeterminado.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMeasureItemStruct`  
 Un puntero largo a una [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de las dimensiones de elementos del cuadro de lista de comprobación. Si el cuadro de lista de comprobación se crea con el [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. En caso contrario, este miembro se llama solo una vez.  
  
##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition  
 El marco de trabajo llama a esta función para obtener la posición y el tamaño de la casilla de verificación de un elemento.  
  
```  
virtual CRect OnGetCheckPosition(
    CRect rectItem,  
    CRect rectCheckBox);
```  
  
### <a name="parameters"></a>Parámetros  
 *rectItem*  
 La posición y el tamaño del elemento de lista.  
  
 `rectCheckBox`  
 Casilla de verificación de la posición predeterminada y el tamaño de un elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Casilla de verificación de la posición y el tamaño de un elemento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada devuelve solo la posición predeterminada y el tamaño de la casilla de verificación ( `rectCheckBox`). De forma predeterminada, una casilla de verificación está alineada en la esquina superior izquierda de un elemento y es el tamaño de la casilla estándar. Puede haber casos en que desea que las casillas de verificación de la derecha, o desea una casilla de verificación mayor o menor. En estos casos, reemplace el método `OnGetCheckPosition` para cambiar la posición de la casilla de verificación y tamaño dentro del elemento.  
  
##  <a name="setcheck"></a>  CCheckListBox::SetCheck  
 Establece el estado de la casilla de verificación especificada.  
  
```  
void SetCheck(
    int nIndex,  
    int nCheck);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero de una casilla de verificación que se encuentra en el cuadro de lista.  
  
 `nCheck`  
 El estado de los botones de la casilla de verificación especificada. Vea la sección Comentarios para los valores posibles.  
  
### <a name="remarks"></a>Comentarios  
 En la tabla siguiente se enumera los valores posibles para el `nCheck` parámetro.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**BST_CHECKED**|Seleccione la casilla de verificación especificada.|  
|**BST_UNCHECKED**|Desactive la casilla de verificación especificada.|  
|**BST_INDETERMINATE**|Establecer el estado de la casilla de verificación especificada en indeterminado.<br /><br /> Este estado solo está disponible si el estilo de la casilla de verificación es `BS_AUTO3STATE` o `BS_3STATE`. Para obtener más información, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
  
##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle  
 Llame a esta función para establecer el estilo de casillas de verificación en el cuadro de lista de comprobación.  
  
```  
void SetCheckStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStyle`  
 Determina el estilo de casillas de verificación en el cuadro de lista de comprobación.  
  
### <a name="remarks"></a>Comentarios  
 Los estilos válidos son:  
  
- **BS_CHECKBOX**  
  
- **BS_AUTOCHECKBOX**  
  
- **BS_AUTO3STATE**  
  
- **BS_3STATE**  
  
 Para obtener información sobre estos estilos, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC TSTCON](../../visual-cpp-samples.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)
