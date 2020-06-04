---
title: Clase CBitmap
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 9a33a6e1bea601422e043d7f2a80029c72d97e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352745"
---
# <a name="cbitmap-class"></a>Clase CBitmap

Encapsula un mapa de bits de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular el mapa de bits.

## <a name="syntax"></a>Sintaxis

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|Construye un objeto `CBitmap`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|Inicializa el objeto con un mapa de bits de memoria dependiente del dispositivo que tiene un ancho, alto y patrón de bits especificados.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicializa el objeto con un mapa de bits con el ancho, alto y `BITMAP` patrón de bits (si se especifica uno) especificado en una estructura.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializa el objeto con un mapa de bits para que sea compatible con un dispositivo especificado.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializa el objeto con un mapa de bits descartable que es compatible con un dispositivo especificado.|
|[CBitmap::FromHandle](#fromhandle)|Devuelve un puntero `CBitmap` a un objeto cuando `HBITMAP` se le da un identificador a un mapa de bits de Windows.|
|[CBitmap::GetBitmap](#getbitmap)|Rellena una `BITMAP` estructura con información sobre el mapa de bits.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copia los bits del mapa de bits especificado en el búfer especificado.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Devuelve el ancho y alto del mapa de bits. Se supone que el alto y el ancho se han establecido previamente por el [SetBitmapDimension](#setbitmapdimension) función miembro.|
|[CBitmap::LoadBitmap](#loadbitmap)|Inicializa el objeto cargando un recurso de mapa de bits con nombre desde el archivo ejecutable de la aplicación y adjuntando el mapa de bits al objeto.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Carga un mapa de bits y asigna colores a los colores actuales del sistema.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicializa el objeto cargando un mapa de bits de Windows predefinido y adjuntando el mapa de bits al objeto.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Establece los bits de un mapa de bits en los valores de bits especificados.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Asigna un ancho y un alto a un mapa de bits en unidades de 0,1 milímetros.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de `CBitmap` Windows asociado al objeto.|

## <a name="remarks"></a>Observaciones

Para usar `CBitmap` un objeto, construya el objeto, adjunte un identificador de mapa de bits con una de las funciones miembro de inicialización y, a continuación, llame a las funciones miembro del objeto.

Para obtener más información `CBitmap`sobre el uso de objetos gráficos como , consulte [Objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a>CBitmap::CBitmap

Construye un objeto `CBitmap`.

```
CBitmap();
```

### <a name="remarks"></a>Observaciones

El objeto resultante debe inicializarse con una de las funciones miembro de inicialización.

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a>CBitmap::CreateBitmap

Inicializa un mapa de bits de memoria dependiente de dispositivo que tiene el ancho, el alto y el patrón de bits especificados.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
Especifica el ancho (en píxeles) del mapa de bits.

*nAltura*<br/>
Especifica el alto (en píxeles) del mapa de bits.

*nPlanes*<br/>
Especifica el número de planos de color del mapa de bits.

*nBitcount*<br/>
Especifica el número de bits de color por píxel de la pantalla.

*lpBits*<br/>
Apunta a una matriz de bytes que contiene los valores de bits de mapa de bits iniciales. Si es NULL, el nuevo mapa de bits se deja sin inicializar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Para un mapa de bits de color, el *nPlanes* o *nBitcount* parámetro debe establecerse en 1. Si ambos parámetros se establecen en 1, `CreateBitmap` crea un mapa de bits monocromo.

Aunque un mapa de bits no se puede seleccionar directamente para un dispositivo de visualización, puede seleccionarse como el mapa de bits actual para un "contexto de dispositivo de memoria" usando [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) y copiarse en cualquier contexto de dispositivo compatible con la función [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) .

Cuando termine con el objeto `CBitmap` creado por la función `CreateBitmap` , seleccione primero el mapa de bits fuera del contexto del dispositivo y elimine luego el objeto `CBitmap` .

Para obtener más información, `bmBits` consulte la `BITMAP` descripción del campo en la estructura. La estructura [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) se describe en la función miembro [CBitmap::CreateBitmapIndirect](#createbitmapindirect) .

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect

Inicializa un mapa de bits que tiene el ancho, alto y el patrón de bits (si se especifica uno) dado en la estructura a la que apunta *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parámetros

*lpBitmap*<br/>
Apunta a una estructura [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) que contiene información sobre el mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Aunque un mapa de bits no se puede seleccionar directamente para un dispositivo de visualización, se puede seleccionar como el mapa de bits actual para un contexto de dispositivo de memoria mediante [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) y copiar en cualquier contexto de dispositivo compatible mediante la función [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) o [CDC::StretchBlt.](../../mfc/reference/cdc-class.md#stretchblt) (La función [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) puede copiar el mapa de bits del pincel actual directamente en el contexto del dispositivo de visualización.)

Si `BITMAP` la estructura señalada por el parámetro *lpBitmap* se ha rellenado mediante la `GetObject` función, no se especifican los bits del mapa de bits y el mapa de bits no se inicializa. Para inicializar el mapa de bits, una aplicación puede utilizar una función como [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) o `CGdiObject::GetObject` [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) para copiar los bits del mapa de bits identificado por el primer parámetro del mapa de bits creado por `CreateBitmapIndirect`.

Cuando termine con `CBitmap` el `CreateBitmapIndirect` objeto creado con la función, seleccione primero `CBitmap` el mapa de bits fuera del contexto del dispositivo y, a continuación, elimine el objeto.

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap

Inicializa un mapa de bits que es compatible con el dispositivo especificado por *pDC*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Especifica el contexto del dispositivo.

*nAncho*<br/>
Especifica el ancho (en píxeles) del mapa de bits.

*nAltura*<br/>
Especifica el alto (en píxeles) del mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mapa de bits tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Se puede seleccionar como el mapa de bits actual para cualquier dispositivo de memoria que sea compatible con el especificado por *pDC*.

Si *pDC* es un contexto de dispositivo de memoria, el mapa de bits devuelto tiene el mismo formato que el mapa de bits seleccionado actualmente en ese contexto de dispositivo. Un "contexto de dispositivo de memoria" es un bloque de memoria que representa una superficie de visualización. Se puede utilizar para preparar imágenes en la memoria antes de copiarlas en la superficie de visualización real del dispositivo compatible.

Cuando se crea un contexto de dispositivo de memoria, GDI selecciona automáticamente un mapa de bits de stock monocromo para él.

Dado que un contexto de dispositivo de memoria de color puede tener mapas `CreateCompatibleBitmap` de bits de color o monocromo seleccionados, el formato del mapa de bits devuelto por la función no siempre es el mismo; sin embargo, el formato de un mapa de bits compatible para un contexto de dispositivo que no es de memoria siempre está en el formato del dispositivo.

Cuando termine con `CBitmap` el objeto `CreateCompatibleBitmap` creado con la función, seleccione primero `CBitmap` el mapa de bits fuera del contexto del dispositivo y, a continuación, elimine el objeto.

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap

Inicializa un mapa de bits descartable que es compatible con el contexto del dispositivo identificado por *pDC*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Especifica un contexto de dispositivo.

*nAncho*<br/>
Especifica el ancho (en bits) del mapa de bits.

*nAltura*<br/>
Especifica la altura (en bits) del mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mapa de bits tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Una aplicación puede seleccionar este mapa de bits como el mapa de bits actual para un dispositivo de memoria que es compatible con el especificado por *pDC*.

Windows puede descartar un mapa de bits creado por esta función solo si una aplicación no lo ha seleccionado en un contexto de visualización. Si Windows descarta el mapa de bits cuando no está seleccionado y la aplicación intenta seleccionarlo más adelante, la función [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) devolverá NULL.

Cuando termine con `CBitmap` el objeto `CreateDiscardableBitmap` creado con la función, seleccione primero `CBitmap` el mapa de bits fuera del contexto del dispositivo y, a continuación, elimine el objeto.

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a>CBitmap::FromHandle

Devuelve un puntero `CBitmap` a un objeto cuando se le da un identificador a un mapa de bits GDI de Windows.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Especifica un mapa de bits GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero `CBitmap` a un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si `CBitmap` un objeto aún no está asociado `CBitmap` al identificador, se crea y adjunta un objeto temporal. Este `CBitmap` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal sólo es válido durante el procesamiento de un mensaje de ventana.

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a>CBitmap::GetBitmap

Recupera las propiedades de imagen para el mapa de bits adjunto.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parámetros

*pBitMap*<br/>
Puntero a una estructura [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) que recibirá las propiedades de la imagen. Este parámetro no debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a>CBitmap::GetBitmapBits

Copia el patrón de bits del mapa de bits adjunto en el búfer especificado.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parámetros

*dwCount*<br/>
El número de bytes que se deben copiar en el búfer.

*lpBits*<br/>
Puntero al búfer que recibirá el mapa de bits.

### <a name="return-value"></a>Valor devuelto

El número de bytes copiados en el búfer si el método se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Utilice [CBitmap::GetBitmap](#getbitmap) para determinar el tamaño de búfer necesario.

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension

Devuelve el ancho y alto del mapa de bits.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Valor devuelto

La anchura y la altura del mapa de bits, medida en unidades de 0,1 milímetros. El alto está `cy` en `CSize` el miembro del objeto `cx` y el ancho está en el miembro. Si el ancho y el alto `SetBitmapDimension`del mapa de bits no se han establecido mediante , el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

Se supone que el alto y el ancho se han establecido previamente mediante el [SetBitmapDimension](#setbitmapdimension) función miembro.

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a>CBitmap::LoadBitmap

Carga el recurso de mapa de bits denominado por *lpszResourceName* o identificado por el número de identificador en *nIDResource* desde el archivo ejecutable de la aplicación.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Apunta a una cadena terminada en null que contiene el nombre del recurso de mapa de bits.

*nIDResource*<br/>
Especifica el número de ID de recurso del recurso de mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mapa de bits `CBitmap` cargado se adjunta al objeto.

Si el mapa de bits identificado por *lpszResourceName* no existe o si no hay memoria suficiente para cargar el mapa de bits, la función devuelve 0.

Puede utilizar la función [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) para `LoadBitmap` eliminar el `CBitmap` mapa de bits cargado por la función, o el destructor eliminará el objeto automáticamente.

> [!CAUTION]
> Antes de eliminar el objeto, asegúrese de que no está seleccionado en un contexto de dispositivo.

Los siguientes mapas de bits se agregaron a las versiones 3.1 y posteriores de Windows:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Estos mapas de bits no se encuentran en los controladores de dispositivo para windows versiones 3.0 y anteriores. Para obtener una lista completa de mapas de bits y una presentación de su apariencia, consulte el Windows SDK.

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap

Llame a esta función miembro para cargar un mapa de bits y asignar los colores a los colores actuales del sistema.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parámetros

*nIDBitmap*<br/>
El identificador del recurso de mapa de bits.

*nFlags*<br/>
Una marca para un mapa de bits. Puede ser cero o CMB_MASKED.

*lpColorMap*<br/>
Puntero a `COLORMAP` una estructura que contiene la información de color necesaria para asignar los mapas de bits. Si este parámetro es NULL, la función utiliza el mapa de colores predeterminado.

*nMapSize*<br/>
El número de mapas de color a los que apunta *lpColorMap*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

De forma `LoadMappedBitmap` predeterminada, asignará los colores que se usan comúnmente en los glifos de botón.

Para obtener información acerca de cómo crear un mapa de bits asignado, vea la función de Windows [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) y la estructura [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) en el Windows SDK.

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap

Carga un mapa de bits predefinido utilizado por Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parámetros

*nIDBitmap*<br/>
Número de ID del mapa de bits de Windows predefinido. Los valores posibles se enumeran a continuación de WINDOWS. H:

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los nombres de mapa de bits que comienzan con OBM_OLD representan mapas de bits utilizados por las versiones de Windows anteriores a 3.0.

Tenga en cuenta que la constante OEMRESOURCE debe definirse antes de incluir WINDOWS. H para utilizar cualquiera de las **constantes OBM_.**

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a>CBitmap::operator HBITMAP

Utilice este operador para obtener el identificador `CBitmap` GDI de Windows adjunto del objeto.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un identificador para `CBitmap` el objeto GDI de Windows representado por el objeto; NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de conversión, que admite el uso directo de un `HBITMAP` objeto.

Para obtener más información sobre el uso de objetos gráficos, vea [Objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a>CBitmap::SetBitmapBits

Establece los bits de un mapa de bits en los valores de bits dados por *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parámetros

*dwCount*<br/>
Especifica el número de bytes a los que apunta *lpBits*.

*lpBits*<br/>
Apunta a la matriz BYTE que contiene los `CBitmap` valores de píxel que se van a copiar en el objeto. Para que el mapa de bits pueda representar su imagen correctamente, los valores deben tener formato para ajustarse a los valores de altura, anchura y profundidad de color que se especificaron cuando se creó la instancia de CBitmap. Para obtener más información, vea [CBitmap::CreateBitmap](#createbitmap).

### <a name="return-value"></a>Valor devuelto

El número de bytes utilizados para establecer los bits de mapa de bits; 0 si se produce un error en la función.

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension

Asigna un ancho y un alto a un mapa de bits en unidades de 0,1 milímetros.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
Especifica el ancho del mapa de bits (en unidades de 0,1 milímetros).

*nAltura*<br/>
Especifica la altura del mapa de bits (en unidades de 0,1 milímetros).

### <a name="return-value"></a>Valor devuelto

Las dimensiones de mapa de bits anteriores. Height está `cy` en la `CSize` variable miembro del objeto `cx` y width está en la variable miembro.

### <a name="remarks"></a>Observaciones

El GDI no utiliza estos valores excepto para devolverlos cuando una aplicación llama a la [GetBitmapDimension](#getbitmapdimension) función miembro.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
