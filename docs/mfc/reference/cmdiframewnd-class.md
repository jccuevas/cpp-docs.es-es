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
ms.openlocfilehash: 9f5289491a7c14749865cfd163417440bc542aba
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776536"
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
|[CMDIFrameWnd::CreateClient](#createclient)|Crea una ventana MDICLIENT de Windows para este `CMDIFrameWnd`. Lo llama el `OnCreate` función miembro de `CWnd`.|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Crea una nueva ventana secundaria.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Devuelve el menú emergente de la ventana.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Activa una ventana secundaria MDI diferentes.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Organiza todas las ventanas secundarias en un formato en cascada.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Recupera la ventana de secundario MDI activa actualmente, junto con una marca que indica si el elemento secundario está maximizado.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Organiza todas las ventanas secundarias de documento minimizada.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximiza una ventana secundaria MDI.|
|[CMDIFrameWnd::MDINext](#mdinext)|Activa la ventana secundaria inmediatamente detrás de la ventana secundaria actualmente activa y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Activa la ventana secundaria anterior y coloca la ventana secundaria actualmente activa inmediatamente detrás de él.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Reemplaza el menú de una ventana de marco MDI, el menú emergente de la ventana o ambos.|
|[CMDIFrameWnd::MDITile](#mditile)|Organiza todas las ventanas secundarias en un formato de mosaico.|

## <a name="remarks"></a>Comentarios

Para crear una ventana de marco MDI útil para su aplicación, derive una clase de `CMDIFrameWnd`. Agregar variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Puede construir una ventana marco MDI mediante una llamada a la [crear](../../mfc/reference/cframewnd-class.md#create) o [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) función miembro de `CFrameWnd`.

Antes de llamar a `Create` o `LoadFrame`, debe construir el objeto de ventana de marco en el montón mediante C++ **nuevo** operador. Antes de llamar a `Create` también se puede registrar una clase de ventana con el [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.

Use el `Create` función miembro para pasar parámetros de creación del marco de inmediatos como argumentos.

`LoadFrame` requiere menos argumentos que `Create`y recupera en su lugar, la mayoría de sus valores predeterminados de recursos, incluidos el título del marco, icono, tabla de aceleradores y menús. Para tener acceso a `LoadFrame`, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Aunque `MDIFrameWnd` se deriva de `CFrameWnd`, deriva una clase de ventana de marco `CMDIFrameWnd` no debe declararse con `DECLARE_DYNCREATE`.

El `CMDIFrameWnd` clase hereda gran parte de su implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte el [CFrameWnd](../../mfc/reference/cframewnd-class.md) descripción de clase. La `CMDIFrameWnd` clase tiene las siguientes características adicionales:

- Una ventana marco MDI administra la ventana MDICLIENT, cambiar la posición junto con las barras de control. La ventana de cliente MDI es el elemento primario directo de ventanas de marco secundario MDI. Los estilos de ventana WS_HSCROLL y WS_VSCROLL especificados en un `CMDIFrameWnd` se aplican a la ventana de cliente MDI en lugar de la ventana de marco principal, por lo que el usuario puede desplazar el área de cliente MDI (como se muestra en el Windows Administrador de programas, por ejemplo).

- Una ventana marco MDI posee un menú predeterminado que se usa como la barra de menús cuando no hay ninguna ventana secundaria MDI activa. Cuando hay un formulario secundario MDI activo, la barra de menús de la ventana de marco MDI se reemplaza automáticamente por el menú de ventana secundaria MDI.

- Una ventana marco MDI funciona junto con la ventana secundaria MDI actual, si hay alguno. Por ejemplo, los mensajes de comandos se delegan al formulario secundario MDI activo antes de la ventana de marco MDI.

- Una ventana marco MDI tiene controladores predeterminados para los siguientes comandos de menú de ventana estándares:

    - ID_WINDOW_TILE_VERT

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- Una ventana marco MDI también tiene una implementación de ID_WINDOW_NEW, que crea un nuevo marco y la vista del documento actual. Una aplicación puede invalidar estas implementaciones de comando predeterminado para personalizar el control de ventana MDI.

No use C++ **eliminar** operador para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. El `CFrameWnd` implementací `PostNcDestroy` eliminará el objeto de C++ cuando se destruye la ventana. Cuando el usuario cierra la ventana de marco, el valor predeterminado `OnClose` controlador llamará `DestroyWindow`.

Para obtener más información sobre `CMDIFrameWnd`, consulte [marco Windows](../../mfc/frame-windows.md).

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

Llame a la `Create` o `LoadFrame` función miembro para crear la ventana de marco MDI visible.

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

*lpCreateStruct*<br/>
Un puntero largo a un [CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) estructura.

*pWindowMenu*<br/>
Un puntero en el menú emergente de la ventana.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro debe llamarse si invalida el `OnCreate` directamente la función miembro.

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

*pClass*<br/>
La clase de tiempo de ejecución de la ventana secundaria que se va a crear.

*nResource*<br/>
El identificador de recursos compartidos asociados con la ventana secundaria.

*hMenu*<br/>
Menú de la ventana secundaria.

*hAccel*<br/>
Acelerador de la ventana secundaria.

### <a name="remarks"></a>Comentarios

Utilice esta función para crear ventanas de una ventana de marco MDI secundarias.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup

Llame a esta función miembro para obtener un identificador para el menú emergente actual denominado "Window" (el menú emergente con los elementos de menú para la administración de ventanas MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parámetros

*hMenuBar*<br/>
La barra de menú actual.

### <a name="return-value"></a>Valor devuelto

El menú emergente de ventana si existe; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

La implementación predeterminada busca un menú emergente que contiene comandos estándares del menú Ventana como ID_WINDOW_NEW y ID_WINDOW_TILE_HORZ.

Reemplace esta función miembro si tiene un menú de ventana que no utiliza los identificadores de comando de menú estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate

Activa una ventana secundaria MDI diferentes.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parámetros

*pWndActivate*<br/>
Apunta a la ventana secundaria MDI en activarse.

### <a name="remarks"></a>Comentarios

Esta función miembro envía el [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) mensaje tanto a la ventana secundaria que se va a activar la ventana secundaria que se está desactivando.

Este es el mismo mensaje que se envía si el usuario cambia el foco a una ventana secundaria MDI utilizando el mouse o teclado.

> [!NOTE]
>  Una ventana secundaria MDI se activa independientemente de la ventana de marco MDI. Cuando el marco se activa, se envía la ventana secundaria que se activó por última vez una [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) mensaje para dibujar un marco de ventana activa y barra de título, pero no recibe otro mensaje WM_MDIACTIVATE.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade

Organiza todas las ventanas secundarias MDI en un formato en cascada.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parámetros

*nType*<br/>
Especifica una marca en cascada. Se puede especificar sólo el siguiente indicador: MDITILE_SKIPDISABLED, lo que impide deshabilitados ventanas secundarias MDI se organizan en cascada.

### <a name="remarks"></a>Comentarios

La primera versión de `MDICascade`, sin parámetros, todas las ventanas secundarias MDI, incluidos deshabilitado las en cascada. La segunda versión de ellas, opcionalmente, ventanas en cascada deshabilitado MDI secundarias no si especificar MDITILE_SKIPDISABLED para el *nLas* parámetro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive

Recupera la actual ventana secundaria MDI activa, junto con una marca que indica si se maximiza la ventana secundaria.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parámetros

*pbMaximized*<br/>
Un puntero a un valor devuelto BOOL. Establece en TRUE si la devolución, si la ventana está maximizada; en caso contrario, FALSE.

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

Maximiza la ventana MDI secundaria especificada.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntos a maximizar la ventana.

### <a name="remarks"></a>Comentarios

Cuando se maximiza una ventana secundaria, Windows cambia el tamaño a fin de hacer su área de cliente de rellenar la ventana del cliente. Windows coloca el menú ventana secundaria del Control en la barra de menús del marco para que el usuario pueda restaurar o cerrar la ventana secundaria. También se agrega el título de la ventana secundaria en el título de ventana de marco.

Si otra ventana secundaria MDI se activa cuando se maximiza la ventana secundaria MDI activa actualmente, Windows restaura a los secundarios activos actualmente y maximiza la ventana secundaria recientemente activados.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext

Activa la ventana secundaria inmediatamente detrás de la ventana secundaria actualmente activa y coloca la ventana secundaria activa actualmente detrás de todas las demás ventanas secundarias.

```
void MDINext();
```

### <a name="remarks"></a>Comentarios

Si se maximiza la ventana secundaria MDI activa actualmente, la función miembro restaura a los secundarios activos actualmente y maximiza al elemento secundario recién creado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev

Activa la ventana secundaria anterior y coloca la ventana secundaria actualmente activa inmediatamente detrás de él.

```
void MDIPrev();
```

### <a name="remarks"></a>Comentarios

Si se maximiza la ventana secundaria MDI activa actualmente, la función miembro restaura a los secundarios activos actualmente y maximiza al elemento secundario recién creado.

##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore

Restaura una ventana secundaria MDI de tamaño maximizado o minimizado.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
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

*pFrameMenu*<br/>
Especifica el menú del nuevo menú de la ventana de marco. Si es NULL, no se cambia el menú.

*pWindowMenu*<br/>
Especifica el menú del menú emergente de ventana nueva. Si es NULL, no se cambia el menú.

### <a name="return-value"></a>Valor devuelto

Un puntero al menú de ventana de marco reemplazado por este mensaje. El puntero puede ser temporal y no se debe almacenar para su uso posterior.

### <a name="remarks"></a>Comentarios

Después de llamar a `MDISetMenu`, una aplicación debe llamar a la [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) función miembro de `CWnd` para actualizar la barra de menús.

Si esta llamada reemplaza el menú emergente de la ventana, elementos de menú de ventana secundaria MDI se quitan desde el menú Ventana anterior y se agrega al menú emergente de ventana nueva.

Si se maximiza una ventana secundaria MDI y esta llamada reemplaza al menú de ventana de marco MDI, los controles de menú y la restauración de Control se quitan en el menú de la ventana de marco anterior y se agregan al menú nuevo.

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

*nType*<br/>
Especifica una marca de disposición en mosaico. Este parámetro puede ser cualquiera de las marcas siguientes:

- Ventanas secundarias de MDI de MDITILE_HORIZONTAL iconos para que una ventana aparezca por encima de otro.

- Evita que MDITILE_SKIPDISABLED había deshabilitado ventanas secundarias MDI desde que se coloca en mosaico.

- Ventanas secundarias de MDI de MDITILE_VERTICAL iconos para que una ventana aparezca junto a otro.

### <a name="remarks"></a>Comentarios

La primera versión de `MDITile`, sin parámetros, los iconos de las ventanas verticalmente en las versiones 3.1 y posteriores de Windows. La segunda versión muestra ventanas en mosaico vertical u horizontalmente, dependiendo del valor de la *nLas* parámetro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Vea también

[Ejemplo MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo SNAPVW de MFC](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
