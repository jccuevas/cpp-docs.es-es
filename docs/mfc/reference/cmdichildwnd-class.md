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
ms.openlocfilehash: 0fbcb47f3148b72a3155e7c17cc913d652c70c2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370081"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd (clase)

Proporciona la funcionalidad de una ventana secundaria de la interfaz de múltiples documentos (MDI) de Windows, junto con los miembros para administrar la ventana.

## <a name="syntax"></a>Sintaxis

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Construye un objeto `CMDIChildWnd`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|Crea la ventana secundaria MDI `CMDIChildWnd` de Windows asociada al objeto.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Devuelve el marco MDI primario de la ventana de cliente MDI.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Activa esta ventana secundaria MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Destruye esta ventana secundaria MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximiza esta ventana secundaria MDI.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Restaura esta ventana secundaria MDI de tamaño maximizado o minimizado.|
|[CMDIChildWnd::SetHandles](#sethandles)|Establece los identificadores de los recursos de menú y acelerador.|

## <a name="remarks"></a>Observaciones

Una ventana secundaria MDI se parece mucho a una ventana de marco típica, excepto que la ventana secundaria MDI aparece dentro de una ventana de marco MDI en lugar de en el escritorio. Una ventana secundaria MDI no tiene una barra de menús propia, sino que comparte el menú de la ventana de marco MDI. El marco de trabajo cambia automáticamente el menú de marco MDI para representar la ventana secundaria MDI activa actualmente.

Para crear una ventana secundaria MDI útil para `CMDIChildWnd`la aplicación, derive una clase de . Agregue variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Hay tres maneras de construir una ventana secundaria MDI:

- Construirlo directamente usando `Create`.

- Construirlo directamente usando `LoadFrame`.

- Construido indirectamente a través de una plantilla de documento.

Antes de `Create` `LoadFrame`llamar o , debe construir el objeto frame-window en el montón mediante el **operador new** C++. Antes `Create` de llamar también puede registrar una clase de ventana con la función global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) para establecer el icono y los estilos de clase para el marco.

Utilice `Create` la función miembro para pasar los parámetros de creación del marco como argumentos inmediatos.

`LoadFrame`requiere menos argumentos `Create`que , y en su lugar recupera la mayoría de sus valores predeterminados de los recursos, incluidos el título, el icono, la tabla de aceleradores y el menú del marco. Para que `LoadFrame`sea accesible por , todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Cuando `CMDIChildWnd` un objeto contiene vistas y documentos, el marco de trabajo los crea indirectamente en lugar de directamente por el programador. El `CDocTemplate` objeto organiza la creación del marco, la creación de las vistas contenedoras y la conexión de las vistas al documento adecuado. Los parámetros `CDocTemplate` del `CRuntimeClass` constructor especifican las tres clases implicadas (documento, marco y vista). El `CRuntimeClass` marco de trabajo utiliza un objeto para crear dinámicamente nuevos marcos cuando lo especifica el usuario (por ejemplo, mediante el comando Nuevo archivo o el comando Ventana MDI Nuevo).

Una clase de ventana `CMDIChildWnd` de trama derivada de debe declararse con DECLARE_DYNCREATE para que el mecanismo de RUNTIME_CLASS anterior funcione correctamente.

La `CMDIChildWnd` clase hereda gran parte `CFrameWnd`de su implementación predeterminada de . Para obtener una lista detallada de estas características, consulte la descripción de la clase [CFrameWnd.](../../mfc/reference/cframewnd-class.md) La `CMDIChildWnd` clase tiene las siguientes características adicionales:

- Junto con `CMultiDocTemplate` la clase, varios `CMDIChildWnd` objetos de la misma plantilla de documento comparten el mismo menú, guardando los recursos del sistema de Windows.

- El menú de ventana secundaria MDI actualmente activo reemplaza por completo el menú de la ventana de marco MDI y el título de la ventana secundaria MDI actualmente activa se agrega al título de la ventana de marco MDI. Para obtener más ejemplos de funciones de ventana secundaria MDI que `CMDIFrameWnd` se implementan junto con una ventana de marco MDI, consulte la descripción de la clase.

No utilice el operador **de eliminación** C++ para destruir una ventana de marco. En su lugar, use `CWnd::DestroyWindow`. La `CFrameWnd` implementación de `PostNcDestroy` eliminará el objeto C++ cuando se destruya la ventana. Cuando el usuario cierra la ventana `OnClose` de `DestroyWindow`marco, el controlador predeterminado llamará a .

Para obtener `CMDIChildWnd`más información sobre , consulte [Ventanas](../../mfc/frame-windows.md)de marco .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd

Llame para `CMDIChildWnd` construir un objeto.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Observaciones

Llame `Create` para crear la ventana visible.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIChildWnd::Create](#create).

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd::Create

Llame a esta función miembro para crear una `CMDIChildWnd` ventana secundaria MDI de Windows y adjuntarlo al objeto.

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
Apunta a una cadena de caracteres terminada en null que nombra la clase Windows (una estructura [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) El nombre de clase puede ser cualquier nombre registrado con la función global [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) Debe ser NULL `CMDIChildWnd`para un estándar .

*lpszWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se utiliza como texto para la barra de título.

*dwStyle*<br/>
Especifica los atributos de [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana. Se requiere el estilo WS_CHILD.

*Rect*<br/>
Contiene el tamaño y la posición de la ventana. El `rectDefault` valor permite a Windows especificar el `CMDIChildWnd`tamaño y la posición del nuevo archivo .

*pParentWnd*<br/>
Especifica el elemento primario de la ventana. Si NULL, se utiliza la ventana principal de la aplicación.

*pContext*<br/>
Especifica un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La ventana de marco secundario MDI activa actualmente puede determinar el título de la ventana de marco principal. Esta función se desactiva desactivando el FWS_ADDTOTITLE parte de estilo de la ventana de marco secundario.

El marco de trabajo llama a esta función miembro en respuesta a un comando de usuario para crear una ventana secundaria y el marco de trabajo usa el *pContext* parámetro para conectar correctamente la ventana secundaria a la aplicación. Cuando se `Create`llama a , *pContext* puede ser NULL.

### <a name="example"></a>Ejemplo

Ejemplo 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Ejemplo

Ejemplo 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame

Llame a esta función para devolver el marco primario MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de marco primario MDI.

### <a name="remarks"></a>Observaciones

El marco devuelto es dos `CMDIChildWnd` elementos primarios quitados de y es `CMDIChildWnd` el elemento primario de la ventana de tipo MDICLIENT que administra el objeto. Llame a la [GetParent](../../mfc/reference/cwnd-class.md#getparent) `CMDIChildWnd` función miembro para devolver el `CWnd` elemento primario MDICLIENT inmediato del objeto como un puntero temporal.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd::MDIActivate

Llame a esta función miembro para activar una ventana secundaria MDI independientemente de la ventana de marco MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Observaciones

Cuando el marco se activa, también se activará la ventana secundaria que se activó por última vez.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy

Llame a esta función miembro para destruir una ventana secundaria MDI.

```
void MDIDestroy();
```

### <a name="remarks"></a>Observaciones

La función miembro quita el título de la ventana secundaria de la ventana de marco y desactiva la ventana secundaria.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize

Llame a esta función miembro para maximizar una ventana secundaria MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Observaciones

Cuando se maximiza una ventana secundaria, Windows la cambia de tamaño para que su área de cliente llene el área de cliente de la ventana de marco. Windows coloca el menú Control de la ventana secundaria en la barra de menús del marco para que el usuario pueda restaurar o cerrar la ventana secundaria y agrega el título de la ventana secundaria al título de la ventana de marco.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd::MDIRestore

Llame a esta función miembro para restaurar una ventana secundaria MDI de tamaño maximizado o minimizado.

```
void MDIRestore();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd::SetHandles

Establece los identificadores de los recursos de menú y acelerador.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parámetros

*hMenú*<br/>
El identificador de un recurso de menú.

*hAccel*<br/>
El identificador de un recurso acelerador.

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer los recursos de menú y acelerador utilizados por el objeto de ventana secundaria MDI.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[EJEMPLO de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)
