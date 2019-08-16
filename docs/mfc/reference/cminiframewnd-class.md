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
ms.openlocfilehash: 45b4698cc70487a6c3fe1470fe27f7b5c4f95402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504599"
---
# <a name="cminiframewnd-class"></a>Clase CMiniFrameWnd

Representa una ventana de marco de altura media, como las que se suelen ver alrededor de las barras de herramientas flotantes.

## <a name="syntax"></a>Sintaxis

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Construye un objeto `CMiniFrameWnd`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMiniFrameWnd::Create](#create)|Crea un `CMiniFrameWnd` objeto después de la construcción.|
|[CMiniFrameWnd::CreateEx](#createex)|Crea un `CMiniFrameWnd` objeto (con opciones adicionales) después de la construcción.|

## <a name="remarks"></a>Comentarios

Estas ventanas de marco reducidos se comportan como las ventanas de fotogramas normales, con la excepción de que no tienen botones o botones minimizar/maximizar y solo tiene que hacer clic en el menú sistema para descartarlas.

Para usar un `CMiniFrameWnd` objeto, defina primero el objeto. A continuación, llame a la función miembro [Create](#create) para mostrar la ventana de marco reducido.

Para obtener más información sobre cómo usar `CMiniFrameWnd` objetos, vea el artículo [barras de herramientas de acoplamiento y flotantes](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd

Construye un `CMiniFrameWnd` objeto, pero no crea la ventana.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Comentarios

Para crear la ventana, llame a [CMiniFrameWnd:: Create](#create).

##  <a name="create"></a>  CMiniFrameWnd::Create

Crea la ventana de marco reducido de Windows y la `CMiniFrameWnd` adjunta al objeto.

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
Apunta a una cadena de caracteres terminada en null que nombra la clase de Windows. El nombre de clase puede ser cualquier nombre registrado con la función [AfxRegisterWndClass (](application-information-and-management.md#afxregisterwndclass) global. Si es NULL, el marco de trabajo registrará la clase de ventana. MFC proporciona a la clase predeterminada los siguientes estilos y atributos:

- Establece el bit de estilo CS_DBLCLKS, que envía mensajes de doble clic al procedimiento de ventana cuando el usuario hace doble clic en el mouse.

- Establece los bits de estilo CS_HREDRAW y CS_VREDRAW, que dirigen el contenido del área cliente para que se vuelva a dibujar cuando la ventana cambie de tamaño.

- Establece el cursor de clase en el IDC_ARROW estándar de Windows.

- Establece el pincel de fondo de clase en NULL, por lo que la ventana no borrará su fondo.

- Establece el icono de clase en el icono de logotipo de Windows estándar, con la marca ondeante.

- Establece la ventana en el tamaño y la posición predeterminados, como indica Windows.

*lpWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.

*dwStyle*<br/>
Especifica los atributos de estilo de ventana. Pueden incluir estilos de ventana estándar y uno o varios de los siguientes estilos especiales:

- MFS_MOVEFRAME permite que la ventana de marco reducido se mueva haciendo clic en cualquier borde de la ventana, no solo en el título.

- MFS_4THICKFRAME deshabilita el cambio de tamaño de la ventana de marco reducido.

- MFS_SYNCACTIVE sincroniza la activación de la ventana de marco reducido con la activación de su ventana primaria.

- MFS_THICKFRAME permite que la ventana de marco reducido tenga un tamaño tan pequeño como el contenido del área de cliente permita.

- MFS_BLOCKSYSMENU deshabilita el acceso al menú sistema y al menú control, y los convierte en parte de la leyenda (barra de título).

Vea [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los posibles valores de estilo de ventana. La combinación típica utilizada para las ventanas de marco reducido es&#124;WS_POPUP&#124;WS_CAPTION WS_SYSMENU.

*rect*<br/>
`RECT` Estructura que especifica las dimensiones deseadas de la ventana.

*pParentWnd*<br/>
Apunta a la ventana primaria. Use NULL para las ventanas de nivel superior.

*nID*<br/>
Si la ventana de marco reducido se crea como una ventana secundaria, éste es el identificador del control secundario; de lo contrario, es 0.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

`Create`Inicializa el nombre de clase y el nombre de la ventana de la ventana y registra los valores predeterminados para su estilo y elemento primario.

##  <a name="createex"></a>  CMiniFrameWnd::CreateEx

Crea un objeto `CMiniFrameWnd`.

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
Especifica el estilo extendido del `CMiniFrameWnd` que se va a crear. Aplique cualquiera de los [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) a la ventana.

*lpClassName*<br/>
Apunta a una cadena de caracteres terminada en null que nombra la clase de Windows (una estructura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) ). El nombre de clase puede ser cualquier nombre registrado con la función [AfxRegisterWndClass (](application-information-and-management.md#afxregisterwndclass) global o cualquiera de los nombres predefinidos de clase de control. No debe ser NULL.

*lpWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.

*dwStyle*<br/>
Especifica los atributos de estilo de ventana. Vea [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los valores posibles.

*rect*<br/>
Tamaño y posición de la ventana, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Apunta al objeto de ventana primario.

*nID*<br/>
Identificador de la ventana secundaria.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Los `CreateEx` parámetros especifican la WNDCLASS, el estilo de ventana y, opcionalmente, la posición inicial y el tamaño de la ventana. `CreateEx`también especifica el elemento primario de la ventana (si existe) y el identificador.

Cuando `CreateEx` se ejecuta, Windows envía los mensajes [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) a la ventana.

Para extender el control de mensajes predeterminado, derive una clase `CMiniFrameWnd`de, agregue un mapa de mensajes a la nueva clase y proporcione funciones miembro para los mensajes anteriores. Invalide `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Invalide los controladores de mensajes de `On` *mensajes* adicionales para agregar más funcionalidad a la clase derivada.

Si se proporciona el estilo WS_VISIBLE, Windows envía todos los mensajes necesarios para activar y mostrar la ventana. Si el estilo de ventana especifica una barra de título, el título de la ventana al que apunta el parámetro *lpszWindowName* se muestra en la barra de título.

El parámetro *dwStyle* puede ser cualquier combinación de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Ya no se admiten las ventanas de cuadro de herramientas de paleta de estilo antiguo. El estilo antiguo, que no tenía un botón Cerrar "X", era compatible con la ejecución de una aplicación MFC en versiones anteriores de Windows, pero ya no se admite en C++visual .net. Ahora solo se admite el nuevo estilo WS_EX_TOOLWINDOW; para obtener una descripción de este estilo, vea [estilos extendidos de ventana](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Vea también

[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)
