---
title: CMDIFrameWnd (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb9f87ed5ae3027e7743a36c2484017d6381f95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374044"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd (clase)
Proporciona la funcionalidad de una ventana de marco de MDI (interfaz de varios documentos) de Windows, junto con miembros para administrar la ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Construye un objeto `CMDIFrameWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIFrameWnd::CreateClient](#createclient)|Crea una ventana de **MDICLIENT** ventana para este `CMDIFrameWnd`. Llamado por el `OnCreate` función miembro de `CWnd`.|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Crea una nueva ventana secundaria.|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Devuelve el menú emergente de la ventana.|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Activa una ventana secundaria MDI diferentes.|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|Organiza todas las ventanas secundarias en un formato en cascada.|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Recupera la ventana de elemento secundario MDI activa actualmente, junto con una marca que indica si el elemento secundario está maximizado.|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Organiza todas las ventanas secundarias de documento minimizada.|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximiza una ventana secundaria MDI.|  
|[CMDIFrameWnd::MDINext](#mdinext)|Activa la ventana secundaria inmediatamente detrás de la ventana secundaria activa actualmente y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Activa la ventana secundaria anterior y coloca la ventana secundaria actualmente activa inmediatamente detrás de él.|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Restaura una ventana secundaria MDI de tamaño minimizado o maximizado.|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Reemplaza el menú de una ventana de marco MDI, el menú emergente de la ventana o ambos.|  
|[CMDIFrameWnd::MDITile](#mditile)|Organiza todas las ventanas secundarias en un formato de mosaico.|  
  
## <a name="remarks"></a>Comentarios  
 Para crear una ventana de marco MDI útil para la aplicación, derive una clase de `CMDIFrameWnd`. Agregue variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.  
  
 Puede crear una ventana de marco MDI mediante una llamada a la [crear](../../mfc/reference/cframewnd-class.md#create) o [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) función miembro de `CFrameWnd`.  
  
 Antes de llamar a **crear** o `LoadFrame`, debe crear el objeto de ventana de marco en el montón mediante C++ **nueva** operador. Antes de llamar a **crear** también se puede registrar una clase de ventana con la [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.  
  
 Use la **crear** función miembro para pasar parámetros de creación del marco inmediatas como argumentos.  
  
 `LoadFrame` requiere menos argumentos que **crear**y en su lugar recupera la mayoría de sus valores predeterminados de recursos, incluidos el título del marco, icono, tabla de aceleradores y menús. Para tener acceso a `LoadFrame`, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, **IDR_MAINFRAME**).  
  
 Aunque **MDIFrameWnd** se deriva de `CFrameWnd`, deriva una clase de ventana de marco `CMDIFrameWnd` no debe declararse con `DECLARE_DYNCREATE`.  
  
 El `CMDIFrameWnd` clase hereda gran parte de su implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte la [CFrameWnd](../../mfc/reference/cframewnd-class.md) descripción de la clase. La `CMDIFrameWnd` clase tiene las siguientes características adicionales:  
  
-   Una ventana de marco MDI administra la **MDICLIENT** ventana, volviéndola a junto con barras de control. La ventana de cliente MDI es el principal directo de las ventanas de marco secundarias MDI. El **WS_HSCROLL** y **WS_VSCROLL** estilos de ventana especificados en un `CMDIFrameWnd` se aplican a la ventana de cliente MDI en lugar de la ventana de marco principal para el usuario puede desplazar el área de cliente MDI (como en las ventanas Administrador de programas, por ejemplo).  
  
-   Una ventana de marco MDI posee un menú predeterminado que se utiliza como la barra de menús cuando no hay ninguna ventana secundaria MDI activa. Cuando hay un formulario secundario MDI activo, la barra de menús de la ventana de marco MDI se sustituye automáticamente por el menú de ventana secundaria MDI.  
  
-   Una ventana de marco MDI funciona junto con la ventana secundaria MDI actual, si hay alguno. Por ejemplo, mensajes de comando se delegan al formulario secundario MDI activo actualmente antes de la ventana de marco MDI.  
  
-   Una ventana de marco MDI tiene controladores predeterminados para los siguientes comandos de menú de ventana estándares:  
  
    - **ID_WINDOW_TILE_VERT**  
  
    - **ID_WINDOW_TILE_HORZ**  
  
    - **ID_WINDOW_CASCADE**  
  
    - **ID_WINDOW_ARRANGE**  
  
-   Una ventana de marco MDI también tiene una implementación de **ID_WINDOW_NEW**, que crea un nuevo marco y la vista en el documento actual. Una aplicación puede invalidar estas implementaciones de comando predeterminado para personalizar el control de ventana MDI.  
  
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
  
##  <a name="cmdiframewnd"></a>  CMDIFrameWnd::CMDIFrameWnd  
 Construye un objeto `CMDIFrameWnd`.  
  
```  
CMDIFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a la **crear** o `LoadFrame` función de miembro para crear la ventana de marco MDI visible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]  
  
##  <a name="createclient"></a>  CMDIFrameWnd::CreateClient  
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
 Debe llamar a esta función miembro si invalida el `OnCreate` directamente la función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]  
  
##  <a name="createnewchild"></a>  CMDIFrameWnd::CreateNewChild  
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
 El identificador de recursos compartidos asociados con la ventana secundaria.  
  
 `hMenu`  
 Menú de la ventana secundaria.  
  
 `hAccel`  
 Acelerador de la ventana secundaria.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para crear ventanas de una ventana de marco MDI secundarias.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 En este ejemplo es un fragmento del artículo de Knowledge Base Q201045, "HOWTO: agregar varios tipos de ventana a una aplicación MDI no-documento/vista." Artículos de Knowledge Base están disponibles en [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup  
 Llame a esta función miembro para obtener un identificador para el menú emergente actual con el nombre "Ventana" (es decir, el menú emergente con elementos de menú para la administración de ventanas MDI).  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>Parámetros  
 *hMenuBar*  
 La barra de menús actual.  
  
### <a name="return-value"></a>Valor devuelto  
 El menú emergente de ventana si existe; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada busca un menú emergente que contiene comandos del menú Ventana estándares como **ID_WINDOW_NEW** y **ID_WINDOW_TILE_HORZ**.  
  
 Reemplace esta función miembro si tiene un menú de ventana que no usa los identificadores de comando de menú estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate  
 Activa una ventana secundaria MDI diferentes.  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWndActivate*  
 Apunta a la ventana secundaria MDI que activarse.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro envía el [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) mensaje a la ventana secundaria se activa y la ventana secundaria que se está desactivando.  
  
 Este es el mismo mensaje que se envía si el usuario cambia el foco a una ventana secundaria MDI mediante el mouse o teclado.  
  
> [!NOTE]
>  Una ventana secundaria MDI se activa independientemente de la ventana de marco MDI. Cuando el marco se activa, se envía la ventana secundaria que se activó por última vez una [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) mensaje para dibujar un marco de ventana activa y barra de título, pero no recibe otra `WM_MDIACTIVATE` mensaje.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).  
  
##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade  
 Organiza todas las ventanas secundarias MDI en un formato en cascada.  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>Parámetros  
 `nType`  
 Especifica una marca en cascada. Se puede especificar sólo el siguiente indicador: `MDITILE_SKIPDISABLED`, lo que impide que deshabilitado ventanas secundarias MDI que se colocan en cascada.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión de `MDICascade`, sin parámetros en cascada todas las ventanas secundarias MDI, incluidos deshabilitado los. La segunda versión hace opcionalmente ventanas en cascada deshabilitado MDI secundario no si se especifica `MDITILE_SKIPDISABLED` para el `nType` parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive  
 Recupera la ventana activa actual MDI secundario, junto con una marca que indica si la ventana secundaria se maximiza.  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pbMaximized*  
 Un puntero a un **BOOL** valor devuelto. Establecido en **TRUE** en la devolución si la ventana está maximizada; en caso contrario **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana secundaria MDI activa.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange  
 Organiza todas las ventanas secundarias de documento minimizada.  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>Comentarios  
 No afecta a las ventanas secundarias que no se minimizan.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIFrameWnd::MDICascade](#mdicascade).  
  
##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize  
 Maximiza la ventana secundaria MDI especificada.  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntos a maximizar la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se maximiza una ventana secundaria, Windows lo modifica para realizar su área cliente rellenar la ventana del cliente. Windows coloca el menú ventana secundaria del Control en la barra de menús del marco para que el usuario pueda restaurar o cerrar la ventana secundaria. También se agrega el título de la ventana secundaria para el título de ventana de marco.  
  
 Si otra ventana secundaria MDI se activa cuando se maximiza la ventana secundaria MDI activa actualmente, Windows restaura al formulario secundario activo actualmente y maximiza la ventana secundaria recién activado.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext  
 Activa la ventana secundaria inmediatamente detrás de la ventana secundaria activa actualmente y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se maximiza la ventana secundaria MDI activa actualmente, la función miembro restaura al formulario secundario activo actualmente y maximiza al elemento secundario recién activado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev  
 Activa la ventana secundaria anterior y coloca la ventana secundaria actualmente activa inmediatamente detrás de él.  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se maximiza la ventana secundaria MDI activa actualmente, la función miembro restaura al formulario secundario activo actualmente y maximiza al elemento secundario recién activado.  
  
##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore  
 Restaura una ventana secundaria MDI de tamaño minimizado o maximizado.  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana para restaurar.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).  
  
##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu  
 Reemplaza el menú de una ventana de marco MDI, el menú emergente de la ventana o ambos.  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 *pFrameMenu*  
 Especifica el menú del nuevo menú de ventana de marco. Si **NULL**, no se cambia el menú.  
  
 `pWindowMenu`  
 Especifica el menú del menú emergente de ventana nueva. Si **NULL**, no se cambia el menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al menú de ventana de marco sustituido por este mensaje. El puntero puede ser temporal y no se debe almacenar para su uso posterior.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `MDISetMenu`, una aplicación debe llamar a la [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) función miembro de `CWnd` para actualizar la barra de menús.  
  
 Si esta llamada reemplaza el menú emergente de la ventana, elementos de menú de ventana secundaria MDI se quitan en el menú de ventana anterior y se ha agregado al menú emergente ventana nueva.  
  
 Si está maximizada una ventana secundaria MDI y esta llamada reemplaza el menú de la ventana de marco MDI, los controles de menú y la restauración de Control se quitan en el menú de ventana de marco anterior y se agrega al menú nuevo.  
  
 No llame a esta función miembro si usa el marco de trabajo para administrar las ventanas secundarias MDI.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>  CMDIFrameWnd::MDITile  
 Organiza todas las ventanas secundarias en un formato de mosaico.  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>Parámetros  
 `nType`  
 Especifica una marca de disposición en mosaico. Este parámetro puede ser cualquiera de los siguientes indicadores:  
  
- `MDITILE_HORIZONTAL` Iconos ventanas MDI secundarias para que una ventana aparece encima de otro.  
  
- `MDITILE_SKIPDISABLED` Impide que se coloca en mosaico deshabilitados ventanas secundarias MDI.  
  
- `MDITILE_VERTICAL` Iconos ventanas MDI secundarias para que una ventana aparece al lado del otro.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión de `MDITile`, sin parámetros, iconos de las ventanas verticalmente en las versiones 3.1 y posteriores de Windows. La segunda versión muestra ventanas en mosaico vertical u horizontalmente, dependiendo del valor de la `nType` parámetro.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMDIFrameWnd::MDICascade](#mdicascade).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Ejemplo MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Ejemplo SNAPVW de MFC](../../visual-cpp-samples.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
