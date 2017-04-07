---
title: CMDIFrameWnd (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
dev_langs:
- C++
helpviewer_keywords:
- MDI frame windows
- CMDIFrameWnd class
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
caps.latest.revision: 22
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
ms.openlocfilehash: 0eae6c14038dd27a5779757d1807068fbe865b81
ms.lasthandoff: 02/24/2017

---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd (clase)
Proporciona la funcionalidad de una ventana de marco de MDI (interfaz de varios documentos) de Windows, junto con miembros para administrar la ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Construye un objeto `CMDIFrameWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDIFrameWnd::CreateClient](#createclient)|Crea un Windows **MDICLIENT** ventana para este `CMDIFrameWnd`. Llamado por el `OnCreate` función miembro de `CWnd`.|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Crea una nueva ventana secundaria.|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Devuelve el menú emergente de la ventana.|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Activa una ventana secundaria MDI diferentes.|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|Organiza todas las ventanas secundarias en un formato en cascada.|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Recupera la ventana de secundario MDI activa actualmente, junto con una marca que indica si no se maximiza el elemento secundario.|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Organiza todas las ventanas secundarias de documento minimizada.|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximiza una ventana secundaria MDI.|  
|[CMDIFrameWnd::MDINext](#mdinext)|Activa la ventana secundaria inmediatamente detrás de la ventana secundaria activa y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Activa la ventana secundaria anterior y coloca la ventana secundaria activa actualmente inmediatamente detrás de él.|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Reemplaza el menú de una ventana de marco MDI, el menú emergente de la ventana o ambos.|  
|[CMDIFrameWnd::MDITile](#mditile)|Organiza todas las ventanas secundarias en un formato de mosaico.|  
  
## <a name="remarks"></a>Comentarios  
 Para crear una ventana de marco MDI útil para su aplicación, derive una clase de `CMDIFrameWnd`. Agregar variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.  
  
 Puede crear una ventana de marco MDI llamando a la [crear](../../mfc/reference/cframewnd-class.md#create) o [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) función miembro de `CFrameWnd`.  
  
 Antes de llamar a **crear** o `LoadFrame`, debe crear el objeto de ventana de marco en el montón mediante C++ **nuevo** operador. Antes de llamar a **crear** también se puede registrar una clase de ventana con el [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.  
  
 Utilice la **crear** función miembro para pasar los parámetros de creación del marco inmediatas como argumentos.  
  
 `LoadFrame`requiere menos argumentos que **crear**y en su lugar recupera la mayor parte de sus valores predeterminados de recursos, como el título del marco, icono, tabla de aceleradores y menús. Para tener acceso a `LoadFrame`, todos estos recursos deben tener el mismo identificador de recursos (por ejemplo, **IDR_MAINFRAME**).  
  
 Aunque **MDIFrameWnd** se deriva de `CFrameWnd`, deriva de una clase de ventana de marco `CMDIFrameWnd` no necesitan declararse con `DECLARE_DYNCREATE`.  
  
 El `CMDIFrameWnd` clase hereda gran parte de la implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte la [CFrameWnd](../../mfc/reference/cframewnd-class.md) descripción de clase. La `CMDIFrameWnd` clase tiene las siguientes características adicionales:  
  
-   Una ventana de marco MDI administra la **MDICLIENT** ventana, cambiar la posición junto con las barras de control. La ventana de cliente MDI es el principal directo de ventanas de marco secundarias MDI. El **WS_HSCROLL** y **WS_VSCROLL** estilos de ventana especificados en un `CMDIFrameWnd` se aplican a la ventana de cliente MDI en lugar de la ventana de marco principal para el usuario puede desplazar el área de cliente MDI (como en el programa Administrador de Windows, por ejemplo).  
  
-   Una ventana de marco MDI posee un menú predeterminado que se utiliza como la barra de menús cuando no hay ninguna ventana secundaria MDI activa. Cuando hay un formulario MDI secundario activo, la barra de menús de la ventana de marco MDI se reemplaza automáticamente por el menú de ventana secundaria MDI.  
  
-   Una ventana de marco MDI funciona junto con la ventana secundaria MDI actual, si hay alguno. Por ejemplo, mensajes de comandos se delegan al formulario MDI secundario activo antes de la ventana de marco MDI.  
  
-   Una ventana de marco MDI tiene controladores predeterminados para los siguientes comandos estándares del menú Ventana:  
  
    - **ID_WINDOW_TILE_VERT**  
  
    - **ID_WINDOW_TILE_HORZ**  
  
    - **ID_WINDOW_CASCADE**  
  
    - **ID_WINDOW_ARRANGE**  
  
-   Una ventana de marco MDI también tiene una implementación de **ID_WINDOW_NEW**, que crea un nuevo marco y la vista del documento actual. Una aplicación puede invalidar estas implementaciones de comando predeterminado para personalizar el control de ventana MDI.  
  
 No use C++ **eliminar** operador para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. El `CFrameWnd` implementación de `PostNcDestroy` eliminará el objeto de C++ cuando se destruye la ventana. Cuando el usuario cierra la ventana de marco, el valor predeterminado `OnClose` controlador llamará `DestroyWindow`.  
  
 Para obtener más información sobre `CMDIFrameWnd`, consulte [ventanas de marco](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd  
 Construye un objeto `CMDIFrameWnd`.  
  
```  
CMDIFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a la **crear** o `LoadFrame` función de miembro para crear la ventana de marco MDI visible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#13;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]  
  
##  <a name="createclient"></a>CMDIFrameWnd::CreateClient  
 Crea la ventana de cliente MDI que administra el `CMDIChildWnd` objetos.  
  
```  
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpCreateStruct`  
 Un puntero largo a una [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) estructura.  
  
 `pWindowMenu`  
 Un puntero al menú ventana emergente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro debe llamarse si reemplaza el `OnCreate` directamente la función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#14;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]  
  
##  <a name="createnewchild"></a>CMDIFrameWnd::CreateNewChild  
 Crea una nueva ventana secundaria.  
  
```  
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,  
    UINT nResource,  
    HMENU hMenu = NULL,  
    HACCEL hAccel = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pClass`  
 La clase en tiempo de ejecución de la ventana secundaria que se va a crear.  
  
 *nResource*  
 El identificador de recursos compartidos asociados a la ventana secundaria.  
  
 `hMenu`  
 Menú de la ventana secundaria.  
  
 `hAccel`  
 Acelerador de la ventana secundaria.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para crear ventanas de una ventana de marco MDI secundarias.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#15;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 En este ejemplo es un extracto del artículo de Knowledge Base Q201045, "Cómo: agregar varios tipos de ventana a una aplicación MDI de vista de documento de no." Artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup  
 Llame a esta función miembro para obtener un identificador para el menú emergente actual con el nombre "Ventana" (el menú emergente con los elementos de menú para la administración de ventanas MDI).  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>Parámetros  
 *hMenuBar*  
 La barra de menús actual.  
  
### <a name="return-value"></a>Valor devuelto  
 El menú emergente de ventana si existe; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada busca un menú emergente que contiene comandos estándares del menú Ventana como **ID_WINDOW_NEW** y **ID_WINDOW_TILE_HORZ**.  
  
 Reemplace esta función miembro si dispone de un menú de ventana que no utiliza los identificadores de comando de menú estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&16;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>CMDIFrameWnd::MDIActivate  
 Activa una ventana secundaria MDI diferentes.  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWndActivate*  
 Apunta a la ventana secundaria MDI se active.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro envía el [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) mensaje a la ventana secundaria activa y la ventana secundaria que se va a desactivar.  
  
 Este es el mismo mensaje que se envía si el usuario cambia el foco a una ventana secundaria MDI utilizando el mouse o el teclado.  
  
> [!NOTE]
>  Una ventana secundaria MDI se activa independientemente de la ventana de marco MDI. Cuando el marco se activa, se envía la ventana secundaria que se activó por última vez una [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) mensaje para dibujar un marco de ventana activa y barra de título, pero no recibe otra `WM_MDIACTIVATE` mensaje.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).  
  
##  <a name="mdicascade"></a>CMDIFrameWnd::MDICascade  
 Organiza todas las ventanas secundarias MDI en un formato en cascada.  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>Parámetros  
 `nType`  
 Especifica una marca en cascada. Se puede especificar sólo el siguiente indicador: `MDITILE_SKIPDISABLED`, lo que impide que deshabilitado ventanas MDI secundarias que se colocan en cascada.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión de `MDICascade`, sin parámetros, colocan en cascada todas las ventanas secundarias MDI, incluidos deshabilitado las. La segunda versión opcionalmente no ventanas en cascada deshabilitado MDI secundario no si se especifica `MDITILE_SKIPDISABLED` para el `nType` parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#17;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive  
 Recupera la actual ventana secundaria MDI activa, junto con una marca que indica si la ventana secundaria se maximiza.  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pbMaximized*  
 Un puntero a un **BOOL** valor devuelto. Establecer en **TRUE** si la ventana está maximizada; de lo contrario la devolución **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana secundaria MDI activa.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange  
 Organiza todas las ventanas secundarias de documento minimizada.  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>Comentarios  
 No afecta a las ventanas secundarias que no se minimizan.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIFrameWnd::MDICascade](#mdicascade).  
  
##  <a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximize  
 Maximiza la ventana MDI secundaria especificada.  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntos a maximizar la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se maximiza una ventana secundaria, Windows cambia su tamaño para que su área cliente ocupe la ventana de cliente. Windows coloca el menú ventana secundaria del Control en la barra de menús del marco para que el usuario pueda restaurar o cerrar la ventana secundaria. También agrega el título de la ventana secundaria en el título de ventana de marco.  
  
 Si otra ventana secundaria MDI se activa cuando se maximiza la ventana MDI secundaria activa actualmente, Windows restaura a los secundarios actualmente activos y maximiza la ventana secundaria recientemente activados.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdinext"></a>CMDIFrameWnd::MDINext  
 Activa la ventana secundaria inmediatamente detrás de la ventana secundaria activa y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se maximiza la ventana MDI secundaria activa actualmente, la función miembro restaura al secundario actualmente activo y maximiza al secundario recién activado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#18;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>CMDIFrameWnd::MDIPrev  
 Activa la ventana secundaria anterior y coloca la ventana secundaria activa actualmente inmediatamente detrás de él.  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se maximiza la ventana MDI secundaria activa actualmente, la función miembro restaura al secundario actualmente activo y maximiza al secundario recién activado.  
  
##  <a name="mdirestore"></a>CMDIFrameWnd::MDIRestore  
 Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana Restaurar.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).  
  
##  <a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu  
 Reemplaza el menú de una ventana de marco MDI, el menú emergente de la ventana o ambos.  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 *pFrameMenu*  
 Especifica el menú del nuevo menú de la ventana de marco. Si **NULL**, no se modifica el menú.  
  
 `pWindowMenu`  
 Especifica el menú del menú emergente ventana nueva. Si **NULL**, no se modifica el menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al menú de ventana de marco reemplazado por este mensaje. El puntero puede ser temporal y no se debe almacenar para su uso posterior.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `MDISetMenu`, una aplicación debe llamar a la [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) función miembro de `CWnd` para actualizar la barra de menús.  
  
 Si esta llamada reemplaza el menú emergente de la ventana, elementos de menú de ventana secundaria MDI se quita del menú Ventana anterior y se agregan a del menú emergente de la ventana nueva.  
  
 Si está maximizada una ventana secundaria MDI y esta llamada reemplaza el menú de la ventana de marco MDI, los controles de menú y restauración de Control se quitan desde el menú de la ventana de marco anterior y se agrega al menú nuevo.  
  
 No llame a esta función miembro si utiliza el marco de trabajo para administrar las ventanas secundarias MDI.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&19;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing&#20;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>CMDIFrameWnd::MDITile  
 Organiza todas las ventanas secundarias en un formato de mosaico.  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>Parámetros  
 `nType`  
 Especifica una marca de mosaico. Este parámetro puede ser uno de los siguientes indicadores:  
  
- `MDITILE_HORIZONTAL`Mosaicos ventanas MDI secundarias para que aparezca la uno ventana encima de otro.  
  
- `MDITILE_SKIPDISABLED`Impide que se coloca en mosaico ventanas secundarias de MDI deshabilitados.  
  
- `MDITILE_VERTICAL`Mosaicos ventanas MDI secundarias para que aparezca la uno ventana junto a otro.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión de `MDITile`, sin parámetros, en mosaico las ventanas verticalmente en las versiones 3.1 y versiones posteriores de Windows. La segunda versión muestra ventanas en mosaico vertical u horizontalmente, dependiendo del valor de la `nType` parámetro.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIFrameWnd::MDICascade](#mdicascade).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Ejemplo MDIDOCVW de MFC](../../visual-cpp-samples.md)   
 [Ejemplo de MFC SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)

