---
title: CMDIFrameWnd (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: a6e68f6368a7b45e0a566a7d2d12f23a9cd62b12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370053"
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
|[CMDIFrameWnd::CreateClient](#createclient)|Crea una ventana MDICLIENT `CMDIFrameWnd`de Windows para esto . Llamado por `OnCreate` la `CWnd`función miembro de .|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Crea una nueva ventana secundaria.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Devuelve el menú emergente Ventana.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Activa una ventana secundaria MDI diferente.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Organiza todas las ventanas secundarias en un formato en cascada.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Recupera la ventana secundaria MDI activa actualmente, junto con una marca que indica si el elemento secundario está maximizado o no.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Organiza todas las ventanas secundarias de documentos minimizadas.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximiza una ventana secundaria MDI.|
|[CMDIFrameWnd::MDINext](#mdinext)|Activa la ventana secundaria inmediatamente detrás de la ventana secundaria activa actualmente y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Activa la ventana secundaria anterior y coloca la ventana secundaria activa inmediatamente detrás de ella.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Reemplaza el menú de una ventana de marco MDI, el menú emergente Ventana o ambos.|
|[CMDIFrameWnd::MDITile](#mditile)|Organiza todas las ventanas secundarias en un formato de mosaico.|

## <a name="remarks"></a>Observaciones

Para crear una ventana de marco MDI útil `CMDIFrameWnd`para la aplicación, derive una clase de . Agregue variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Puede construir una ventana de marco MDI llamando a `CFrameWnd`la [create](../../mfc/reference/cframewnd-class.md#create) o [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) función miembro de .

Antes de `Create` `LoadFrame`llamar o , debe construir el objeto de ventana de marco en el montón mediante el **operador new** C++. Antes `Create` de llamar también puede registrar una clase de ventana con la función global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) para establecer el icono y los estilos de clase para el marco.

Utilice `Create` la función miembro para pasar los parámetros de creación del marco como argumentos inmediatos.

`LoadFrame`requiere menos argumentos `Create`que , y en su lugar recupera la mayoría de sus valores predeterminados de los recursos, incluidos el título, el icono, la tabla de aceleradores y el menú del marco. Para que `LoadFrame`se pueda tener acceso a ellos , todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Aunque `MDIFrameWnd` se deriva `CFrameWnd`de , no `CMDIFrameWnd` es necesario declarar `DECLARE_DYNCREATE`con .

La `CMDIFrameWnd` clase hereda gran parte `CFrameWnd`de su implementación predeterminada de . Para obtener una lista detallada de estas características, consulte la descripción de la clase [CFrameWnd.](../../mfc/reference/cframewnd-class.md) La `CMDIFrameWnd` clase tiene las siguientes características adicionales:

- Una ventana de marco MDI administra la ventana MDICLIENT, reposicionándola junto con las barras de control. La ventana de cliente MDI es el elemento primario directo de las ventanas de marco secundario MDI. Los estilos de ventana WS_HSCROLL `CMDIFrameWnd` y WS_VSCROLL especificados en una aplicación a la ventana de cliente MDI en lugar de la ventana de marco principal para que el usuario pueda desplazarse por el área de cliente MDI (como en el Administrador de programas de Windows, por ejemplo).

- Una ventana de marco MDI posee un menú predeterminado que se utiliza como la barra de menús cuando no hay ninguna ventana secundaria MDI activa. Cuando hay un elemento secundario MDI activo, la barra de menús de la ventana de marco MDI se reemplaza automáticamente por el menú de la ventana secundaria MDI.

- Una ventana de marco MDI funciona junto con la ventana secundaria MDI actual, si la hay. Por ejemplo, los mensajes de comando se delegan en el elemento secundario MDI activo actualmente antes de la ventana de marco MDI.

- Una ventana de marco MDI tiene controladores predeterminados para los siguientes comandos de menú de ventana estándar:

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- Una ventana de marco MDI también tiene una implementación de ID_WINDOW_NEW, que crea un nuevo marco y vista en el documento actual. Una aplicación puede invalidar estas implementaciones de comandos predeterminadas para personalizar el control de ventanas MDI.

No utilice el operador **de eliminación** C++ para destruir una ventana de marco. En su lugar, use `CWnd::DestroyWindow`. La `CFrameWnd` implementación de `PostNcDestroy` eliminará el objeto C++ cuando se destruya la ventana. Cuando el usuario cierra la ventana `OnClose` de `DestroyWindow`marco, el controlador predeterminado llamará a .

Para obtener `CMDIFrameWnd`más información sobre , consulte [Ventanas](../../mfc/frame-windows.md)de marco .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd

Construye un objeto `CMDIFrameWnd`.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Observaciones

Llame `Create` a `LoadFrame` la función o miembro para crear la ventana de marco MDI visible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd::CreateClient

Crea la ventana de cliente `CMDIChildWnd` MDI que administra los objetos.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parámetros

*lpCreateStruct*<br/>
Un puntero largo a una estructura [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

*pWindowMenu*<br/>
Un puntero al menú emergente Ventana.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro debe llamarse si invalida la `OnCreate` función miembro directamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd::CreateNewChild

Crea una nueva ventana secundaria.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Parámetros

*pClass*<br/>
La clase en tiempo de ejecución de la ventana secundaria que se va a crear.

*nResource*<br/>
El identificador de los recursos compartidos asociados a la ventana secundaria.

*hMenú*<br/>
Menú de la ventana secundaria.

*hAccel*<br/>
El acelerador de la ventana del niño.

### <a name="remarks"></a>Observaciones

Utilice esta función para crear ventanas secundarias de una ventana de marco MDI.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup

Llame a esta función miembro para obtener un identificador del menú emergente actual denominado "Ventana" (el menú emergente con elementos de menú para la administración de ventanas MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parámetros

*hMenuBar*<br/>
La barra de menús actual.

### <a name="return-value"></a>Valor devuelto

El menú emergente Ventana si existe; NULL.

### <a name="remarks"></a>Observaciones

La implementación predeterminada busca un menú emergente que contenga comandos de menú ventana estándar, como ID_WINDOW_NEW y ID_WINDOW_TILE_HORZ.

Invalide esta función miembro si tiene un menú Ventana que no utiliza los identificadores de comando de menú estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd::MDIActivate

Activa una ventana secundaria MDI diferente.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parámetros

*pWndActivate*<br/>
Señala a la ventana secundaria MDI que se va a activar.

### <a name="remarks"></a>Observaciones

Esta función miembro envía el [mensaje de WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) a la ventana secundaria que se está activando y a la ventana secundaria que se está desactivando.

Este es el mismo mensaje que se envía si el usuario cambia el foco a una ventana secundaria MDI mediante el mouse o el teclado.

> [!NOTE]
> Una ventana secundaria MDI se activa independientemente de la ventana de marco MDI. Cuando el marco se activa, la ventana secundaria que se activó por última vez se envía un [mensaje de WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) para dibujar un marco de ventana activo y la barra de título, pero no recibe otro mensaje WM_MDIACTIVATE.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd::MDICascade

Organiza todas las ventanas secundarias MDI en un formato en cascada.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parámetros

*nType*<br/>
Especifica una marca en cascada. Solo se puede especificar la siguiente marca: MDITILE_SKIPDISABLED, lo que impide que las ventanas secundarias MDI deshabilitadas se conecten en cascada.

### <a name="remarks"></a>Observaciones

La primera `MDICascade`versión de , sin parámetros, conecta en cascada todas las ventanas secundarias MDI, incluidas las deshabilitadas. Opcionalmente, la segunda versión no deshabilita en cascada las ventanas secundarias MDI si especifica MDITILE_SKIPDISABLED para el *nType* parámetro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive

Recupera la ventana secundaria MDI activa actual, junto con una marca que indica si se maximiza la ventana secundaria.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parámetros

*pbMaximized*<br/>
Un puntero a un valor devuelto BOOL. Establezca en TRUE al devolver si la ventana está maximizada; de lo contrario FALSO.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana secundaria MDI activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange

Organiza todas las ventanas secundarias de documentos minimizadas.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Observaciones

No afecta a las ventanas secundarias que no se minimizan.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximize

Maximiza la ventana secundaria MDI especificada.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana para maximizar.

### <a name="remarks"></a>Observaciones

Cuando se maximiza una ventana secundaria, Windows la cambia de tamaño para que su área de cliente llene la ventana de cliente. Windows coloca el menú Control de la ventana secundaria en la barra de menús del marco para que el usuario pueda restaurar o cerrar la ventana secundaria. También agrega el título de la ventana secundaria al título de la ventana de marco.

Si se activa otra ventana secundaria MDI cuando se maximiza la ventana secundaria MDI activa actualmente, Windows restaura el elemento secundario activo actualmente y maximiza la ventana secundaria recién activada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd::MDINext

Activa la ventana secundaria inmediatamente detrás de la ventana secundaria activa actualmente y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.

```
void MDINext();
```

### <a name="remarks"></a>Observaciones

Si se maximiza la ventana secundaria MDI actualmente activa, la función miembro restaura el elemento secundario activo actualmente y maximiza el elemento secundario recién activado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd::MDIPrev

Activa la ventana secundaria anterior y coloca la ventana secundaria activa inmediatamente detrás de ella.

```
void MDIPrev();
```

### <a name="remarks"></a>Observaciones

Si se maximiza la ventana secundaria MDI actualmente activa, la función miembro restaura el elemento secundario activo actualmente y maximiza el elemento secundario recién activado.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd::MDIRestore

Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que se va a restaurar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu

Reemplaza el menú de una ventana de marco MDI, el menú emergente Ventana o ambos.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parámetros

*pFrameMenu*<br/>
Especifica el menú del nuevo menú de ventana de marco. Si NULL, el menú no se cambia.

*pWindowMenu*<br/>
Especifica el menú del nuevo menú emergente Ventana. Si NULL, el menú no se cambia.

### <a name="return-value"></a>Valor devuelto

Un puntero al menú de ventana de marco reemplazado por este mensaje. El puntero puede ser temporal y no se debe almacenar para su uso posterior.

### <a name="remarks"></a>Observaciones

Después `MDISetMenu`de llamar a , una aplicación `CWnd` debe llamar a la [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) función miembro de para actualizar la barra de menús.

Si esta llamada reemplaza el menú emergente Ventana, los elementos de menú de la ventana secundaria MDI se eliminan del menú Ventana anterior y se agregan al nuevo menú emergente Ventana.

Si se maximiza una ventana secundaria MDI y esta llamada reemplaza el menú de ventana de marco MDI, el menú Control y los controles de restauración se quitan del menú de ventana de marco anterior y se agregan al nuevo menú.

No llame a esta función miembro si usa el marco de trabajo para administrar las ventanas secundarias MDI.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd::MDITile

Organiza todas las ventanas secundarias en un formato de mosaico.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parámetros

*nType*<br/>
Especifica un indicador de ordenamiento en teselas. Este parámetro puede ser cualquiera de los siguientes indicadores:

- MDITILE_HORIZONTAL ventanas secundarias de Tiles MDI para que aparezca una ventana encima de otra.

- MDITILE_SKIPDISABLED Impide que se alicen ventanas secundarias MDI deshabilitadas.

- MDITILE_VERTICAL ventanas secundarias de Tiles MDI para que aparezca una ventana al lado de otra.

### <a name="remarks"></a>Observaciones

La primera `MDITile`versión de , sin parámetros, teselas las ventanas verticalmente en las versiones 3.1 y posteriores de Windows. La segunda versión teselas ventanas vertical u horizontalmente, dependiendo del valor de la *nType* parámetro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[EJEMPLO de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
