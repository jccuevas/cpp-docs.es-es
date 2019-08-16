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
ms.openlocfilehash: 27f4f14c9e93091728e256c890dcffee26a43de4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502994"
---
# <a name="cpalette-class"></a>Clase CPalette

Encapsula una paleta de colores de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|Construye un `CPalette` objeto sin ninguna paleta de Windows asociada. Debe inicializar el `CPalette` objeto con una de las funciones miembro de inicialización antes de que se pueda usar.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Reemplaza las entradas de la paleta lógica identificadas `CPalette` por el objeto. La aplicación no tiene que actualizar su área cliente, ya que Windows asigna las nuevas entradas a la paleta del sistema inmediatamente.|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Crea una paleta de semitonos para el contexto de dispositivo y la `CPalette` adjunta al objeto.|
|[CPalette::CreatePalette](#createpalette)|Crea una paleta de colores de Windows y la `CPalette` adjunta al objeto.|
|[CPalette::FromHandle](#fromhandle)|Devuelve un puntero a un `CPalette` objeto cuando se proporciona un identificador a un objeto de la paleta de Windows.|
|[CPalette::GetEntryCount](#getentrycount)|Recupera el número de entradas de la paleta en una paleta lógica.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Devuelve el índice de la entrada en la paleta lógica que más se aproxime a un valor de color.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Recupera un intervalo de entradas de la paleta en una paleta lógica.|
|[CPalette::ResizePalette](#resizepalette)|Cambia el tamaño de la paleta lógica especificada por el `CPalette` objeto al número de entradas especificado.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Establece marcas y valores de color RGB en un intervalo de entradas de una paleta lógica.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPalette:: Operator HPALETTE](#operator_hpalette)|Devuelve el HPALETTE asociado a `CPalette`.|

## <a name="remarks"></a>Comentarios

Una paleta proporciona una interfaz entre una aplicación y un dispositivo de salida de color (por ejemplo, un dispositivo de pantalla). La interfaz permite que la aplicación saque el máximo partido de las capacidades de color del dispositivo de salida sin interferir gravemente con los colores mostrados por otras aplicaciones. Windows usa la paleta lógica de la aplicación (una lista de colores necesarios) y la paleta del sistema (que define los colores disponibles) para determinar los colores utilizados.

Un `CPalette` objeto proporciona funciones miembro para manipular la paleta a la que hace referencia el objeto. Construya un `CPalette` objeto y use sus funciones miembro para crear la paleta real, un objeto de interfaz de dispositivo gráfico (GDI) y para manipular sus entradas y otras propiedades.

Para obtener más información sobre `CPalette`el uso de, vea [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="animatepalette"></a>  CPalette::AnimatePalette

Reemplaza las entradas de la paleta lógica asociada al `CPalette` objeto.

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
Especifica el número de entradas de la paleta que se va a animar.

*lpPaletteColors*<br/>
Apunta al primer miembro de una matriz de estructuras [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) para reemplazar las entradas de la paleta identificadas por *nStartIndex* y *nNumEntries*.

### <a name="remarks"></a>Comentarios

Cuando una aplicación llama `AnimatePalette`a, no tiene que actualizar su área cliente, ya que Windows asigna las nuevas entradas a la paleta del sistema inmediatamente.

La `AnimatePalette` función solo cambiará las entradas con la marca PC_RESERVED establecida en el `palPaletteEntry` miembro correspondiente de la estructura [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) que está asociada al `CPalette` objeto. Vea LOGPALETTE en el Windows SDK para obtener más información sobre esta estructura.

##  <a name="cpalette"></a>  CPalette::CPalette

Construye un objeto `CPalette`.

```
CPalette();
```

### <a name="remarks"></a>Comentarios

El objeto no tiene ninguna paleta adjunta hasta que `CreatePalette` llame a para adjuntar uno.

##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette

Crea una paleta de semitonos para el contexto del dispositivo.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Identifica el contexto del dispositivo.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Una aplicación debe crear una paleta de semitonos cuando el modo de ajuste de un contexto de dispositivo se establece en semitonos. La paleta de semitono lógica devuelta por la función miembro [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) debería seleccionarse y realizarse en el contexto del dispositivo antes de que se llame a la función [CDC:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) o [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) .

Vea el Windows SDK para obtener más información `CreateHalftonePalette` acerca `StretchDIBits`de y.

##  <a name="createpalette"></a>  CPalette::CreatePalette

Inicializa un `CPalette` objeto creando una paleta de colores lógica de Windows y adjuntarlo `CPalette` al objeto.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parámetros

*lpLogPalette*<br/>
Apunta a una estructura [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) que contiene información sobre los colores de la paleta lógica.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Vea el Windows SDK para obtener más información sobre `LOGPALETTE` la estructura.

##  <a name="fromhandle"></a>  CPalette::FromHandle

Devuelve un puntero a un `CPalette` objeto cuando se proporciona un identificador a un objeto de la paleta de Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parámetros

*hPalette*<br/>
Identificador de una paleta de colores de GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CPalette` objeto si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si un `CPalette` objeto todavía no está asociado a la paleta de Windows, se `CPalette` crea y se adjunta un objeto temporal. Este objeto `CPalette` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos gráficos temporales. En otras palabras, el objeto temporal solo es válido durante el procesamiento de un mensaje de ventana.

##  <a name="getentrycount"></a>  CPalette::GetEntryCount

Llame a esta función miembro para recuperar el número de entradas de una paleta lógica determinada.

```
int GetEntryCount();
```

### <a name="return-value"></a>Valor devuelto

Número de entradas en una paleta lógica.

##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex

Devuelve el índice de la entrada en la paleta lógica que más se aproxime al valor de color especificado.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parámetros

*crColor*<br/>
Especifica el color con el que debe coincidir.

### <a name="return-value"></a>Valor devuelto

Índice de una entrada en una paleta lógica. La entrada contiene el color que más casi coincide con el color especificado.

##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries

Recupera un intervalo de entradas de la paleta en una paleta lógica.

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
Especifica el número de entradas de la paleta lógica que se va a recuperar.

*lpPaletteColors*<br/>
Apunta a una matriz de estructuras de datos [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) para recibir las entradas de la paleta. La matriz debe contener al menos tantas estructuras de datos especificadas por *nNumEntries*.

### <a name="return-value"></a>Valor devuelto

Número de entradas recuperadas de la paleta lógica; 0 si se produjo un error en la función.

##  <a name="operator_hpalette"></a>CPalette:: Operator HPALETTE

Utilice este operador para obtener el identificador de GDI de Windows asociado `CPalette` del objeto.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, identificador del objeto GDI de Windows representado por el `CPalette` objeto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este operador es un operador de conversión, que admite el uso directo de un objeto HPALETTE.

Para obtener más información sobre el uso de objetos gráficos, vea el artículo [objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

##  <a name="resizepalette"></a>  CPalette::ResizePalette

Cambia el tamaño de la paleta lógica asociada al `CPalette` objeto al número de entradas especificado por *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parámetros

*nNumEntries*<br/>
Especifica el número de entradas de la paleta una vez que se ha cambiado el tamaño.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha cambiado el tamaño de la paleta correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si una aplicación llama `ResizePalette` a para reducir el tamaño de la paleta, las entradas que permanecen en la paleta cuyo tamaño se ha cambiado no cambian. Si la aplicación llama `ResizePalette` a para ampliar la paleta, las entradas adicionales de la paleta se establecen en negro (los valores rojo, verde y azul son 0) y las marcas de todas las entradas adicionales se establecen en 0.

Para obtener más información sobre la API `ResizePalette`de Windows, consulte [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) en el Windows SDK.

##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries

Establece marcas y valores de color RGB en un intervalo de entradas de una paleta lógica.

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
Especifica el número de entradas de la paleta lógica que se va a establecer.

*lpPaletteColors*<br/>
Apunta a una matriz de estructuras de datos [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) para recibir las entradas de la paleta. La matriz debe contener al menos tantas estructuras de datos especificadas por *nNumEntries*.

### <a name="return-value"></a>Valor devuelto

Número de entradas establecidas en la paleta lógica; 0 si se produjo un error en la función.

### <a name="remarks"></a>Comentarios

Si la paleta lógica está seleccionada en un contexto de dispositivo cuando la aplicación `SetPaletteEntries`llama a, los cambios no surtirán efecto hasta que la aplicación llame a [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Para obtener más información, vea [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) en el Windows SDK.

## <a name="see-also"></a>Vea también

[DIBLOOK de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
