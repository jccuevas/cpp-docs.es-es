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
ms.openlocfilehash: 7161a4cf4484b6cc9e76e6955de558ca6e9121ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424684"
---
# <a name="cbitmap-class"></a>Clase CBitmap

Encapsula un mapa de bits de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular el mapa de bits.

## <a name="syntax"></a>Sintaxis

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmap:: CBitmap](#cbitmap)|Construye un objeto `CBitmap`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmap:: CreateBitmap](#createbitmap)|Inicializa el objeto con un mapa de bits de memoria dependiente del dispositivo que tiene un ancho, un alto y un patrón de bits especificados.|
|[CBitmap:: CreateBitmapIndirect](#createbitmapindirect)|Inicializa el objeto con un mapa de bits con el ancho, el alto y el patrón de bits (si se especifica) que se proporcionan en una estructura de `BITMAP`.|
|[CBitmap:: CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializa el objeto con un mapa de bits para que sea compatible con un dispositivo especificado.|
|[CBitmap:: CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializa el objeto con un mapa de bits descartable que es compatible con un dispositivo especificado.|
|[CBitmap:: FromHandle](#fromhandle)|Devuelve un puntero a un objeto `CBitmap` cuando se proporciona un identificador a un mapa de bits de Windows `HBITMAP`.|
|[CBitmap:: GetBitmap](#getbitmap)|Rellena una estructura de `BITMAP` con información sobre el mapa de bits.|
|[CBitmap:: GetBitmapBits](#getbitmapbits)|Copia los bits del mapa de bits especificado en el búfer especificado.|
|[CBitmap:: GetBitmapDimension](#getbitmapdimension)|Devuelve el ancho y el alto del mapa de bits. Se supone que el alto y el ancho se han establecido anteriormente mediante la función miembro [SetBitmapDimension](#setbitmapdimension) .|
|[CBitmap:: LoadBitmap](#loadbitmap)|Inicializa el objeto cargando un recurso de mapa de bits con nombre del archivo ejecutable de la aplicación y adjuntando el mapa de bits al objeto.|
|[CBitmap:: LoadMappedBitmap](#loadmappedbitmap)|Carga un mapa de bits y asigna colores a los colores actuales del sistema.|
|[CBitmap:: LoadOEMBitmap](#loadoembitmap)|Inicializa el objeto cargando un mapa de bits de Windows predefinido y adjuntando el mapa de bits al objeto.|
|[CBitmap:: SetBitmapBits](#setbitmapbits)|Establece los bits de un mapa de bits en los valores de bit especificados.|
|[CBitmap:: SetBitmapDimension](#setbitmapdimension)|Asigna un ancho y un alto a un mapa de bits en unidades 0,1-milímetro.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmap:: Operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de Windows asociado al objeto de `CBitmap`.|

## <a name="remarks"></a>Observaciones

Para usar un objeto de `CBitmap`, construya el objeto, adjunte un identificador de mapa de bits a él con una de las funciones miembro de inicialización y, a continuación, llame a las funciones miembro del objeto.

Para obtener más información sobre el uso de objetos gráficos como `CBitmap`, vea [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cbitmap"></a>CBitmap:: CBitmap

Construye un objeto `CBitmap`.

```
CBitmap();
```

### <a name="remarks"></a>Observaciones

El objeto resultante se debe inicializar con una de las funciones miembro de inicialización.

##  <a name="createbitmap"></a>CBitmap:: CreateBitmap

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

*nWidth*<br/>
Especifica el ancho (en píxeles) del mapa de bits.

*nHeight*<br/>
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

En el caso de un mapa de bits de color, el parámetro *nPlanes* o *nBitcount* debe establecerse en 1. Si ambos parámetros se establecen en 1, `CreateBitmap` crea un mapa de bits monocromo.

Aunque un mapa de bits no se puede seleccionar directamente para un dispositivo de visualización, puede seleccionarse como el mapa de bits actual para un "contexto de dispositivo de memoria" usando [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) y copiarse en cualquier contexto de dispositivo compatible con la función [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) .

Cuando termine con el objeto `CBitmap` creado por la función `CreateBitmap` , seleccione primero el mapa de bits fuera del contexto del dispositivo y elimine luego el objeto `CBitmap` .

Para obtener más información, vea la descripción del campo `bmBits` en la estructura `BITMAP`. La estructura [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) se describe en la función miembro [CBitmap::CreateBitmapIndirect](#createbitmapindirect) .

##  <a name="createbitmapindirect"></a>CBitmap:: CreateBitmapIndirect

Inicializa un mapa de bits que tiene el ancho, el alto y el patrón de bits (si se especifica), dados en la estructura a la que apunta *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parámetros

*lpBitmap*<br/>
Apunta a una estructura de [mapa de bits](/windows/win32/api/wingdi/ns-wingdi-bitmap) que contiene información sobre el mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Aunque un mapa de bits no se puede seleccionar directamente para un dispositivo de visualización, puede seleccionarse como el mapa de bits actual para un contexto de dispositivo de memoria mediante [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) y copiarse en cualquier contexto de dispositivo compatible con la función [CDC:: bitblt](../../mfc/reference/cdc-class.md#bitblt) o [CDC:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) . (La función [CDC::P atblt](../../mfc/reference/cdc-class.md#patblt) puede copiar el mapa de bits para el pincel actual directamente en el contexto de dispositivo de pantalla).

Si la estructura de `BITMAP` señalada por el parámetro *lpBitmap* se ha rellenado con la función `GetObject`, no se especifican los bits del mapa de bits y el mapa de bits no se inicializa. Para inicializar el mapa de bits, una aplicación puede usar una función como [CDC:: bitblt](../../mfc/reference/cdc-class.md#bitblt) o [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) para copiar los bits del mapa de bits identificado por el primer parámetro de `CGdiObject::GetObject` al mapa de bits creado por `CreateBitmapIndirect`.

Cuando termine con el `CBitmap` objeto creado con `CreateBitmapIndirect` función, seleccione primero el mapa de bits fuera del contexto del dispositivo y, a continuación, elimine el objeto `CBitmap`.

##  <a name="createcompatiblebitmap"></a>CBitmap:: CreateCompatibleBitmap

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

*nWidth*<br/>
Especifica el ancho (en píxeles) del mapa de bits.

*nHeight*<br/>
Especifica el alto (en píxeles) del mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mapa de bits tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Se puede seleccionar como el mapa de bits actual para cualquier dispositivo de memoria compatible con el especificado por *pDC*.

Si *pDC* es un contexto de dispositivo de memoria, el mapa de bits devuelto tiene el mismo formato que el mapa de bits seleccionado actualmente en ese contexto de dispositivo. Un "contexto de dispositivo de memoria" es un bloque de memoria que representa una superficie de presentación. Se puede usar para preparar imágenes en la memoria antes de copiarlas en la superficie de visualización real del dispositivo compatible.

Cuando se crea un contexto de dispositivo de memoria, GDI selecciona automáticamente un mapa de bits de cotización monocroma para él.

Dado que un contexto de dispositivo de memoria de color puede tener los mapas de bits de color o monocromo seleccionados, el formato del mapa de bits devuelto por la función `CreateCompatibleBitmap` no es siempre el mismo. sin embargo, el formato de un mapa de bits compatible para un contexto de dispositivo que no es de memoria siempre está en el formato del dispositivo.

Cuando termine con el `CBitmap` objeto creado con la función `CreateCompatibleBitmap`, seleccione primero el mapa de bits fuera del contexto del dispositivo y, a continuación, elimine el objeto `CBitmap`.

##  <a name="creatediscardablebitmap"></a>CBitmap:: CreateDiscardableBitmap

Inicializa un mapa de bits descartable que es compatible con el contexto de dispositivo identificado por *pDC*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Especifica un contexto de dispositivo.

*nWidth*<br/>
Especifica el ancho (en bits) del mapa de bits.

*nHeight*<br/>
Especifica el alto (en bits) del mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mapa de bits tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Una aplicación puede seleccionar este mapa de bits como el mapa de bits actual para un dispositivo de memoria compatible con el especificado por *pDC*.

Windows puede descartar un mapa de bits creado por esta función solo si una aplicación no la ha seleccionado en un contexto de presentación. Si Windows descarta el mapa de bits cuando no está seleccionado y la aplicación intenta seleccionarlo más tarde, la función [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) devolverá null.

Cuando termine con el `CBitmap` objeto creado con la función `CreateDiscardableBitmap`, seleccione primero el mapa de bits fuera del contexto del dispositivo y, a continuación, elimine el objeto `CBitmap`.

##  <a name="fromhandle"></a>CBitmap:: FromHandle

Devuelve un puntero a un objeto `CBitmap` cuando se proporciona un identificador a un mapa de bits de Windows GDI.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Especifica un mapa de bits de Windows GDI.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de `CBitmap` si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Si un objeto de `CBitmap` no está ya asociado al identificador, se crea y se adjunta un objeto de `CBitmap` temporal. Este objeto `CBitmap` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal solo es válido durante el procesamiento de un mensaje de ventana.

##  <a name="getbitmap"></a>CBitmap:: GetBitmap

Recupera las propiedades de la imagen para el mapa de bits adjunto.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parámetros

*pBitMap*<br/>
Puntero a una estructura de [mapa de bits](/windows/win32/api/wingdi/ns-wingdi-bitmap) que recibirá las propiedades de la imagen. Este parámetro no debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

##  <a name="getbitmapbits"></a>CBitmap:: GetBitmapBits

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

Número de bytes copiados en el búfer si el método se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Use [CBitmap:: GetBitmap](#getbitmap) para determinar el tamaño de búfer necesario.

##  <a name="getbitmapdimension"></a>CBitmap:: GetBitmapDimension

Devuelve el ancho y el alto del mapa de bits.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho y alto del mapa de bits, medido en unidades 0,1-milímetro. El alto está en el miembro `cy` del objeto `CSize` y el ancho está en el miembro `cx`. Si el ancho y el alto del mapa de bits no se han establecido mediante `SetBitmapDimension`, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

Se supone que el alto y el ancho se han establecido previamente mediante el uso de la función miembro [SetBitmapDimension](#setbitmapdimension) .

##  <a name="loadbitmap"></a>CBitmap:: LoadBitmap

Carga el recurso de mapa de bits denominado por *lpszResourceName* o identificado por el número de identificador en *nIDResource* desde el archivo ejecutable de la aplicación.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Apunta a una cadena terminada en null que contiene el nombre del recurso de mapa de bits.

*nIDResource*<br/>
Especifica el número de ID. de recurso del recurso de mapa de bits.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mapa de bits cargado se adjunta al objeto de `CBitmap`.

Si el mapa de bits identificado por *lpszResourceName* no existe o si no hay suficiente memoria para cargar el mapa de bits, la función devuelve 0.

Puede usar la función [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) para eliminar el mapa de bits cargado por la función `LoadBitmap`, o el destructor `CBitmap` eliminará el objeto automáticamente.

> [!CAUTION]
>  Antes de eliminar el objeto, asegúrese de que no está seleccionado en un contexto de dispositivo.

Se han agregado los siguientes mapas de bits a las versiones 3,1 y posteriores de Windows:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Estos mapas de bits no se encuentran en los controladores de dispositivos para las versiones 3,0 y anteriores de Windows. Para obtener una lista completa de los mapas de bits y una presentación de su aspecto, vea el Windows SDK.

##  <a name="loadmappedbitmap"></a>CBitmap:: LoadMappedBitmap

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
IDENTIFICADOR del recurso de mapa de bits.

*nFlags*<br/>
Marca para un mapa de bits. Puede ser cero o CMB_MASKED.

*lpColorMap*<br/>
Puntero a una estructura de `COLORMAP` que contiene la información de color necesaria para asignar los mapas de bits. Si este parámetro es NULL, la función utiliza la asignación de colores predeterminada.

*nMapSize*<br/>
El número de mapas de color a los que apunta *lpColorMap*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

De forma predeterminada, `LoadMappedBitmap` asignará los colores que se usan normalmente en glifos de botón.

Para obtener información sobre cómo crear un mapa de bits asignado, vea la función de Windows [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) y la estructura [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) en el Windows SDK.

##  <a name="loadoembitmap"></a>CBitmap:: LoadOEMBitmap

Carga un mapa de bits predefinido utilizado por Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parámetros

*nIDBitmap*<br/>
Número de identificador del mapa de bits predefinido de Windows. Los valores posibles se enumeran a continuación desde WINDOWS. C

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

Los nombres de mapa de bits que comienzan por OBM_OLD representan mapas de bits usados por las versiones de Windows anteriores a 3,0.

Tenga en cuenta que la constante OEMRESOURCE debe definirse antes de incluir las ventanas. H para usar cualquiera de las constantes de **OBM_** .

##  <a name="operator_hbitmap"></a>CBitmap:: Operator HBITMAP

Utilice este operador para obtener el identificador de GDI de Windows asociado del objeto `CBitmap`.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, identificador del objeto GDI de Windows representado por el objeto `CBitmap`; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de conversión, que admite el uso directo de un objeto `HBITMAP`.

Para obtener más información sobre el uso de objetos gráficos, vea [objetos gráficos](/windows/win32/gdi/graphic-objects) en el Windows SDK.

##  <a name="setbitmapbits"></a>CBitmap:: SetBitmapBits

Establece los bits de un mapa de bits en los valores de bit proporcionados por *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parámetros

*dwCount*<br/>
Especifica el número de bytes al que apunta *lpBits*.

*lpBits*<br/>
Apunta a la matriz de BYTEs que contiene los valores de píxel que se van a copiar en el objeto de `CBitmap`. Para que el mapa de bits pueda representar su imagen correctamente, se debe dar formato a los valores para ajustarse a los valores de alto, ancho y profundidad de color que se especificaron cuando se creó la instancia de CBitmap. Para obtener más información, vea [CBitmap:: CreateBitmap](#createbitmap).

### <a name="return-value"></a>Valor devuelto

Número de bytes utilizados para establecer los bits de mapa de bits; 0 si se produce un error en la función.

##  <a name="setbitmapdimension"></a>CBitmap:: SetBitmapDimension

Asigna un ancho y un alto a un mapa de bits en unidades 0,1-milímetro.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
Especifica el ancho del mapa de bits (en unidades 0,1-milímetros).

*nHeight*<br/>
Especifica el alto del mapa de bits (en unidades 0,1-milímetros).

### <a name="return-value"></a>Valor devuelto

Dimensiones de mapa de bits anteriores. Height está en la variable de miembro `cy` del objeto `CSize` y el ancho está en la variable miembro `cx`.

### <a name="remarks"></a>Observaciones

GDI no utiliza estos valores excepto para devolverlos cuando una aplicación llama a la función miembro [GetBitmapDimension](#getbitmapdimension) .

## <a name="see-also"></a>Consulte también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject (clase)](../../mfc/reference/cgdiobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
