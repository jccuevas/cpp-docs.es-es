---
title: Clase CPalette
ms.date: 11/04/2016
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
ms.openlocfilehash: 83cd125fa7ab64aa39c606bc048022400d158e72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374759"
---
# <a name="cpalette-class"></a>Clase CPalette

Encapsula una paleta de colores de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|Construye un `CPalette` objeto sin paleta de Windows adjunta. Debe inicializar `CPalette` el objeto con una de las funciones miembro de inicialización antes de que se pueda utilizar.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Reemplaza las entradas de la paleta `CPalette` lógica identificada por el objeto. La aplicación no tiene que actualizar su área de cliente, ya que Windows asigna las nuevas entradas a la paleta del sistema inmediatamente.|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Crea una paleta de medios tonos para el `CPalette` contexto del dispositivo y la adjunta al objeto.|
|[CPalette::CreatePalette](#createpalette)|Crea una paleta de colores `CPalette` de Windows y la adjunta al objeto.|
|[CPalette::FromHandle](#fromhandle)|Devuelve un puntero `CPalette` a un objeto cuando se le da un identificador a un objeto de paleta de Windows.|
|[CPalette::GetEntryCount](#getentrycount)|Recupera el número de entradas de paleta en una paleta lógica.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Devuelve el índice de la entrada en la paleta lógica que coincide más estrechamente con un valor de color.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Recupera un rango de entradas de paleta en una paleta lógica.|
|[CPalette::ResizePalette](#resizepalette)|Cambia el tamaño de la paleta `CPalette` lógica especificada por el objeto al número especificado de entradas.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Establece valores de color RGB y indicadores en un rango de entradas en una paleta lógica.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPalette::operador HPALETTE](#operator_hpalette)|Devuelve el HPALETTE `CPalette`adjunto al archivo .|

## <a name="remarks"></a>Observaciones

Una paleta proporciona una interfaz entre una aplicación y un dispositivo de salida de color (por ejemplo, un dispositivo de visualización). La interfaz permite a la aplicación aprovechar al máximo las capacidades de color del dispositivo de salida sin interferir severamente con los colores mostrados por otras aplicaciones. Windows utiliza la paleta lógica de la aplicación (una lista de colores necesarios) y la paleta del sistema (que define los colores disponibles) para determinar los colores utilizados.

Un `CPalette` objeto proporciona funciones miembro para manipular la paleta a la que hace referencia el objeto. Construir `CPalette` un objeto y utilizar sus funciones miembro para crear la paleta real, un objeto de interfaz de dispositivo gráfico (GDI) y para manipular sus entradas y otras propiedades.

Para obtener más `CPalette`información sobre el uso de , consulte [Objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette::AnimatePalette

Reemplaza las entradas de la paleta `CPalette` lógica asociada al objeto.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parámetros

*nStartIndex*<br/>
Especifica la primera entrada de la paleta que se va a animar.

*nNumEntries*<br/>
Especifica el número de entradas de la paleta que se van a animar.

*lpPaletteColors*<br/>
Apunta al primer miembro de una matriz de estructuras [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) para reemplazar las entradas de paleta identificadas por *nStartIndex* y *nNumEntries*.

### <a name="remarks"></a>Observaciones

Cuando una `AnimatePalette`aplicación llama , no tiene que actualizar su área de cliente, porque Windows asigna las nuevas entradas a la paleta del sistema inmediatamente.

La `AnimatePalette` función sólo modificará las entradas con `palPaletteEntry` el indicador PC_RESERVED establecido en `CPalette` el miembro correspondiente de la estructura [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) que se adjunta al objeto. Consulte LOGPALETTE en el Windows SDK para obtener más información acerca de esta estructura.

## <a name="cpalettecpalette"></a><a name="cpalette"></a>CPalette::CPalette

Construye un objeto `CPalette`.

```
CPalette();
```

### <a name="remarks"></a>Observaciones

El objeto no tiene ninguna `CreatePalette` paleta adjunta hasta que se llama para adjuntar una.

## <a name="cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette::CreateHalftonePalette

Crea una paleta de medios tonos para el contexto del dispositivo.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Identifica el contexto del dispositivo.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Una aplicación debe crear una paleta de medios tonos cuando el modo de estiramiento de un contexto de dispositivo se establece en HALFTONE. La paleta de medios tonos lógica devuelta por la función miembro [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) debe seleccionarse y realizarse en el contexto del dispositivo antes de llamar a la función [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) o [StretchDIBits.](/windows/win32/api/wingdi/nf-wingdi-stretchdibits)

Consulte el Windows SDK `CreateHalftonePalette` para `StretchDIBits`obtener más información sobre y .

## <a name="cpalettecreatepalette"></a><a name="createpalette"></a>CPalette::CreatePalette

Inicializa un `CPalette` objeto creando una paleta de colores `CPalette` lógica de Windows y adjuntándolo al objeto.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parámetros

*lpLogPalette*<br/>
Apunta a una estructura [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) que contiene información sobre los colores de la paleta lógica.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Consulte el Windows SDK para `LOGPALETTE` obtener más información acerca de la estructura.

## <a name="cpalettefromhandle"></a><a name="fromhandle"></a>CPalette::FromHandle

Devuelve un puntero `CPalette` a un objeto cuando se le da un identificador a un objeto de paleta de Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parámetros

*hPalette*<br/>
Identificador de una paleta de colores GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero `CPalette` a un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si `CPalette` un objeto aún no está asociado `CPalette` a la paleta de Windows, se crea y adjunta un objeto temporal. Este `CPalette` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos gráficos temporales. En otras palabras, el objeto temporal sólo es válido durante el procesamiento de un mensaje de ventana.

## <a name="cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette::GetEntryCount

Llame a esta función miembro para recuperar el número de entradas en una paleta lógica determinada.

```
int GetEntryCount();
```

### <a name="return-value"></a>Valor devuelto

Número de entradas en una paleta lógica.

## <a name="cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex

Devuelve el índice de la entrada en la paleta lógica que coincide más estrechamente con el valor de color especificado.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parámetros

*crColor*<br/>
Especifica el color que se va a coincidir.

### <a name="return-value"></a>Valor devuelto

El índice de una entrada en una paleta lógica. La entrada contiene el color que casi coincide con el color especificado.

## <a name="cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette::GetPaletteEntries

Recupera un rango de entradas de paleta en una paleta lógica.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parámetros

*nStartIndex*<br/>
Especifica la primera entrada de la paleta lógica que se va a recuperar.

*nNumEntries*<br/>
Especifica el número de entradas en la paleta lógica que se van a recuperar.

*lpPaletteColors*<br/>
Apunta a una matriz de estructuras de datos [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) para recibir las entradas de la paleta. La matriz debe contener al menos tantas estructuras de datos como especifica *nNumEntries*.

### <a name="return-value"></a>Valor devuelto

El número de entradas recuperadas de la paleta lógica; 0 si la función ha fallado.

## <a name="cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette::operador HPALETTE

Utilice este operador para obtener el identificador `CPalette` GDI de Windows adjunto del objeto.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un identificador para `CPalette` el objeto GDI de Windows representado por el objeto; NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de conversión, que admite el uso directo de un objeto HPALETTE.

Para obtener más información sobre el uso de objetos gráficos, consulte el artículo [Objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

## <a name="cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette::ResizePalette

Cambia el tamaño de la `CPalette` paleta lógica asociada al objeto al número de entradas especificado por *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parámetros

*nNumEntries*<br/>
Especifica el número de entradas de la paleta después de cambiar su tamaño.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la paleta se redimensionó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si una `ResizePalette` aplicación llama para reducir el tamaño de la paleta, las entradas restantes en la paleta redimensionada no cambian. Si la `ResizePalette` aplicación llama para ampliar la paleta, las entradas de paleta adicionales se establecen en negro (los valores rojo, verde y azul son todos 0) y las marcas de todas las entradas adicionales se establecen en 0.

Para obtener más información `ResizePalette`sobre la API de Windows , consulte [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) en el Windows SDK.

## <a name="cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette::SetPaletteEntries

Establece valores de color RGB y indicadores en un rango de entradas en una paleta lógica.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parámetros

*nStartIndex*<br/>
Especifica la primera entrada de la paleta lógica que se va a establecer.

*nNumEntries*<br/>
Especifica el número de entradas en la paleta lógica que se va a establecer.

*lpPaletteColors*<br/>
Apunta a una matriz de estructuras de datos [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) para recibir las entradas de la paleta. La matriz debe contener al menos tantas estructuras de datos como especifica *nNumEntries*.

### <a name="return-value"></a>Valor devuelto

El número de entradas establecidas en la paleta lógica; 0 si la función ha fallado.

### <a name="remarks"></a>Observaciones

Si la paleta lógica se selecciona en `SetPaletteEntries`un contexto de dispositivo cuando llama a la aplicación , los cambios no surtirán efecto hasta que la aplicación llame a [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Para obtener más información, consulte [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
