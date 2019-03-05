---
title: CBitmapButton (clase)
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: c800b40fcf2bb3008b35614390e4aafcb43a54f5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296766"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton (clase)

Crea controles de botón de comando etiquetados con imágenes de mapa de bits en lugar de texto.

## <a name="syntax"></a>Sintaxis

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Construye un objeto `CBitmapButton`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|Asocia un botón en un cuadro de diálogo con un objeto de la `CBitmapButton` (clase), carga el bitmap(s) por su nombre y cambia el tamaño del botón para ajustar el mapa de bits.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicializa el objeto cargando uno o varios recursos de mapa de bits con nombre de archivo de recursos de la aplicación y asociar los mapas de bits para el objeto.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Cambia el tamaño del botón para acomodar el mapa de bits.|

## <a name="remarks"></a>Comentarios

`CBitmapButton` los objetos contienen hasta cuatro mapas de bits que contienen imágenes para los distintos Estados que puede suponer un botón: (normal o), hacia abajo (o seleccionado), centrado y deshabilitado. El primer mapa de bits es necesario; los demás son opcionales.

Imágenes de los botones de mapa de bits incluyen el borde alrededor de la imagen, así como la propia imagen. El borde normalmente desempeña un papel importante en que muestra el estado del botón. Por ejemplo, el mapa de bits para el estado del foco normalmente es similar a uno para el estado de funcionamiento, pero con un margen de rectángulo discontinua desde el borde o una línea sólida gruesa en el borde. El mapa de bits para deshabilitado estado normalmente se parece a uno para el estado de funcionamiento, pero tiene un contraste inferior (por ejemplo, una selección de menú atenuados o no accesible).

Estos mapas de bits pueden ser de cualquier tamaño, pero se tratan como si fueran el mismo tamaño que el mapa de bits para el estado presionado.

Diversas aplicaciones exigen distintas combinaciones de imágenes de mapa de bits:

|Arriba|Verticalmente|Con foco|Deshabilitado|Administración de|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||Botón sin estilo WS_TABSTOP|
|×|×|×|×|Botón de cuadro de diálogo con todos los Estados|
|×|×|×||Botón de cuadro de diálogo con estilo WS_TABSTOP|

Al crear un control de botón de mapa de bits, establezca el estilo BS_OWNERDRAW para especificar que el botón está dibujado por el propietario. Esto hace que Windows enviar los mensajes WM_MEASUREITEM y WM_DRAWITEM para el botón; el marco de trabajo procesa estos mensajes y administra la apariencia del botón por usted.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Para crear un control de botón de mapa de bits en el área de cliente de una ventana

1. Creación de una a cuatro imágenes de mapa de bits para el botón.

1. Construir la [CBitmapButton](#cbitmapbutton) objeto.

1. Llame a la [crear](../../mfc/reference/cbutton-class.md#create) función para crear el control de botón de Windows y adjuntarlo a la `CBitmapButton` objeto.

1. Llame a la [LoadBitmaps](#loadbitmaps) función miembro para cargar los recursos de mapa de bits después de que se construye el botón de mapa de bits.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Para incluir un control de botón de mapa de bits en un cuadro de diálogo

1. Creación de una a cuatro imágenes de mapa de bits para el botón.

1. Crear una plantilla de cuadro de diálogo con un botón dibujado por el propietario colocado donde desee que el botón de mapa de bits. No importa el tamaño del botón en la plantilla.

1. Establece el título del botón en un valor como "MYIMAGE" y definir un símbolo para el botón como IDC_MYIMAGE.

1. En el script de recursos de la aplicación, asigne a cada una de las imágenes creadas para el botón de un identificador construido anexando una de las letras "U", "D", "F","o"X"(por arriba, abajo, centrado y deshabilitado) a la cadena utilizada para el título del botón en el paso 3. Para el título del botón "MYIMAGE", por ejemplo, los identificadores sería "MYIMAGEU", "MYIMAGED", "MYIMAGEF" y "MYIMAGEX." Le **debe** especificar el identificador de los mapas de bits entre comillas dobles. De lo contrario, el editor de recursos le asignará a un número entero para el recurso y MFC se producirá un error al cargar la imagen.

1. En la clase de cuadro de diálogo de la aplicación (derivado de `CDialog`), agregue un `CBitmapButton` objeto miembro.

1. En el `CDialog` del objeto [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) rutinaria, llamada la `CBitmapButton` del objeto [AutoLoad](#autoload) funcione, utilizando como parámetros el identificador de control del botón y el `CDialog` objeto **esto** puntero.

Si desea controlar los mensajes de notificación de Windows, como BN_CLICKED, enviado por un control de botón de mapa de bits a su elemento primario (normalmente una clase derivada de `CDialog`), agregar a la `CDialog`-objeto derivado de un miembro de mapa de mensajes de entrada y el controlador de mensajes función para cada mensaje. Las notificaciones enviadas por un `CBitmapButton` objeto son los mismos que los enviados por un [CButton](../../mfc/reference/cbutton-class.md) objeto.

La clase [CToolBar](../../mfc/reference/ctoolbar-class.md) adopta un enfoque diferente para los botones de mapa de bits.

Para obtener más información sobre `CBitmapButton`, consulte [controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

##  <a name="autoload"></a>  CBitmapButton::AutoLoad

Asocia un botón en un cuadro de diálogo con un objeto de la `CBitmapButton` (clase), carga el bitmap(s) por su nombre y cambia el tamaño del botón para ajustar el mapa de bits.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del control. del botón

*pParent*<br/>
Puntero al objeto que posee el botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use el `AutoLoad` esa función para inicializar un botón dibujado por el propietario de un cuadro de diálogo como un botón de mapa de bits. Instrucciones para usar esta función se encuentran en la sección Comentarios para el `CBitmapButton` clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

##  <a name="cbitmapbutton"></a>  CBitmapButton::CBitmapButton

Crea un objeto `CBitmapButton`.

```
CBitmapButton();
```

### <a name="remarks"></a>Comentarios

Después de crear el C++ `CBitmapButton` de objeto, llame a [CButton::Create](../../mfc/reference/cbutton-class.md#create) para crear el control de botón de Windows y adjuntarlo a la `CBitmapButton` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

##  <a name="loadbitmaps"></a>  CBitmapButton::LoadBitmaps

Use esta función cuando desea cargar imágenes de mapa de bits identificadas por sus nombres de recursos o los números de identificación, o cuando no puede usar el `AutoLoad` funciona porque, por ejemplo, va a crear un botón de mapa de bits que no forma parte de un cuadro de diálogo.

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>Parámetros

*lpszBitmapResource*<br/>
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para normal de un botón mapa de bits o "seguridad" del estado. Obligatorio.

*lpszBitmapResourceSel*<br/>
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits de un botón de mapa de bits está seleccionado o "down" estado. Puede ser NULL.

*lpszBitmapResourceFocus*<br/>
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para un botón de mapa de bits habían centrado estado. Puede ser NULL.

*lpszBitmapResourceDisabled*<br/>
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits en el botón de mapa de bits de estado deshabilitado. Puede ser NULL.

*nIDBitmapResource*<br/>
Especifica el número de Id. de recurso del recurso de mapa de bits para normal de un botón mapa de bits o "seguridad" del estado. Obligatorio.

*nIDBitmapResourceSel*<br/>
Especifica el número de Id. de recurso del recurso de mapa de bits para la que ha seleccionado un botón de mapa de bits o "down" estado. Puede ser 0.

*nIDBitmapResourceFocus*<br/>
Especifica el número de Id. de recurso del recurso de mapa de bits para el estado de foco del botón de un mapa de bits. Puede ser 0.

*nIDBitmapResourceDisabled*<br/>
Especifica el número de Id. de recurso del recurso de mapa de bits para el estado deshabilitado del botón de un mapa de bits. Puede ser 0.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

##  <a name="sizetocontent"></a>  CBitmapButton::SizeToContent

Llame a esta función para cambiar el tamaño de un botón de mapa de bits para el tamaño del mapa de bits.

```
void SizeToContent();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CTRLTEST](../../visual-cpp-samples.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
