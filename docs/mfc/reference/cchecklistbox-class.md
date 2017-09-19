---
title: Clase CCheckListBox | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CCheckListBox class
- checklist boxes
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2cce91e3b6cb6cdf6ec2f4564fcf5090a54c917f
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cchecklistbox-class"></a>Clase CCheckListBox
Proporciona la funcionalidad de un cuadro de lista de comprobación de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCheckListBox : public CListBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Construye un objeto `CCheckListBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCheckListBox::Create](#create)|Crea el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox` objeto.|  
|[CCheckListBox::DrawItem](#drawitem)|Llamado por el marco cuando un aspecto visual de un cuadro de lista dibujado por el propietario cambie.|  
|[CCheckListBox::Enable](#enable)|Habilita o deshabilita un elemento de cuadro de lista de comprobación.|  
|[CCheckListBox::GetCheck](#getcheck)|Obtiene el estado de la casilla de verificación de un elemento.|  
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtiene el estilo de casillas de verificación del control.|  
|[CCheckListBox::IsEnabled](#isenabled)|Determina si un elemento está habilitado.|  
|[CCheckListBox::MeasureItem](#measureitem)|Lo llama el marco de trabajo cuando se crea un cuadro de lista con un estilo de dibujo del propietario.|  
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Llamado por el marco para obtener la posición de la casilla de verificación de un elemento.|  
|[CCheckListBox::SetCheck](#setcheck)|Establece el estado de la casilla de verificación de un elemento.|  
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Establece el estilo de casillas de verificación del control.|  
  
## <a name="remarks"></a>Comentarios  
 Un cuadro de lista de comprobación"" muestra una lista de elementos, como los nombres de archivo. Cada elemento de la lista tiene una casilla de verificación situada junto a la que el usuario puede activar o desactivar.  
  
 `CCheckListBox`es sólo para los controles dibujados por el propietario porque la lista contiene más de las cadenas de texto. En su forma más sencilla, un cuadro de lista de comprobación contiene cadenas de texto y casillas de verificación, pero no es necesario tener texto en absoluto. Por ejemplo, podría tener una lista de mapas de bits pequeños con una casilla de verificación junto a cada elemento.  
  
 Para crear su propio cuadro de lista de comprobación, debe derivar su propia clase de `CCheckListBox`. Al derivar su propia clase, escribir un constructor para la clase derivada, a continuación, llame a **crear**.  
  
 Si desea controlar mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregar una función de miembro de entrada y el controlador de mensajes del mapa de mensajes a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes toma la forma siguiente:  
  
 **ON_**Notification **(**`id`, `memberFxn`**)**  
  
 donde `id` especifica el identificador de ventana secundaria del control que envía la notificación y `memberFxn` es el nombre de la función de miembro primario que ha escrito para controlar la notificación.  
  
 Prototipo de función del elemento primario es el siguiente:  
  
 **afx_msg** `void` `memberFxn` **( );**  
  
 Hay sólo una entrada de mapa de mensajes que pertenecen específicamente a **CCheckListBox** (consulte también las entradas del mapa de mensajes para [CListBox](../../mfc/reference/clistbox-class.md)):  
  
- **ON_CLBN_CHKCHANGE** el usuario ha cambiado el estado de la casilla de verificación de un elemento.  
  
 Si el cuadro de lista de comprobación es un cuadro de lista de comprobación predeterminado (una lista de cadenas con el tamaño predeterminado las casillas de verificación a la izquierda de cada uno), puede utilizar el valor predeterminado [CCheckListBox::DrawItem](#drawitem) para dibujar el cuadro de lista de comprobación. De lo contrario, es necesario reemplazar el [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) (función) y la [CCheckListBox::DrawItem](#drawitem) y [CCheckListBox::MeasureItem](#measureitem) funciones.  
  
 Puede crear un cuadro de lista de comprobación de una plantilla de cuadro de diálogo o directamente en el código.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox  
 Construye un objeto `CCheckListBox`.  
  
```  
CCheckListBox();
```  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CCheckListBox` objeto en dos pasos. Definir una clase derivada de `CCheckListBox`, a continuación, llame a **crear**, que inicializa el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[60 NVC_MFCControlLadenDialog](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]  
  
##  <a name="create"></a>CCheckListBox::Create  
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
 Especifica el estilo del cuadro de lista de comprobación. El estilo debe ser **LBS_HASSTRINGS** y **LBS_OWNERDRAWFIXED** (todos los elementos de la lista tienen el mismo alto) o **LBS_OWNERDRAWVARIABLE** (elementos de la lista son de distinto alto). Este estilo se puede combinar con otras [estilos de cuadro de lista](../../mfc/reference/list-box-styles.md) excepto **LBS_USETABSTOPS**.  
  
 `rect`  
 Especifica la posición y el tamaño del cuadro de lista de comprobación. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
 `pParentWnd`  
 Especifica la ventana primaria del cuadro de lista de comprobación (normalmente un `CDialog` objeto). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del cuadro de lista de comprobación  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CCheckListBox` objeto en dos pasos. En primer lugar, defina una clase derivada de **CcheckListBox** y, a continuación, llame a **crear**, que inicializa el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox`. Consulte [CCheckListBox::CCheckListBox](#cchecklistbox) para obtener un ejemplo.  
  
 Cuando **crear** se ejecuta, Windows envía la [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) mensajes para el control de cuadro de lista de comprobación.  
  
 Estos mensajes se controlan de manera predeterminada el [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funciones miembro en la `CWnd` clase base. Para extender el control de mensajes predeterminado, agregue un mapa de mensajes para el su clase derivada y las funciones de miembro de reemplazo anterior controlador de mensajes. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/window-styles.md) a un control de cuadro de lista de comprobación:  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
- **WS_VSCROLL** para agregar una barra de desplazamiento vertical  
  
- **WS_HSCROLL** para agregar una barra de desplazamiento horizontal  
  
- **WS_GROUP** para agrupar controles  
  
- **WS_TABSTOP** para permitir que este control de tabulación  
  
##  <a name="drawitem"></a>CCheckListBox::DrawItem  
 Llamado por el marco cuando un aspecto visual de los cambios del cuadro de lista de comprobación dibujado por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero largo a una [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura que contiene información sobre el tipo de dibujo necesario.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** y **itemState** los miembros de la `DRAWITEMSTRUCT` estructura definir la acción de dibujo que se realiza.  
  
 De forma predeterminada, esta función dibuja una lista de casilla de verificación de forma predeterminada, que consta de una lista de cadenas con una casilla de verificación tamaño predeterminado a la izquierda. El tamaño de lista de casilla de verificación es el especificado en [crear](#create).  
  
 Reemplace esta función miembro para implementar el dibujo de los cuadros de lista de comprobación dibujados por el propietario que no son los predeterminados, como cuadros de lista de comprobación con las listas que no son cadenas, con elementos de alto variable o con las casillas de verificación que no están a la izquierda. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para el contexto de presentación proporcionado en `lpDrawItemStruct` antes de la finalización de esta función miembro.  
  
 Si los elementos de cuadro de lista de comprobación no son la misma altura, la lista de comprobación cuadro Estilo (especificado en **crear**) debe ser **LBS_OWNERVARIABLE**, y se debe reemplazar el [MeasureItem](#measureitem) (función).  
  
##  <a name="enable"></a>CCheckListBox::Enable  
 Llame a esta función para habilitar o deshabilitar un elemento de cuadro de lista de comprobación.  
  
```  
void Enable(
    int nIndex,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del elemento de cuadro de lista de comprobación que se habilite.  
  
 `bEnabled`  
 Especifica si el elemento está habilitado o deshabilitado.  
  
##  <a name="getcheck"></a>CCheckListBox::GetCheck  
 Recupera el estado de la casilla de verificación especificada.  
  
```  
int GetCheck(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero de la casilla de verificación que se encuentra en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de la casilla de verificación especificada. La tabla siguiente enumeran los valores posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`BST_CHECKED`|La casilla de verificación está activada.|  
|`BST_UNCHECKED`|No se comprueba la casilla de verificación.|  
|`BST_INDETERMINATE`|El estado de la casilla es indeterminado.|  
  
##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle  
 Llame a esta función para obtener el estilo del cuadro de lista de comprobación.  
  
```  
UINT GetCheckStyle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estilo de casillas de verificación del control.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información sobre posibles estilos, consulte [SetCheckStyle](#setcheckstyle).  
  
##  <a name="isenabled"></a>CCheckListBox::IsEnabled  
 Llame a esta función para determinar si un elemento está habilitado.  
  
```  
BOOL IsEnabled(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el elemento está habilitado; en caso contrario, 0.  
  
##  <a name="measureitem"></a>CCheckListBox::MeasureItem  
 Lo llama el marco de trabajo cuando se crea un cuadro de lista de comprobación con un estilo no predeterminado.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMeasureItemStruct`  
 Un puntero largo a una [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de las dimensiones de elementos de cuadro de lista de comprobación. Si el cuadro de lista de comprobación se crea con el [LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md) estilo, el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. De lo contrario, este miembro se llama solo una vez.  
  
##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition  
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
 La posición predeterminada y el tamaño de la casilla de verificación de un elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Casilla de verificación de la posición y el tamaño de un elemento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada sólo devuelve la posición predeterminada y el tamaño de la casilla de verificación ( `rectCheckBox`). De forma predeterminada, una casilla de verificación está alineada en la esquina superior izquierda de un elemento y es el tamaño de la casilla estándar. Puede haber casos donde desee las casillas de verificación de la derecha, o desea una casilla de verificación de mayor o menor. En estos casos, anular `OnGetCheckPosition` para cambiar la posición de la casilla de verificación y tamaño dentro del elemento.  
  
##  <a name="setcheck"></a>CCheckListBox::SetCheck  
 Establece el estado de la casilla de verificación especificada.  
  
```  
void SetCheck(
    int nIndex,  
    int nCheck);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero de la casilla de verificación que se encuentra en el cuadro de lista.  
  
 `nCheck`  
 El estado del botón de la casilla de verificación especificada. Vea la sección Comentarios para los valores posibles.  
  
### <a name="remarks"></a>Comentarios  
 La tabla siguiente enumeran los valores posibles para el `nCheck` parámetro.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**BST_CHECKED**|Seleccione la casilla de verificación especificada.|  
|**BST_UNCHECKED**|Desactive la casilla de verificación especificada.|  
|**BST_INDETERMINATE**|Establecer el estado de la casilla de verificación especificada en indeterminado.<br /><br /> Este estado solo está disponible si el estilo de la casilla de verificación es `BS_AUTO3STATE` o `BS_3STATE`. Para obtener más información, consulte [estilos de botón](../../mfc/reference/button-styles.md).|  
  
##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle  
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
  
 Para obtener información acerca de estos estilos, consulte [estilos de botón](../../mfc/reference/button-styles.md).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo TSTCON de MFC](../../visual-cpp-samples.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)

