---
title: CMDIChildWnd (clase)
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: 09a9846cc3d242ef7d812cb31b4dcdd515d5f6ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506077"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd (clase)

Proporciona la funcionalidad de una ventana secundaria de la interfaz de múltiples documentos (MDI) de Windows, junto con los miembros para administrar la ventana.

## <a name="syntax"></a>Sintaxis

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Construye un objeto `CMDIChildWnd`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|Crea la ventana secundaria MDI de Windows asociada al `CMDIChildWnd` objeto.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Devuelve el marco MDI primario de la ventana del cliente MDI.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Activa esta ventana secundaria MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Destruye esta ventana secundaria MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximiza la ventana secundaria MDI.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Restaura esta ventana secundaria MDI de tamaño maximizado o minimizado.|
|[CMDIChildWnd::SetHandles](#sethandles)|Establece los identificadores de los recursos de menú y acelerador.|

## <a name="remarks"></a>Comentarios

Una ventana secundaria MDI tiene un aspecto muy similar al de una ventana de marco típica, excepto en que la ventana secundaria MDI aparece dentro de una ventana de marco MDI en lugar de en el escritorio. Una ventana secundaria MDI no tiene una barra de menús propia, sino que comparte el menú de la ventana de marco MDI. El marco de trabajo cambia automáticamente el menú marco MDI para representar la ventana MDI secundaria actualmente activa.

Para crear una ventana secundaria MDI útil para la aplicación, derive una clase de `CMDIChildWnd`. Agregue variables de miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Hay tres formas de crear una ventana secundaria MDI:

- Construya directamente mediante `Create`.

- Construya directamente mediante `LoadFrame`.

- Construya indirectamente a través de una plantilla de documento.

Antes de llamar `Create` a `LoadFrame`o, debe construir el objeto de ventana de marco en el montón mediante C++ el operador **New** . Antes de `Create` llamar a, también puede registrar una clase de ventana con la función global [AfxRegisterWndClass (](application-information-and-management.md#afxregisterwndclass) para establecer el icono y los estilos de clase para el marco.

Utilice la `Create` función miembro para pasar los parámetros de creación del marco como argumentos inmediatos.

`LoadFrame`requiere menos argumentos que `Create`y, en su lugar, recupera la mayoría de los valores predeterminados de los recursos, incluidos el título, el icono, la tabla de aceleradores y el menú del marco. Para que sea accesible `LoadFrame`para, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Cuando un `CMDIChildWnd` objeto contiene vistas y documentos, el marco de trabajo los crea indirectamente en lugar de hacerlo directamente por el programador. El `CDocTemplate` objeto orquesta la creación del marco, la creación de las vistas contenedoras y la conexión de las vistas al documento adecuado. Los parámetros del `CDocTemplate` constructor especifican el `CRuntimeClass` de las tres clases implicadas (documento, marco y vista). El `CRuntimeClass` marco de trabajo usa un objeto para crear dinámicamente nuevos marcos cuando lo especifica el usuario (por ejemplo, con el comando archivo nuevo o el comando nueva ventana MDI).

Una clase de ventana de marco derivada `CMDIChildWnd` de se debe declarar con DECLARE_DYNCREATE para que el mecanismo de RUNTIME_CLASS anterior funcione correctamente.

La `CMDIChildWnd` clase hereda gran parte de su implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte la descripción de la clase [CFrameWnd](../../mfc/reference/cframewnd-class.md) . La `CMDIChildWnd` clase tiene las siguientes características adicionales:

- Junto con la `CMultiDocTemplate` clase, varios `CMDIChildWnd` objetos de la misma plantilla de documento comparten el mismo menú, guardando los recursos del sistema de Windows.

- El menú de la ventana secundaria MDI actualmente activo reemplaza por completo el menú de la ventana de marco MDI y el título de la ventana MDI secundaria activa actualmente se agrega al título de la ventana de marco MDI. Para obtener más ejemplos de funciones de la ventana secundaria MDI que se implementan junto con una ventana de marco `CMDIFrameWnd` MDI, vea la descripción de la clase.

No use el C++ operador **Delete** para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. La `CFrameWnd` implementación de `PostNcDestroy` eliminará el C++ objeto cuando se destruya la ventana. Cuando el usuario cierra la ventana de marco, el controlador `OnClose` predeterminado llamará `DestroyWindow`a.

Para obtener más información `CMDIChildWnd`sobre, consulte [ventanas de marco](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

Llame a para construir `CMDIChildWnd` un objeto.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Comentarios

Llame `Create` a para crear la ventana visible.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIChildWnd:: Create](#create).

##  <a name="create"></a>  CMDIChildWnd::Create

Llame a esta función miembro para crear una ventana secundaria MDI de Windows y adjuntarla al `CMDIChildWnd` objeto.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
Apunta a una cadena de caracteres terminada en null que nombra la clase de Windows (una estructura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) ). El nombre de clase puede ser cualquier nombre registrado con la función global [AfxRegisterWndClass (](application-information-and-management.md#afxregisterwndclass) . Debe ser NULL para un estándar `CMDIChildWnd`.

*lpszWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se usa como texto para la barra de título.

*dwStyle*<br/>
Especifica los atributos de [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana. El estilo WS_CHILD es obligatorio.

*rect*<br/>
Contiene el tamaño y la posición de la ventana. El `rectDefault` valor permite que Windows especifique el tamaño y la posición de la `CMDIChildWnd`nueva.

*pParentWnd*<br/>
Especifica el elemento primario de la ventana. Si es NULL, se utiliza la ventana principal de la aplicación.

*pContext*<br/>
Especifica una estructura [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La ventana de marco secundario MDI activa actualmente puede determinar el título de la ventana de marco primario. Esta característica se deshabilita desactivando el bit de estilo FWS_ADDTOTITLE de la ventana de marco secundario.

El marco de trabajo llama a esta función miembro como respuesta a un comando de usuario para crear una ventana secundaria y el marco usa el parámetro *pContext* para conectar correctamente la ventana secundaria a la aplicación. Cuando se llama `Create`a, *pContext* puede ser null.

### <a name="example"></a>Ejemplo

Ejemplo 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Ejemplo

Ejemplo 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

Llame a esta función para devolver el marco primario MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana de marco primario MDI.

### <a name="remarks"></a>Comentarios

El marco devuelto es que se han quitado dos elementos primarios de `CMDIChildWnd` y es el elemento primario de la ventana de tipo MdiClient que administra el `CMDIChildWnd` objeto. Llame a la función miembro [GetParent](../../mfc/reference/cwnd-class.md#getparent) para devolver `CMDIChildWnd` el elemento primario MdiClient inmediato del objeto como `CWnd` un puntero temporal.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIFrameWnd:: MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

Llame a esta función miembro para activar una ventana secundaria MDI independientemente de la ventana de marco MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Comentarios

Cuando el marco se activa, la ventana secundaria que se activó por última vez también se activará.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIFrameWnd:: GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

##  <a name="mdidestroy"></a>  CMDIChildWnd::MDIDestroy

Llame a esta función miembro para destruir una ventana secundaria MDI.

```
void MDIDestroy();
```

### <a name="remarks"></a>Comentarios

La función miembro quita el título de la ventana secundaria de la ventana de marco y desactiva la ventana secundaria.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>  CMDIChildWnd::MDIMaximize

Llame a esta función miembro para maximizar una ventana secundaria MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Comentarios

Cuando una ventana secundaria está maximizada, Windows la cambia para que su área cliente rellene el área cliente de la ventana de marco. Windows coloca el menú de control de la ventana secundaria en la barra de menús del marco para que el usuario pueda restaurar o cerrar la ventana secundaria y agregue el título de la ventana secundaria al título de la ventana de marco.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>  CMDIChildWnd::MDIRestore

Llame a esta función miembro para restaurar una ventana secundaria MDI de tamaño maximizado o minimizado.

```
void MDIRestore();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>  CMDIChildWnd::SetHandles

Establece los identificadores de los recursos de menú y acelerador.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
Identificador de un recurso de menú.

*hAccel*<br/>
Identificador de un recurso de acelerador.

### <a name="remarks"></a>Comentarios

Llame a esta función para establecer los recursos de menú y acelerador utilizados por el objeto de ventana secundaria MDI.

## <a name="see-also"></a>Vea también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)
