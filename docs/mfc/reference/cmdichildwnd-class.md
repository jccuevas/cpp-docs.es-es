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
ms.openlocfilehash: 13f027e68184a4869e88883ff8b8d3b123b94e3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403937"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd (clase)

Proporciona la funcionalidad de una ventana secundaria de la interfaz de múltiples documentos (MDI) de Windows, junto con los miembros para administrar la ventana.

## <a name="syntax"></a>Sintaxis

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Construye un objeto `CMDIChildWnd`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|Crea la ventana secundaria de MDI de Windows asociada con el `CMDIChildWnd` objeto.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Devuelve al elemento primario de marco MDI de la ventana de cliente MDI.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Activa esta ventana MDI secundaria.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Esta ventana MDI secundaria se destruye.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Esta ventana MDI secundaria se maximiza.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Restaura esta ventana secundaria MDI de tamaño maximizado o minimizado.|
|[CMDIChildWnd::SetHandles](#sethandles)|Establece los identificadores de recursos de menú y el acelerador.|

## <a name="remarks"></a>Comentarios

Una ventana secundaria MDI se parece mucho a una ventana marco típica, excepto en que la ventana secundaria MDI aparece dentro de una ventana marco MDI en lugar de en el escritorio. Una ventana secundaria MDI no tiene una barra de menús de su propio, pero en su lugar, comparte el menú de la ventana de marco MDI. El marco de trabajo cambia automáticamente el menú de marco MDI para representar la ventana secundaria MDI activa actualmente.

Para crear una ventana secundaria MDI útil para su aplicación, derive una clase de `CMDIChildWnd`. Agregar variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Hay tres formas de crear una ventana secundaria MDI:

- Crear directamente mediante `Create`.

- Crear directamente mediante `LoadFrame`.

- Construirla indirectamente a través de una plantilla de documento.

Antes de llamar a `Create` o `LoadFrame`, debe construir el objeto de ventana de marco en el montón mediante C++ **nuevo** operador. Antes de llamar a `Create` también se puede registrar una clase de ventana con el [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.

Use el `Create` función miembro para pasar parámetros de creación del marco de inmediatos como argumentos.

`LoadFrame` requiere menos argumentos que `Create`y recupera en su lugar, la mayoría de sus valores predeterminados de recursos, incluidos el título del marco, icono, tabla de aceleradores y menús. Para tener acceso a `LoadFrame`, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Cuando un `CMDIChildWnd` objeto contiene documentos y vistas, crea indirectamente el marco de trabajo en lugar de directamente por el programador. La `CDocTemplate` objeto organiza la creación del marco, la creación de las vistas que contienen y la conexión de las vistas para el documento adecuado. Los parámetros de la `CDocTemplate` constructor especifica el `CRuntimeClass` de las tres clases implicadas (documento, marco y ver). Un `CRuntimeClass` objeto se usa el marco de trabajo para crear de forma dinámica nuevos marcos al especificado por el usuario (por ejemplo, mediante el comando nuevo archivo o el comando nuevo de ventana MDI).

Deriva una clase de ventana de marco `CMDIChildWnd` debe declararse con DECLARE_DYNCREATE para el mecanismo RUNTIME_CLASS anterior funcione correctamente.

El `CMDIChildWnd` clase hereda gran parte de su implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte el [CFrameWnd](../../mfc/reference/cframewnd-class.md) descripción de clase. La `CMDIChildWnd` clase tiene las siguientes características adicionales:

- Junto con el `CMultiDocTemplate` (clase), varios `CMDIChildWnd` objetos desde la misma plantilla de documento comparten el mismo menú, ahorrando recursos de sistema de Windows.

- El menú de ventana de secundario MDI activo reemplaza completamente el menú de la ventana de marco MDI y se agrega el título de la ventana secundaria MDI activa actualmente al título de la ventana de marco MDI. Para obtener más ejemplos de funciones de ventana secundaria MDI que se implementan junto con una ventana marco MDI, consulte el `CMDIFrameWnd` descripción de clase.

No use C++ **eliminar** operador para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. El `CFrameWnd` implementací `PostNcDestroy` eliminará el objeto de C++ cuando se destruye la ventana. Cuando el usuario cierra la ventana de marco, el valor predeterminado `OnClose` controlador llamará `DestroyWindow`.

Para obtener más información sobre `CMDIChildWnd`, consulte [marco Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

Llamada a construir una `CMDIChildWnd` objeto.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Comentarios

Llame a `Create` para crear la ventana visible.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIChildWnd::Create](#create).

##  <a name="create"></a>  CMDIChildWnd::Create

Llame a esta función miembro para crear una ventana secundaria MDI de Windows y adjuntarlo a la `CMDIChildWnd` objeto.

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
Apunta a una cadena de caracteres terminada en null que se nombra la clase de Windows (un [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) estructura). El nombre de clase puede ser cualquier nombre registrado con el [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global. Debe ser NULL para un estándar `CMDIChildWnd`.

*lpszWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se utiliza como texto de la barra de título.

*dwStyle*<br/>
Especifica el período de [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributos. Se requiere el estilo WS_CHILD.

*rect*<br/>
Contiene el tamaño y posición de la ventana. El `rectDefault` valor permite que Windows especificar el tamaño y la posición del nuevo `CMDIChildWnd`.

*pParentWnd*<br/>
Especifica el elemento primario de la ventana. Si es NULL, se usa la ventana principal de la aplicación.

*pContext*<br/>
Especifica un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La ventana de marco de secundario MDI activa puede determinar el título de la ventana de marco principal. Esta característica está deshabilitada si se desactiva el bit de estilo FWS_ADDTOTITLE de la ventana de marco secundario.

El marco llama a esta función miembro en respuesta a un comando de usuario para crear una ventana secundaria, y el marco de trabajo usa el *pContext* parámetro conectar correctamente a la ventana secundaria a la aplicación. Cuando se llama a `Create`, *pContext* puede ser NULL.

### <a name="example"></a>Ejemplo

Ejemplo 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Ejemplo

Ejemplo 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

Llame a esta función para devolver el marco MDI primario.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de marco principal MDI.

### <a name="remarks"></a>Comentarios

El marco devuelto es dos padres quitados el `CMDIChildWnd` y es el elemento primario de la ventana de tipo MDICLIENT que administra el `CMDIChildWnd` objeto. Llame a la [GetParent](../../mfc/reference/cwnd-class.md#getparent) función miembro para devolver el `CMDIChildWnd` primario MDICLIENT inmediato del objeto como un archivo temporal `CWnd` puntero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

Llame a esta función miembro para activar una ventana secundaria MDI independientemente de la ventana de marco MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Comentarios

Cuando se activa el marco, también se activará la ventana secundaria que se activó por última vez.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

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

Cuando se maximiza una ventana secundaria, Windows cambia su tamaño para que su área de cliente ocupe el área cliente de la ventana de marco. Windows coloca el menú ventana secundaria del Control en la barra de menús del marco para que el usuario puede restaurar o cerrar la ventana secundaria y agrega el título de la ventana secundaria en el título de ventana de marco.

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

Establece los identificadores de recursos de menú y el acelerador.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
El identificador de un recurso de menú.

*hAccel*<br/>
El identificador de un recurso de aceleradores.

### <a name="remarks"></a>Comentarios

Llame a esta función para definir los recursos de menú y acelerador utilizados por el objeto de ventana secundaria MDI.

## <a name="see-also"></a>Vea también

[Ejemplo MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo SNAPVW de MFC](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)
