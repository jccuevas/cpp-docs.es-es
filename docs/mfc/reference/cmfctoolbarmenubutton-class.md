---
title: Clase CMFCToolBarMenuButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CompareWith
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CopyFrom
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateFromMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::EnableQuickCustomize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetCommands
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetImageRect
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPaletteRows
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HasButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HaveHotBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsClickedOnMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsDroppedDown
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsEmptyMenuAllowed
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsExclusive
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsQuickMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsTearOffMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnAfterCreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnBeforeDrag
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCalculateSize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCancelMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnChangeParentWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClick
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClickMenuItem
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnContextHelp
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDraw
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDrawOnCustomizeList
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OpenPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::ResetImageToDefault
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SaveBarState
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::Serialize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetACCData
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuOnly
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMessageWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetRadio
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetTearOff
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::DrawDocumentIcon
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarMenuButton class
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
caps.latest.revision: 31
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a06fd323862c6869463b4db0977816b5707c3e18
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarmenubutton-class"></a>Clase CMFCToolBarMenuButton
Un botón de la barra de herramientas que contiene un menú emergente.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](#cmfctoolbarmenubutton)|Construye un objeto `CMFCToolBarMenuButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CompareWith](#comparewith)|Compara esta instancia con los `CMFCToolBarButton` objeto. (Invalida [CMFCToolBarButton::CompareWith](../../mfc/reference/cmfctoolbarbutton-class.md#comparewith).)|  
|[CMFCToolBarMenuButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de barra de herramientas a la actual. (Invalida [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|[CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu)|Inicializa el menú de la barra de herramientas desde un identificador de menú de Windows.|  
|[CMFCToolBarMenuButton::CreateMenu](#createmenu)|Crea un menú de Windows que se compone de los comandos en el menú de la barra de herramientas. Devuelve un identificador para el menú de Windows.|  
|[CMFCToolBarMenuButton::CreatePopupMenu](#createpopupmenu)|Crea un objeto de menú emergente ( [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md)) para mostrar el menú de la barra de herramientas.|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](#enablequickcustomize)||  
|[CMFCToolBarMenuButton::GetCommands](#getcommands)|Proporciona acceso de sólo lectura a la lista de comandos en el menú de la barra de herramientas.|  
|[CMFCToolBarMenuButton::GetImageRect](#getimagerect)|Recupera el rectángulo delimitador de la imagen del botón.|  
|[CMFCToolBarMenuButton::GetPaletteRows](#getpaletterows)|Devuelve el número de filas en el menú emergente cuando el menú está en modo de paleta.|  
|[CMFCToolBarMenuButton::GetPopupMenu](#getpopupmenu)|Devuelve un puntero al objeto de menú emergente que está asociado con el botón.|  
|[CMFCToolBarMenuButton::HasButton](#hasbutton)||  
|[CMFCToolBarMenuButton::HaveHotBorder](#havehotborder)|Determina si un borde del botón se muestra cuando un usuario selecciona el botón. (Invalida [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarMenuButton::IsBorder](#isborder)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](#isclickedonmenu)||  
|[CMFCToolBarMenuButton::IsDroppedDown](#isdroppeddown)|Determina si se muestra el menú emergente.|  
|[CMFCToolBarMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Llamado por el marco de trabajo para determinar si un usuario puede abrir un submenú del elemento de menú seleccionado.|  
|[CMFCToolBarMenuButton::IsExclusive](#isexclusive)|Determina si el botón está en modo exclusivo, es decir, si el menú emergente permanece abierto incluso cuando el usuario mueve el puntero sobre otra barra de herramientas o botón.|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](#ismenupalettemode)|Determina si el menú emergente está en modo de paleta.|  
|[CMFCToolBarMenuButton::IsQuickMode](#isquickmode)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](#istearoffmenu)|Determina si el menú emergente tiene una barra desplazable.|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](#onaftercreatepopupmenu)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](#onbeforedrag)|Especifica si se puede arrastrar el botón. (Invalida [CMFCToolBarButton::OnBeforeDrag](../../mfc/reference/cmfctoolbarbutton-class.md#onbeforedrag).)|  
|[CMFCToolBarMenuButton::OnCalculateSize](#oncalculatesize)|Llamado por el marco para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Invalida [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarMenuButton::OnCancelMode](#oncancelmode)|Llamado por el marco de trabajo para controlar la [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) mensaje. (Invalida [CMFCToolBarButton::OnCancelMode](../../mfc/reference/cmfctoolbarbutton-class.md#oncancelmode).)|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Llamado por el marco de trabajo cuando el botón se inserta en una barra de herramientas. (Invalida [CMFCToolBarButton::OnChangeParentWnd](cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarMenuButton::OnClick](#onclick)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón del mouse. (Invalida [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarMenuButton::OnClickMenuItem](#onclickmenuitem)|Lo llama el marco de trabajo cuando el usuario selecciona un elemento en el menú emergente.|  
|[CMFCToolBarMenuButton::OnContextHelp](#oncontexthelp)|Llamado por el marco cuando la barra de herramientas primario controla un `WM_HELPHITTEST` mensaje. (Invalida [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCToolBarMenuButton::OnDraw](#ondraw)|Llamado por el marco para dibujar el botón con los estilos especificados y las opciones. (Invalida [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Llamado por el marco para dibujar el botón en el **comandos** panel de la **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarMenuButton::OpenPopupMenu](#openpopupmenu)|Lo llama el marco de trabajo cuando el usuario abre el menú emergente.|  
|[CMFCToolBarMenuButton::ResetImageToDefault](#resetimagetodefault)|Establece el valor predeterminado de la imagen que está asociada con el botón. (Invalida [CMFCToolBarButton::ResetImageToDefault](../../mfc/reference/cmfctoolbarbutton-class.md#resetimagetodefault).)|  
|[CMFCToolBarMenuButton::SaveBarState](#savebarstate)|Guarda el estado del botón de barra de herramientas. (Invalida [CMFCToolBarButton::SaveBarState](../../mfc/reference/cmfctoolbarbutton-class.md#savebarstate).)|  
|[CMFCToolBarMenuButton::Serialize](#serialize)|Lee este objeto desde un archivo o lo escribe en un archivo. (Invalida [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCToolBarMenuButton::SetACCData](#setaccdata)|Rellena proporcionado `CAccessibilityData` objeto con datos de accesibilidad en el botón de barra de herramientas. (Invalida [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|  
|[CMFCToolBarMenuButton::SetMenuOnly](#setmenuonly)|Especifica si se puede agregar el botón a una barra de herramientas.|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)|Especifica si el menú emergente está en modo de paleta.|  
|[CMFCToolBarMenuButton::SetMessageWnd](#setmessagewnd)||  
|[CMFCToolBarMenuButton::SetRadio](#setradio)|Fuerza el botón de menú de la barra de herramientas para mostrar un icono que indica que está seleccionado.|  
|[CMFCToolBarMenuButton::SetTearOff](#settearoff)|Especifica un desplazable Id. de la barra del menú emergente.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](#drawdocumenticon)|Dibuja un icono en el botón de menú.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw](#m_balwayscallownerdraw)|Si `TRUE`, el marco llama siempre [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) cuando se dibuja un botón.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CMFCToolBarMenuButton` pueden aparecer como un menú, un elemento de menú que tiene un submenú, un botón que ejecuta un comando o muestra un menú o un botón que muestra sólo un menú. Determinar el comportamiento y la apariencia del botón de menú mediante la especificación de parámetros como la imagen, texto, identificador de menú y el identificador asociado con el botón en el constructor del comando `CMFCToolbarMenuButton::CMFCToolbarMenuButton`.  
  
 Una clase personalizada derivada de la `CMFCToolbarMenuButton` clase debe usar el [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro. El [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) macro genera un error cuando se cierra la aplicación.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un `CMFCToolBarMenuButton` objeto. El código muestra cómo especificar que el menú desplegable está en modo de paleta y especifique el identificador de la barra desplazable que se crea cuando el usuario arrastra el botón de menú de una barra de menús. Este fragmento de código forma parte de la [ejemplo de panel de palabras](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad&#10;](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarmenubutton.h  
  
##  <a name="cmfctoolbarmenubutton"></a>CMFCToolBarMenuButton::CMFCToolBarMenuButton  
 Construye un objeto `CMFCToolBarMenuButton`.  
  
```  
CMFCToolBarMenuButton();
CMFCToolBarMenuButton(const CMFCToolBarMenuButton& src);

CMFCToolBarMenuButton(
    UINT uiID,  
    HMENU hMenu,  
    int iImage,  
    LPCTSTR lpszText=NULL,  
    BOOL bUserButton=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Existente `CMFCToolBarMenuButton` el objeto que se copiará en este `CMFCToolBarMenuButton` objeto.  
  
 [in] `uiID`  
 El identificador del comando que se ejecutará cuando un usuario hace clic en el botón; o ( `UINT`) -1 para un botón de menú que no se ejecuta directamente un comando.  
  
 [in] `hMenu`  
 Un identificador de un menú; o `NULL` si el botón no tiene un menú.  
  
 [in] `iImage`  
 Índice de la imagen del botón; o -1 si este botón no tiene un icono o utiliza el icono para el comando especificado por `uiID`. El índice es el mismo para cada `CMFCToolBarImages` objeto de la aplicación.  
  
 [in] `lpszText`  
 El texto del botón de menú de barra de herramientas.  
  
 [in] `bUserButton`  
 `TRUE`Si se muestra una imagen definida por el usuario; `FALSE` si se muestra una imagen predefinida asociada con el comando especificado por `uiID`.  
  
### <a name="remarks"></a>Comentarios  
 Si `uiID` es válido Id. de comando, el botón realiza ese comando cuando el usuario hace clic en él. Si `hMenu` es un identificador válido de menú, el botón proporciona un menú desplegable cuando aparece en una barra de herramientas o a un submenú cuando aparece en un menú. Si ambos `uiID` y `hMenu` son válidos, el botón es un botón de división con una parte que llevará a cabo el comando cuando el usuario hace clic en él y una parte con una flecha hacia abajo que se despliegue un menú cuando el usuario hace clic en él. Sin embargo, si `hMenu` es válido, un usuario no podrá hacer clic en el botón para ejecutar un comando cuando el botón se inserta en un menú.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCToolBarMenuButton` clase. Este fragmento de código forma parte de la [ejemplo de panel de palabras](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad&#9;](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_2.cpp)]  
  
##  <a name="comparewith"></a>CMFCToolBarMenuButton::CompareWith  

  
```  
virtual BOOL CompareWith(const CMFCToolBarButton& other) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `other`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="copyfrom"></a>CMFCToolBarMenuButton::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="createfrommenu"></a>CMFCToolBarMenuButton::CreateFromMenu  
 Inicializa el menú de la barra de herramientas desde un identificador de menú de Windows.  
  
```  
virtual void CreateFromMenu(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hMenu`  
 Identificador de un menú.  
  
### <a name="remarks"></a>Comentarios  
 Un botón de menú de la barra de herramientas puede mostrar un submenú de la lista desplegable.  
  
 El marco de trabajo llama a este método para inicializar los comandos en el submenú de un menú.  
  
##  <a name="createmenu"></a>CMFCToolBarMenuButton::CreateMenu  
 Crea un menú que se compone de los comandos en el menú de la barra de herramientas. Devuelve un identificador para el menú.  
  
```  
virtual HMENU CreateMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un controlador del menú si correcto. `NULL`Si la lista de comandos asociados con el botón de menú de la barra de herramientas está vacía.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar este método en una clase derivada para personalizar la forma en que se genera el menú.  
  
##  <a name="createpopupmenu"></a>CMFCToolBarMenuButton::CreatePopupMenu  
 Crea un `CMFCPopupMenu` objeto para mostrar el menú de la barra de herramientas.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CMFCPopupMenu` objeto que muestra el menú desplegable asociado con el botón de menú de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método es llamado por el marco para preparar la presentación del menú desplegable asociado con el botón.  
  
 La implementación predeterminada simplemente construye y devuelve un nuevo `CMFCPopupMenu` objeto. Invalide este método si desea utilizar un tipo derivado de [CMFCPopupMenu clase](cmfcpopupmenu-class.md) o para realizar operaciones de inicialización adicional.  
  
##  <a name="drawdocumenticon"></a>CMFCToolBarMenuButton::DrawDocumentIcon  
 Dibuja un icono de documento en el botón de menú.  
  
```  
void DrawDocumentIcon(
    CDC* pDC,  
    const CRect& rectImage,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo.  
  
 [in] `rectImage`  
 Coordenadas de la imagen del rectángulo delimitador.  
  
 [in] `hIcon`  
 Identificador del icono.  
  
### <a name="remarks"></a>Comentarios  
 Este método toma un icono de documento y dibuja en el botón de menú, centrado en el área especificada por `rectImage`.  
  
##  <a name="enablequickcustomize"></a>CMFCToolBarMenuButton::EnableQuickCustomize  

  
```  
void EnableQuickCustomize();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hasbutton"></a>CMFCToolBarMenuButton::HasButton  

  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="havehotborder"></a>CMFCToolBarMenuButton::HaveHotBorder  

  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isborder"></a>CMFCToolBarMenuButton::IsBorder  

  
```  
virtual BOOL IsBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isclickedonmenu"></a>CMFCToolBarMenuButton::IsClickedOnMenu  

  
```  
BOOL IsClickedOnMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isquickmode"></a>CMFCToolBarMenuButton::IsQuickMode  

  
```  
BOOL IsQuickMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcommands"></a>CMFCToolBarMenuButton::GetCommands  
 Proporciona acceso de sólo lectura a la lista de comandos en el menú de la barra de herramientas.  
  
```  
const CObList& GetCommands() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Const hacen referencia a un [clase CObList](../../mfc/reference/coblist-class.md) , que contiene una colección de [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objetos.  
  
### <a name="remarks"></a>Comentarios  
 Un botón de menú de la barra de herramientas puede mostrar un submenú. Puede proporcionar la lista de comandos en el submenú en el constructor o en [CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu) como un identificador de un menú ( `HMENU`). El menú se convierte en una lista de objetos que se derivan de [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) y se almacenan en el interno `CObList` objeto. Puede tener acceso a esta lista mediante una llamada a este método.  
  
##  <a name="getimagerect"></a>CMFCToolBarMenuButton::GetImageRect  
 Recupera el rectángulo delimitador de la imagen del botón.  
  
```  
void GetImageRect(CRect& rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectImage`  
 Una referencia a un `CRect` objeto que recibe las coordenadas de la imagen del rectángulo delimitador.  
  
##  <a name="getpaletterows"></a>CMFCToolBarMenuButton::GetPaletteRows  
 Devuelve el número de filas en el menú desplegable cuando el menú está en modo de paleta.  
  
```  
int GetPaletteRows() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas en la paleta.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el botón de menú se establece en modo de paleta, elementos de menú aparecen en varias columnas con sólo un número limitado de filas. Llamar a este método para obtener el número de filas. Puede habilitar o deshabilitar el modo de paleta y especifique el número de filas mediante [CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode).  
  
##  <a name="getpopupmenu"></a>CMFCToolBarMenuButton::GetPopupMenu  
 Devuelve un puntero a la [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto que representa el menú desplegable del botón.  
  
```  
CMFCPopupMenu* GetPopupMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto creado cuando el marco de trabajo dibujó el submenú del botón de menú de la barra de herramientas; `NULL` si no se muestra ningún submenú.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un botón de menú de la barra de herramientas muestra un menú desplegable, el botón crea un [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto para representar el menú. Llamar a este método para obtener un puntero a la `CMFCPopupMenu` objeto. No debería almacenar el puntero devuelto, porque es temporal y deja de ser válido cuando el usuario cierra el menú desplegable.  
  
##  <a name="isdroppeddown"></a>CMFCToolBarMenuButton::IsDroppedDown  
 Indica si actualmente se muestra el menú emergente.  
  
```  
virtual BOOL IsDroppedDown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón de menú de la barra de herramientas muestra su submenú; de lo contrario, `FALSE`.  
  
##  <a name="isemptymenuallowed"></a>CMFCToolBarMenuButton::IsEmptyMenuAllowed  
 Especifica si los elementos de menú muestra los submenús vacíos.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo abre un submenú del elemento de menú seleccionado incluso cuando el submenú está vacío; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un usuario intenta abrir el submenú de elemento de menú actualmente seleccionado. Si el submenú está vacío y `IsEmptyMenuAllowed` devuelve `FALSE`, no se abre el submenú.  
  
 La implementación predeterminada devuelve `FALSE`. Invalide este método para personalizar este comportamiento.  
  
##  <a name="isexclusive"></a>CMFCToolBarMenuButton::IsExclusive  
 Indica si el botón está en modo exclusivo.  
  
```  
virtual BOOL IsExclusive() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón está funcionando en modo exclusivo; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario abre un menú emergente de un botón y, a continuación, mueve el puntero del mouse sobre otro botón de barra de herramientas o menú, se cierra el menú emergente, a menos que el botón está en modo exclusivo.  
  
 La implementación predeterminada siempre devuelve `FALSE`. Invalide este método en una clase derivada si desea activar el modo exclusivo.  
  
##  <a name="ismenupalettemode"></a>CMFCToolBarMenuButton::IsMenuPaletteMode  
 Determina si el menú desplegable está en modo de paleta.  
  
```  
BOOL IsMenuPaletteMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si, en caso contrario, se activa el modo de paleta `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el botón de menú se establece en modo de paleta, elementos de menú aparecen en varias columnas con sólo un número limitado de filas. Llamar a este método para obtener el número de filas. Puede habilitar o deshabilitar el modo de paleta llamando a [CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode).  
  
##  <a name="istearoffmenu"></a>CMFCToolBarMenuButton::IsTearOffMenu  
 Indica si el menú desplegable tiene una barra desplazable.  
  
```  
virtual BOOL IsTearOffMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón de menú de la barra de herramientas tiene una barra desplazable; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para habilitar la característica desplazable y establecer la desplazable barra ID, llame a [CMFCToolBarMenuButton::SetTearOff](#settearoff).  
  
##  <a name="m_balwayscallownerdraw"></a>CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw  
 Especifica si el marco llama siempre [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) cuando se dibuja un botón.  
  
```  
static BOOL m_bAlwaysCallOwnerDraw;  
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se establece esta variable miembro en `TRUE`, el botón se llama siempre [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) método para mostrar la imagen en el botón. Cuando `m_bAlwaysCallOwnerDraw` es `FALSE`, el propio botón dibuja la imagen si la imagen está predefinida. De lo contrario, llama a `OnDrawMenuImage`.  
  
##  <a name="onaftercreatepopupmenu"></a>CMFCToolBarMenuButton::OnAfterCreatePopupMenu  

  
```  
virtual void OnAfterCreatePopupMenu();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onbeforedrag"></a>CMFCToolBarMenuButton::OnBeforeDrag  

  
```  
virtual BOOL OnBeforeDrag() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oncalculatesize"></a>CMFCToolBarMenuButton::OnCalculateSize  

  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `sizeDefault`  
 [in] `bHorz`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oncancelmode"></a>CMFCToolBarMenuButton::OnCancelMode  

  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarMenuButton::OnChangeParentWnd  

  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onclick"></a>CMFCToolBarMenuButton::OnClick  

  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `bDelay`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onclickmenuitem"></a>CMFCToolBarMenuButton::OnClickMenuItem  
 Lo llama el marco de trabajo cuando el usuario selecciona un elemento en el menú desplegable.  
  
```  
virtual BOOL OnClickMenuItem();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `FALSE`Si el marco de trabajo debe continuar el menú predeterminado, elemento de procesamiento; de lo contrario, `TRUE`. La implementación predeterminada siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario hace clic en un elemento de menú, el marco ejecuta un comando que está asociado con ese elemento.  
  
 Para personalizar el procesamiento del elemento de menú, invalidar `OnClickMenuItem` en una clase derivada de `CMFCToolBarMenuButton` clase. También deberá reemplazar [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) y reemplazan a los botones de menú que requieren un procesamiento especial con instancias de la clase derivada.  
  
##  <a name="oncontexthelp"></a>CMFCToolBarMenuButton::OnContextHelp  

  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondraw"></a>CMFCToolBarMenuButton::OnDraw  

  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `pImages`  
 [in] `bHorz`  
 [in] `bCustomizeMode`  
 [in] `bHighlight`  
 [in] `bDrawBorder`  
 [in] `bGrayDisabledButtons`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarMenuButton::OnDrawOnCustomizeList  

  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `bSelected`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="openpopupmenu"></a>CMFCToolBarMenuButton::OpenPopupMenu  
 Lo llama el marco de trabajo cuando el usuario abre el menú desplegable de un botón de menú de la barra de herramientas.  
  
```  
virtual BOOL OpenPopupMenu(CWnd* pWnd=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Especifica la ventana que recibe los comandos de menú desplegable. Puede ser `NULL` sólo si el botón de menú de la barra de herramientas tiene una ventana primaria.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Cuando un [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto se creó y se abrió correctamente; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función cuando el usuario abre un menú desplegable de un botón de menú de la barra de herramientas.  
  
##  <a name="resetimagetodefault"></a>CMFCToolBarMenuButton::ResetImageToDefault  

  
```  
virtual void ResetImageToDefault();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="savebarstate"></a>CMFCToolBarMenuButton::SaveBarState  

  
```  
virtual void SaveBarState();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se crea un botón de barra de herramientas como resultado de una operación de arrastrar y colocar. Este método llama a la [CMFCPopupMenu::SaveState](../../mfc/reference/cmfcpopupmenu-class.md#savestate) método en el menú emergente de nivel superior, que hace que el botón primario del menú emergente para volver a crear su menú.  
  
##  <a name="serialize"></a>CMFCToolBarMenuButton::Serialize  

  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setaccdata"></a>CMFCToolBarMenuButton::SetACCData  
 Establece los datos de accesibilidad para el elemento de la cinta de opciones.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParent`  
 La ventana principal para el elemento de la cinta de opciones.  
  
 `data`  
 Los datos de accesibilidad para el elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método establece los datos de accesibilidad para el elemento de la cinta de opciones y siempre devuelve `TRUE`. Invalide este método para establecer los datos de accesibilidad y devolver un valor que indique éxito o error.  
  
##  <a name="setmenuonly"></a>CMFCToolBarMenuButton::SetMenuOnly  
 Especifica si el botón se dibuja como un botón de menú o un botón de división que tiene un identificador de comando válido y un submenú.  
  
```  
void SetMenuOnly(BOOL bMenuOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMenuOnly`  
 `TRUE`para mostrar este botón como un botón de menú que tiene un identificador de comando válido y un submenú `FALSE` mostrar este botón como un botón de división que tiene un identificador de comando válido y un submenú.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, cuando un botón de menú de la barra de herramientas tiene un submenú y un identificador de comando, el menú aparece como un botón de división que tiene un botón principal y un botón de flecha abajo. Si se llama a este método y `bMenuOnly` es `TRUE`, el botón en su lugar aparece como un botón de menú único con una flecha hacia abajo en el botón. Cuando el usuario hace clic en la flecha en cualquier modo, se abre el submenú y, cuando el usuario hace clic en la parte no flecha del botón en ningún modo el marco ejecuta el comando.  
  
##  <a name="setmenupalettemode"></a>CMFCToolBarMenuButton::SetMenuPaletteMode  
 Especifica si el menú desplegable está en modo de paleta.  
  
```  
void SetMenuPaletteMode(
    BOOL bMenuPaletteMode=TRUE,  
    int nPaletteRows=1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMenuPaletteMode`  
 Especifica si el menú desplegable está en modo de paleta.  
  
 [in] `nPaletteRows`  
 Número de filas de la paleta.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de paleta, todos los elementos de menú se muestran como una paleta de varias columnas. Especificar el número de filas mediante `nPaletteRows`.  
  
##  <a name="setmessagewnd"></a>CMFCToolBarMenuButton::SetMessageWnd  

  
```  
void SetMessageWnd(CWnd* pWndMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndMessage`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setradio"></a>CMFCToolBarMenuButton::SetRadio  
 Establece el botón de menú de la barra de herramientas para mostrar un icono de estilo de botón de radio cuando se activa.  
  
```  
virtual void SetRadio();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se dibuja el botón de menú mientras se comprueba, llama a [CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck) para dibujar un icono de marca de verificación. De forma predeterminada, `OnDrawMenuCheck` las solicitudes que el administrador visual actual dibuja una casilla de verificación estilo de marca de verificación en el botón de menú. Después de llamar a este método, el administrador visual actual dibuja en su lugar una marca de verificación de estilo de botón de radio en el botón de menú. Este cambio no se puede deshacer.  
  
 Cuando se llama a este método y el botón de menú que se muestra actualmente, se actualizará.  
  
##  <a name="settearoff"></a>CMFCToolBarMenuButton::SetTearOff  
 Especifica el identificador de la barra desplazable para el menú desplegable.  
  
```  
virtual void SetTearOff(UINT uiBarID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiBarID`  
 Especifica un nuevo desplazable barra Id.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para especificar el identificador de la barra desplazable que se crea cuando el usuario arrastra el botón de menú de una barra de menús. Si el `uiBarID` parámetro es 0, el usuario no puede arrancar en el botón de menú.  
  
 Llame a [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) para habilitar la característica de menú en la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
