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
ms.openlocfilehash: df21591dec1da5861125d7e9480fb9345aaad061
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752949"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton (clase)

Crea controles de botón de comando etiquetados con imágenes de mapa de bits en lugar de texto.

## <a name="syntax"></a>Sintaxis

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Construye un objeto `CBitmapButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|Asocia un botón de un cuadro `CBitmapButton` de diálogo con un objeto de la clase, carga los mapas de bits por nombre y ajusta el tamaño del botón para que se ajuste al mapa de bits.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicializa el objeto cargando uno o varios recursos de mapa de bits con nombre desde el archivo de recursos de la aplicación y adjuntando los mapas de bits al objeto.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Ajusta el tamaño del botón para acomodar el mapa de bits.|

## <a name="remarks"></a>Observaciones

`CBitmapButton`los objetos contienen hasta cuatro mapas de bits, que contienen imágenes para los diferentes estados que un botón puede asumir: arriba (o normal), abajo (o seleccionado), enfocado y deshabilitado. Solo se requiere el primer mapa de bits; los otros son opcionales.

Las imágenes de botón de mapa de bits incluyen el borde alrededor de la imagen, así como la propia imagen. El borde normalmente desempeña un papel en mostrar el estado del botón. Por ejemplo, el mapa de bits para el estado enfocado suele ser similar al del estado arriba, pero con un rectángulo discontinuo insertado desde el borde o una línea sólida gruesa en el borde. El mapa de bits para el estado deshabilitado suele parecerse al del estado arriba, pero tiene un contraste más bajo (como una selección de menú atenuada o atenuada).

Estos mapas de bits pueden ser de cualquier tamaño, pero todos se tratan como si tuvieran el mismo tamaño que el mapa de bits para el estado up.

Varias aplicaciones exigen diferentes combinaciones de imágenes de mapa de bits:

|Arriba|Bajar|Con foco|Disabled|Application|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||Botón sin estilo WS_TABSTOP|
|×|×|×|×|Botón de diálogo con todos los estados|
|×|×|×||Botón de diálogo con estilo WS_TABSTOP|

Al crear un control de botón de mapa de bits, establezca el estilo de BS_OWNERDRAW para especificar que el botón está dibujado por el propietario. Esto hace que Windows envíe los mensajes WM_MEASUREITEM y WM_DRAWITEM para el botón; el marco de trabajo controla estos mensajes y administra la apariencia del botón por usted.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Para crear un control de botón de mapa de bits en el área de cliente de una ventana

1. Cree de una a cuatro imágenes de mapa de bits para el botón.

1. Construir el [CBitmapButton](#cbitmapbutton) objeto.

1. Llame a la [función Create](../../mfc/reference/cbutton-class.md#create) para crear `CBitmapButton` el control de botón de Windows y adjuntarlo al objeto.

1. Llame a la [LoadBitmaps](#loadbitmaps) función miembro para cargar los recursos de mapa de bits después de que se construye el botón de mapa de bits.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Para incluir un control de botón de mapa de bits en un cuadro de diálogo

1. Cree de una a cuatro imágenes de mapa de bits para el botón.

1. Cree una plantilla de cuadro de diálogo con un botón de dibujo del propietario situado donde desee el botón de mapa de bits. El tamaño del botón en la plantilla no importa.

1. Establezca el título del botón en un valor como " MYIMAGE" y defina un símbolo para el botón como IDC_MYIMAGE.

1. En el script de recursos de la aplicación, asigne a cada una de las imágenes creadas para el botón un identificador construido añadiendo una de las letras "U", "D", "F" o "X" (para arriba, abajo, enfocado y deshabilitado) a la cadena utilizada para el título del botón en el paso 3. Para el título de botón "MYIMAGE", por ejemplo, los iDs serían " MYIMAGEU", " MYIMAGED", " MYIMAGEF" y " MYIMAGEX." **Debe** especificar el identificador de los mapas de bits entre comillas dobles. De lo contrario, el editor de recursos asignará un entero al recurso y MFC producirá un error al cargar la imagen.

1. En la clase de cuadro de `CDialog`diálogo `CBitmapButton` de la aplicación (derivada de ), agregue un objeto miembro.

1. En `CDialog` la rutina [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) del `CBitmapButton` objeto, llame a la función [AutoLoad](#autoload) del objeto, utilizando como parámetros el identificador de control del botón y el `CDialog` puntero **this** del objeto.

Si desea controlar los mensajes de notificación de Windows, como BN_CLICKED, enviado por un `CDialog`control de `CDialog`botón de mapa de bits a su elemento primario (normalmente una clase derivada de ), agregue al objeto derivado una entrada de mapa de mensajes y la función miembro del controlador de mensajes para cada mensaje. Las notificaciones enviadas por un `CBitmapButton` objeto son las mismas que las enviadas por un [CButton](../../mfc/reference/cbutton-class.md) objeto.

La clase [CToolBar](../../mfc/reference/ctoolbar-class.md) adopta un enfoque diferente a los botones de mapa de bits.

Para obtener `CBitmapButton`más información sobre , consulte [Controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton::AutoLoad

Asocia un botón de un cuadro `CBitmapButton` de diálogo con un objeto de la clase, carga los mapas de bits por nombre y ajusta el tamaño del botón para que se ajuste al mapa de bits.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador de control del botón.

*pParent*<br/>
Puntero al objeto que posee el botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Utilice `AutoLoad` la función para inicializar un botón de dibujo del propietario en un cuadro de diálogo como un botón de mapa de bits. Las instrucciones para utilizar esta función `CBitmapButton` se encuentran en las observaciones de la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton

Crea un objeto `CBitmapButton` .

```
CBitmapButton();
```

### <a name="remarks"></a>Observaciones

Después de crear `CBitmapButton` el objeto C++, llame a [CButton::Create](../../mfc/reference/cbutton-class.md#create) para crear el control de botón de Windows y adjuntarlo al `CBitmapButton` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps

Utilice esta función cuando desee cargar imágenes de mapa de bits `AutoLoad` identificadas por sus nombres de recursos o números de ID, o cuando no pueda utilizar la función porque, por ejemplo, está creando un botón de mapa de bits que no forma parte de un cuadro de diálogo.

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
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para el estado normal o "arriba" de un botón de mapa de bits. Necesario.

*lpszBitmapResourceSel*<br/>
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para el estado seleccionado o "abajo" de un botón de mapa de bits. Puede ser NULL.

*lpszBitmapResourceFocus*<br/>
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para el estado enfocado de un botón de mapa de bits. Puede ser NULL.

*lpszBitmapResourceDisabled*<br/>
Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para el estado deshabilitado de un botón de mapa de bits. Puede ser NULL.

*nIDBitmapResource*<br/>
Especifica el número de ID de recurso del recurso de mapa de bits para el estado normal o "arriba" de un botón de mapa de bits. Necesario.

*nIDBitmapResourceSel*<br/>
Especifica el número de ID de recurso del recurso de mapa de bits para el estado seleccionado o "abajo" de un botón de mapa de bits. Puede ser 0.

*nIDBitmapResourceFocus*<br/>
Especifica el número de id de recurso del recurso de mapa de bits para el estado enfocado de un botón de mapa de bits. Puede ser 0.

*nIDBitmapResourceDisabled*<br/>
Especifica el número de ID de recurso del recurso de mapa de bits para el estado deshabilitado de un botón de mapa de bits. Puede ser 0.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton::SizeToContent

Llame a esta función para cambiar el tamaño de un botón de mapa de bits al tamaño del mapa de bits.

```cpp
void SizeToContent();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Consulte también

[EJEMPLO de MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
