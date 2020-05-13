---
title: Clase CMiniFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: e9b91161f4207f4d2215d8777beade93617ddfac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319816"
---
# <a name="cminiframewnd-class"></a>Clase CMiniFrameWnd

Representa una ventana de marco de altura media, como las que se suelen ver alrededor de las barras de herramientas flotantes.

## <a name="syntax"></a>Sintaxis

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Construye un objeto `CMiniFrameWnd`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMiniFrameWnd::Create](#create)|Crea `CMiniFrameWnd` un objeto después de la construcción.|
|[CMiniFrameWnd::CreateEx](#createex)|Crea `CMiniFrameWnd` un objeto (con opciones adicionales) después de la construcción.|

## <a name="remarks"></a>Observaciones

Estas ventanas de marco pequeño se comportan como ventanas de marco normales, excepto que no tienen botones o menús de minimización/maximización y solo tienes que hacer un solo clic en el menú del sistema para descartarlas.

Para utilizar `CMiniFrameWnd` un objeto, defina primero el objeto. A continuación, llame a la [create](#create) función miembro para mostrar la ventana de marco pequeño.

Para obtener más información `CMiniFrameWnd` sobre cómo utilizar objetos, consulte el artículo [Acoplar y barras](../../mfc/docking-and-floating-toolbars.md)de herramientas flotantes .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

Construye un `CMiniFrameWnd` objeto, pero no crea la ventana.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Observaciones

Para crear la ventana, llame a [CMiniFrameWnd::Create](#create).

## <a name="cminiframewndcreate"></a><a name="create"></a>CMiniFrameWnd::Create

Crea la ventana de marco pequeño de `CMiniFrameWnd` Windows y la adjunta al objeto.

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parámetros

*lpClassName*<br/>
Apunta a una cadena de caracteres terminada en null que nombra la clase Windows. El nombre de clase puede ser cualquier nombre registrado con la función global [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) Si NULL, el marco de trabajo registrará la clase de ventana. MFC proporciona a la clase predeterminada los siguientes estilos y atributos:

- Establece el CS_DBLCLKS de bits de estilo, que envía mensajes de doble clic al procedimiento de ventana cuando el usuario hace doble clic en el mouse.

- Establece bits de estilo CS_HREDRAW y CS_VREDRAW, que dirigen el contenido del área de cliente que se va a volver a dibujar cuando la ventana cambia de tamaño.

- Establece el cursor de clase en el IDC_ARROW estándar de Windows.

- Establece el pincel de fondo de clase en NULL, por lo que la ventana no borrará su fondo.

- Establece el icono de clase en el icono de logotipo de Windows estándar con bandera ondulante.

- Establece la ventana en el tamaño y la posición predeterminados, como se indica en Windows.

*lpWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.

*dwStyle*<br/>
Especifica los atributos de estilo de ventana. Estos pueden incluir estilos de ventana estándar y uno o más de los siguientes estilos especiales:

- MFS_MOVEFRAME Permite mover la ventana de marco pequeño haciendo clic en cualquier borde de la ventana, no solo en el título.

- MFS_4THICKFRAME Deshabilita el cambio de tamaño de la ventana de marco pequeño.

- MFS_SYNCACTIVE Sincroniza la activación de la ventana de marco pequeño con la activación de su ventana principal.

- MFS_THICKFRAME Permite que la ventana de marco pequeño sea tan pequeña como el contenido del área de cliente lo permita.

- MFS_BLOCKSYSMENU Deshabilita el acceso al menú del sistema y al menú de control y los convierte en parte del título (barra de título).

Consulte [CWnd::Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los posibles valores de estilo de ventana. La combinación típica utilizada para las ventanas de marco pequeño se WS_POPUP&#124;WS_CAPTION WS_SYSMENU de&#124;.

*Rect*<br/>
Estructura `RECT` que especifica las dimensiones deseadas de la ventana.

*pParentWnd*<br/>
Apunta a la ventana padre. Use NULL para las ventanas de nivel superior.

*nID*<br/>
Si la ventana de marco pequeño se crea como una ventana secundaria, este es el identificador del control secundario; de lo contrario 0.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

`Create`inicializa el nombre de clase y el nombre de la ventana de la ventana y registra los valores predeterminados para su estilo y elemento primario.

## <a name="cminiframewndcreateex"></a><a name="createex"></a>CMiniFrameWnd::CreateEx

Crea un objeto `CMiniFrameWnd` .

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido `CMiniFrameWnd` del que se está creando. Aplique cualquiera de los [estilos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) de ventana extendida a la ventana.

*lpClassName*<br/>
Apunta a una cadena de caracteres terminada en null que nombra la clase Windows (una estructura [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) El nombre de clase puede ser cualquier nombre registrado con la función [global AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) o cualquiera de los nombres de clase de control predefinidos. No debe ser NULL.

*lpWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.

*dwStyle*<br/>
Especifica los atributos de estilo de ventana. Consulte [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana y [CWnd::Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los valores posibles.

*Rect*<br/>
El tamaño y la posición de la ventana, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Apunta al objeto de ventana principal.

*nID*<br/>
Identificador de la ventana secundaria.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Los `CreateEx` parámetros especifican el WNDCLASS, el estilo de ventana y (opcionalmente) la posición inicial y el tamaño de la ventana. `CreateEx`también especifica el elemento primario de la ventana (si existe) y el identificador.

Cuando `CreateEx` se ejecuta, Windows envía los mensajes [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) a la ventana.

Para ampliar el control de mensajes `CMiniFrameWnd`predeterminado, derive una clase de , agregue un mapa de mensajes a la nueva clase y proporcione funciones miembro para los mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Invalide `On` *más* controladores de mensajes de mensaje para agregar más funcionalidad a la clase derivada.

Si se da el estilo de WS_VISIBLE, Windows envía a la ventana todos los mensajes necesarios para activar y mostrar la ventana. Si el estilo de ventana especifica una barra de título, el título de la ventana al que apunta el parámetro *lpszWindowName* se muestra en la barra de título.

El parámetro *dwStyle* puede ser cualquier combinación de estilos de [ventana.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

Ya no se admiten las ventanas de la caja de herramientas Paleta de estilo antiguo. El estilo antiguo, que no tenía un botón de cierre "X", se admitía al ejecutar una aplicación MFC en versiones anteriores de Windows, pero ya no se admite en Visual C+.NET. Ahora solo se admite el nuevo estilo de WS_EX_TOOLWINDOW; para obtener una descripción de este estilo, consulte [Estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Consulte también

[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)
