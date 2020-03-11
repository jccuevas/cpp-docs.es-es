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
ms.openlocfilehash: 20d74030cdc90ed2e1a7809c121967e74db21b4a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866571"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd (clase)

Proporciona la funcionalidad de una ventana de marco de MDI (interfaz de varios documentos) de Windows, junto con miembros para administrar la ventana.

## <a name="syntax"></a>Sintaxis

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMDIFrameWnd:: CMDIFrameWnd](#cmdiframewnd)|Construye un objeto `CMDIFrameWnd`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMDIFrameWnd:: CreateClient](#createclient)|Crea una ventana de Windows MDICLIENT para esta `CMDIFrameWnd`. Llamado por la función miembro `OnCreate` de `CWnd`.|
|[CMDIFrameWnd:: CreateNewChild](#createnewchild)|Crea una nueva ventana secundaria.|
|[CMDIFrameWnd:: GetWindowMenuPopup](#getwindowmenupopup)|Devuelve el menú emergente de la ventana.|
|[CMDIFrameWnd:: MDIActivate](#mdiactivate)|Activa una ventana secundaria MDI diferente.|
|[CMDIFrameWnd:: MDICascade](#mdicascade)|Organiza todas las ventanas secundarias en un formato en cascada.|
|[CMDIFrameWnd:: MDIGetActive](#mdigetactive)|Recupera la ventana MDI secundaria actualmente activa, junto con una marca que indica si el elemento secundario está maximizado o no.|
|[CMDIFrameWnd:: MDIIconArrange](#mdiiconarrange)|Organiza todas las ventanas secundarias de documento minimizadas.|
|[CMDIFrameWnd:: MDIMaximize](#mdimaximize)|Maximiza una ventana secundaria MDI.|
|[CMDIFrameWnd:: MDINext](#mdinext)|Activa la ventana secundaria inmediatamente detrás de la ventana secundaria actualmente activa y coloca la ventana secundaria activa actualmente detrás de las demás ventanas secundarias.|
|[CMDIFrameWnd:: MDIPrev](#mdiprev)|Activa la ventana secundaria anterior y coloca la ventana secundaria activa actualmente detrás de ella.|
|[CMDIFrameWnd:: MDIRestore](#mdirestore)|Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.|
|[CMDIFrameWnd:: MDISetMenu](#mdisetmenu)|Reemplaza el menú de una ventana de marco MDI, el menú emergente ventana o ambos.|
|[CMDIFrameWnd:: MDITile](#mditile)|Organiza todas las ventanas secundarias en un formato en mosaico.|

## <a name="remarks"></a>Observaciones

Para crear una ventana de marco MDI útil para la aplicación, derive una clase de `CMDIFrameWnd`. Agregue variables de miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Puede crear una ventana de marco MDI llamando a la función miembro [Create](../../mfc/reference/cframewnd-class.md#create) o [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) de `CFrameWnd`.

Antes de llamar a `Create` o `LoadFrame`, debe construir el objeto de ventana de marco en el montón C++ mediante el operador **New** . Antes de llamar a `Create` también puede registrar una clase de ventana con la función global [AfxRegisterWndClass (](application-information-and-management.md#afxregisterwndclass) para establecer el icono y los estilos de clase para el marco.

Utilice la función miembro `Create` para pasar los parámetros de creación del marco como argumentos inmediatos.

`LoadFrame` requiere menos argumentos que `Create`y, en su lugar, recupera la mayoría de los valores predeterminados de los recursos, incluidos el título, el icono, la tabla de aceleradores y el menú del marco. Para tener acceso a ellos mediante `LoadFrame`, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Aunque `MDIFrameWnd` se deriva de `CFrameWnd`, no es necesario declarar una clase de ventana de marco derivada de `CMDIFrameWnd` con `DECLARE_DYNCREATE`.

La clase `CMDIFrameWnd` hereda gran parte de su implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte la descripción de la clase [CFrameWnd](../../mfc/reference/cframewnd-class.md) . La clase `CMDIFrameWnd` tiene las siguientes características adicionales:

- Una ventana de marco MDI administra la ventana MDICLIENT y la coloca en conjunción con las barras de control. La ventana de cliente MDI es el elemento primario directo de las ventanas de marco secundario MDI. Los estilos de ventana WS_HSCROLL y WS_VSCROLL especificados en un `CMDIFrameWnd` se aplican a la ventana de cliente MDI en lugar de a la ventana de marco principal para que el usuario pueda desplazarse por el área de cliente MDI (como en el administrador de programas de Windows, por ejemplo).

- Una ventana de marco MDI posee un menú predeterminado que se utiliza como barra de menús cuando no hay ninguna ventana secundaria MDI activa. Cuando hay un elemento secundario MDI activo, la barra de menús de la ventana de marco MDI se reemplaza automáticamente en el menú de la ventana secundaria MDI.

- Una ventana de marco MDI funciona junto con la ventana secundaria MDI actual, si hay alguna. Por ejemplo, los mensajes de comando se delegan al elemento secundario MDI activo en ese momento antes de la ventana de marco MDI.

- Una ventana de marco MDI tiene controladores predeterminados para los siguientes comandos de menú estándar de la ventana:

    - ID_WINDOW_TILE_VERT

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- Una ventana de marco MDI también tiene una implementación de ID_WINDOW_NEW, que crea un nuevo marco y una vista en el documento actual. Una aplicación puede invalidar estas implementaciones de comandos predeterminadas para personalizar el control de ventanas MDI.

No use el C++ operador **Delete** para destruir una ventana de marco. En su lugar, use `CWnd::DestroyWindow`. La implementación de `CFrameWnd` de `PostNcDestroy` eliminará C++ el objeto cuando se destruya la ventana. Cuando el usuario cierra la ventana de marco, el controlador de `OnClose` predeterminado llamará a `DestroyWindow`.

Para obtener más información sobre `CMDIFrameWnd`, consulte [ventanas de marco](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cmdiframewnd"></a>CMDIFrameWnd:: CMDIFrameWnd

Construye un objeto `CMDIFrameWnd`.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Observaciones

Llame a la función miembro `Create` o `LoadFrame` para crear la ventana de marco MDI visible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

##  <a name="createclient"></a>CMDIFrameWnd:: CreateClient

Crea la ventana de cliente MDI que administra los objetos `CMDIChildWnd`.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parámetros

*lpCreateStruct*<br/>
Un puntero largo a una estructura [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) .

*pWindowMenu*<br/>
Un puntero al menú emergente de la ventana.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se debe llamar a esta función miembro si se reemplaza la función miembro de `OnCreate` directamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

##  <a name="createnewchild"></a>CMDIFrameWnd:: CreateNewChild

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
Clase en tiempo de ejecución de la ventana secundaria que se va a crear.

*nResource*<br/>
IDENTIFICADOR de recursos compartidos asociados a la ventana secundaria.

*hMenu*<br/>
Menú de la ventana secundaria.

*hAccel*<br/>
Acelerador de la ventana secundaria.

### <a name="remarks"></a>Observaciones

Utilice esta función para crear ventanas secundarias de una ventana de marco MDI.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>CMDIFrameWnd:: GetWindowMenuPopup

Llame a esta función miembro para obtener un identificador para el menú emergente actual denominado "Window" (menú emergente con elementos de menú para la administración de ventanas MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parámetros

*hMenuBar*<br/>
Barra de menús actual.

### <a name="return-value"></a>Valor devuelto

El menú emergente de la ventana si existe uno; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

La implementación predeterminada busca un menú emergente que contiene comandos de menú de ventana estándar, como ID_WINDOW_NEW y ID_WINDOW_TILE_HORZ.

Invalide esta función miembro si tiene un menú ventana que no use los identificadores de comando de menú estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

##  <a name="mdiactivate"></a>CMDIFrameWnd:: MDIActivate

Activa una ventana secundaria MDI diferente.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parámetros

*pWndActivate*<br/>
Apunta a la ventana secundaria MDI que se va a activar.

### <a name="remarks"></a>Observaciones

Esta función miembro envía el mensaje de [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) a la ventana secundaria que se está activando y se desactiva la ventana secundaria.

Este es el mismo mensaje que se envía si el usuario cambia el foco a una ventana secundaria MDI mediante el mouse o el teclado.

> [!NOTE]
>  Una ventana secundaria MDI se activa independientemente de la ventana de marco MDI. Cuando el marco se activa, la ventana secundaria que se activó por última vez se envía un mensaje de [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) para dibujar un marco de ventana activo y una barra de título, pero no recibe otro mensaje de WM_MDIACTIVATE.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd:: GetWindowMenuPopup](#getwindowmenupopup).

##  <a name="mdicascade"></a>CMDIFrameWnd:: MDICascade

Organiza todas las ventanas secundarias MDI en un formato en cascada.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parámetros

*nType*<br/>
Especifica una marca en cascada. Solo se puede especificar la marca siguiente: MDITILE_SKIPDISABLED, que impide que las ventanas secundarias MDI deshabilitadas se ejecuten en cascada.

### <a name="remarks"></a>Observaciones

La primera versión de `MDICascade`, sin parámetros, organiza en cascada todas las ventanas secundarias MDI, incluidas las deshabilitadas. Opcionalmente, la segunda versión no deshabilita en cascada las ventanas secundarias MDI deshabilitadas si se especifica MDITILE_SKIPDISABLED para el parámetro *ndeclaraciones* .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

##  <a name="mdigetactive"></a>CMDIFrameWnd:: MDIGetActive

Recupera la ventana secundaria MDI activa actual, junto con una marca que indica si la ventana secundaria está maximizada.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parámetros

*pbMaximized*<br/>
Un puntero a un valor devuelto de BOOL. Se establece en TRUE en la devolución si la ventana está maximizada; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana secundaria MDI activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIChildWnd:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdiiconarrange"></a>CMDIFrameWnd:: MDIIconArrange

Organiza todas las ventanas secundarias de documento minimizadas.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Observaciones

No afecta a las ventanas secundarias que no están minimizadas.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd:: MDICascade](#mdicascade).

##  <a name="mdimaximize"></a>CMDIFrameWnd:: MDIMaximize

Maximiza la ventana secundaria MDI especificada.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana para maximizar.

### <a name="remarks"></a>Observaciones

Cuando una ventana secundaria está maximizada, Windows la cambia para que su área cliente rellene la ventana del cliente. Windows coloca el menú de control de la ventana secundaria en la barra de menús del marco para que el usuario pueda restaurar o cerrar la ventana secundaria. También agrega el título de la ventana secundaria al título de la ventana de marco.

Si se activa otra ventana secundaria MDI cuando se maximiza la ventana secundaria MDI activa actualmente, Windows restaura el elemento secundario actualmente activo y maximiza la ventana secundaria que se acaba de activar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIChildWnd:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdinext"></a>CMDIFrameWnd:: MDINext

Activa la ventana secundaria inmediatamente detrás de la ventana secundaria actualmente activa y coloca la ventana secundaria activa actualmente detrás de las demás ventanas secundarias.

```
void MDINext();
```

### <a name="remarks"></a>Observaciones

Si la ventana MDI secundaria actualmente activa está maximizada, la función miembro restaura el elemento secundario actualmente activo y maximiza el secundario que se acaba de activar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

##  <a name="mdiprev"></a>CMDIFrameWnd:: MDIPrev

Activa la ventana secundaria anterior y coloca la ventana secundaria activa actualmente detrás de ella.

```
void MDIPrev();
```

### <a name="remarks"></a>Observaciones

Si la ventana MDI secundaria actualmente activa está maximizada, la función miembro restaura el elemento secundario actualmente activo y maximiza el secundario que se acaba de activar.

##  <a name="mdirestore"></a>CMDIFrameWnd:: MDIRestore

Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que se va a restaurar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIChildWnd:: MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

##  <a name="mdisetmenu"></a>CMDIFrameWnd:: MDISetMenu

Reemplaza el menú de una ventana de marco MDI, el menú emergente ventana o ambos.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parámetros

*pFrameMenu*<br/>
Especifica el menú del nuevo menú de ventana de marco. Si es NULL, el menú no cambia.

*pWindowMenu*<br/>
Especifica el menú del menú emergente nueva ventana. Si es NULL, el menú no cambia.

### <a name="return-value"></a>Valor devuelto

Un puntero al menú de la ventana de marco reemplazado por este mensaje. El puntero puede ser temporal y no se debe almacenar para su uso posterior.

### <a name="remarks"></a>Observaciones

Después de llamar a `MDISetMenu`, una aplicación debe llamar a la función miembro [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) de `CWnd` para actualizar la barra de menús.

Si esta llamada reemplaza el menú emergente ventana, los elementos de menú de la ventana secundaria MDI se quitan del menú ventana anterior y se agregan al menú emergente nueva ventana.

Si una ventana secundaria MDI está maximizada y esta llamada reemplaza el menú marco MDI-ventana, los controles menú control y restaurar se quitan del menú de la ventana de marco anterior y se agregan al menú nuevo.

No llame a esta función miembro si usa el marco de trabajo para administrar las ventanas secundarias MDI.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

##  <a name="mditile"></a>CMDIFrameWnd:: MDITile

Organiza todas las ventanas secundarias en un formato en mosaico.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parámetros

*nType*<br/>
Especifica una marca de mosaico. Este parámetro puede ser cualquiera de las marcas siguientes:

- MDITILE_HORIZONTAL mosaicos ventanas secundarias MDI para que una ventana aparezca sobre otra.

- MDITILE_SKIPDISABLED impide que las ventanas secundarias MDI deshabilitadas se muestren en mosaico.

- MDITILE_VERTICAL mosaicos ventanas secundarias MDI para que una ventana aparezca junto a otra.

### <a name="remarks"></a>Observaciones

La primera versión de `MDITile`, sin parámetros, organiza las ventanas en mosaico vertical en las versiones 3,1 y posteriores de Windows. La segunda versión segmenta ventanas vertical u horizontalmente, según el valor del parámetro *ndeclaraciones* .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd:: MDICascade](#mdicascade).

## <a name="see-also"></a>Consulte también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
