---
title: CGdiObject (clase)
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: 1b2b87173bf504455ba314fdd89ffae298cae6a8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301225"
---
# <a name="cgdiobject-class"></a>CGdiObject (clase)

Proporciona una clase base para diferentes clases de objetos de la interfaz de dispositivo gráfico (GDI) de Windows, tales como mapas de bits, regiones, pinceles, lápices, tablas y fuentes.

## <a name="syntax"></a>Sintaxis

```
class CGdiObject : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Construye un objeto `CGdiObject`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|Adjunta un objeto GDI de Windows a un `CGdiObject` objeto.|
|[CGdiObject::CreateStockObject](#createstockobject)|Recupera un identificador a uno de los lápices de acciones predefinidas de Windows, pinceles o las fuentes.|
|[CGdiObject::DeleteObject](#deleteobject)|Elimina el objeto GDI de Windows asociado al `CGdiObject` objeto de la memoria al liberar todo el almacenamiento del sistema asociado al objeto.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Elimina cualquier temporal `CGdiObject` los objetos creados por `FromHandle`.|
|[CGdiObject::Detach](#detach)|Desasocia un objeto GDI de Windows desde un `CGdiObject` de objetos y devuelve un identificador para el objeto GDI de Windows.|
|[CGdiObject::FromHandle](#fromhandle)|Devuelve un puntero a un `CGdiObject` objeto especifica un identificador a un objeto GDI de Windows.|
|[CGdiObject::GetObject](#getobject)|Rellena un búfer con datos que describe el objeto GDI de Windows asociada a la `CGdiObject` objeto.|
|[CGdiObject::GetObjectType](#getobjecttype)|Recupera el tipo del objeto GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Devuelve `m_hObject` a menos que **esto** es NULL, en el que se devuelve NULL case.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Restablece el origen de un pincel o restablece una paleta lógica.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CGdiObject::operator !=](#operator_neq)|Determina si dos objetos GDI lógicamente no son iguales.|
|[CGdiObject::operator ==](#operator_eq_eq)|Determina si dos objetos GDI son lógicamente iguales.|
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Recupera un identificador para el objeto adjunto de GDI de Windows.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|Un identificador que contiene el HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN o HFONT asociado a este objeto.|

## <a name="remarks"></a>Comentarios

No crear nunca un `CGdiObject` directamente. En su lugar, se crea un objeto de una de sus clases derivadas, como `CPen` o `CBrush`.

Para obtener más información sobre `CGdiObject`, consulte [objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="attach"></a>  CGdiObject::Attach

Adjunta un objeto GDI de Windows a un `CGdiObject` objeto.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
IDENTIFICADOR de un objeto GDI de Windows (por ejemplo, HPEN o HBRUSH).

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos adjuntos se realiza correctamente; en caso contrario, es 0.

##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject

Construye un objeto `CGdiObject`.

```
CGdiObject();
```

### <a name="remarks"></a>Comentarios

No crear nunca un `CGdiObject` directamente. En su lugar, se crea un objeto de una de sus clases derivadas, como `CPen` o `Cbrush`.

##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject

Recupera un identificador a uno de los lápices de GDI de Windows estándar predefinidos, pinceles o fuentes y adjunta el objeto GDI en el `CGdiObject` objeto.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Constante que especifica el tipo de objeto stock deseado. Vea el parámetro *fnObject* para [GetStockObject](/windows/desktop/api/wingdi/nf-wingdi-getstockobject) en el SDK de Windows para obtener una descripción de los valores adecuados.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Llamada a esta función con uno de la clase derivada, las clases que corresponde al tipo de objeto GDI de Windows, como `CPen` para una pluma de cotizaciones.

##  <a name="deleteobject"></a>  CGdiObject::DeleteObject

Elimina el objeto adjunto de GDI de Windows de la memoria al liberar todo el almacenamiento del sistema asociado al objeto GDI de Windows.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto GDI se eliminó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El almacenamiento asociado con el `CGdiObject` objeto no se ve afectado por esta llamada. No debe llamar una aplicación `DeleteObject` en un `CGdiObject` objeto que está seleccionado actualmente en un contexto de dispositivo.

Cuando se elimina un pincel de modelo, no se elimina el mapa de bits asociado con el pincel. El mapa de bits debe eliminarse por separado.

##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap

Llama de forma automática el `CWinApp` controlador de tiempo de inactividad, `DeleteTempMap` elimina temporales `CGdiObject` los objetos creados por `FromHandle`.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Comentarios

`DeleteTempMap` Desasocia el objeto GDI de Windows que se adjunta a un archivo temporal `CGdiObject` objeto antes de eliminar el `CGdiObject` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>  CGdiObject::Detach

Desasocia un objeto GDI de Windows desde un `CGdiObject` de objetos y devuelve un identificador para el objeto GDI de Windows.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Valor devuelto

Un `HANDLE` para la GDI de Windows al objeto desasociado; de lo contrario, NULL si no hay ningún objeto GDI está conectado.

##  <a name="fromhandle"></a>  CGdiObject::FromHandle

Devuelve un puntero a un `CGdiObject` objeto especifica un identificador a un objeto GDI de Windows.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
IDENTIFICADOR de un objeto GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CGdiObject` que puede ser temporal o permanente.

### <a name="remarks"></a>Comentarios

Si un `CGdiObject` objeto no está asociado al objeto GDI de Windows, un archivo temporal `CGdiObject` objeto creado y conectado.

Este temporal `CGdiObject` objeto solo es válido hasta la próxima vez que la aplicación tiene tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos de gráficos temporales. Otra forma de expresarlo es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.

##  <a name="getobject"></a>  CGdiObject::GetObject

Rellena un búfer con datos que define un objeto especificado.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parámetros

*nCount*<br/>
Especifica el número de bytes que deben copiarse en el *lpObject* búfer.

*lpObject*<br/>
Señala a un búfer proporcionado por el usuario que va a recibir la información.

### <a name="return-value"></a>Valor devuelto

Recupera el número de bytes; en caso contrario, 0 si un error se produce.

### <a name="remarks"></a>Comentarios

La función recupera una estructura de datos cuyo tipo depende del tipo de objeto de gráfico, como se muestra en la lista siguiente:

|Object|Tipo de búfer|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/desktop/api/Wingdi/ns-wingdi-taglogpen)|
|`CBrush`|[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)|
|`CFont`|[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)|
|`CBitmap`|[BITMAP](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap)|
|`CPalette`|WORD|
|`CRgn`|No compatibles|

Si el objeto es un `CBitmap` objeto, `GetObject` devuelve el ancho, alto y la información de formato de color del mapa de bits. Los bits reales que se pueden recuperar mediante el uso de [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Si el objeto es un `CPalette` objeto, `GetObject` recupera una palabra que especifica el número de entradas en la paleta. La función no recupera el [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) estructura que define la paleta. Una aplicación puede obtener información sobre las entradas de la paleta mediante una llamada a [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType

Recupera el tipo del objeto GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Valor devuelto

El tipo del objeto, si se realiza correctamente; en caso contrario, es 0. El valor puede ser uno de los siguientes:

- Mapa de bits OBJ_BITMAP

- OBJ_BRUSH Brush

- Fuente OBJ_FONT

- Paleta OBJ_PAL

- OBJ_PEN Pen

- Lápiz OBJ_EXTPEN extendidos

- Región OBJ_REGION

- Contexto de dispositivo OBJ_DC

- Contexto de dispositivo de memoria OBJ_MEMDC

- Metarchivo OBJ_METAFILE

- Contexto de dispositivo de metarchivo OBJ_METADC

- Metarchivo mejorado OBJ_ENHMETAFILE

- Contexto de dispositivo de metarchivo mejorado OBJ_ENHMETADC

##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle

Devuelve `m_hObject` a menos que **esto** es NULL, en el que se devuelve NULL case.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el objeto adjunto de GDI de Windows; en caso contrario, es NULL si no hay ningún objeto está asociado.

### <a name="remarks"></a>Comentarios

Esto forma parte del paradigma de interfaz de controlador general y es útil cuando NULL es un valor válido o especial para un identificador.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

Un identificador que contiene el HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE o HFONT asociado a este objeto.

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>  CGdiObject::operator !=

Determina si dos objetos GDI lógicamente no son iguales.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Un puntero a una existente `CGdiObject`.

### <a name="remarks"></a>Comentarios

Determina si un objeto GDI en el lado izquierdo no es igual a un objeto GDI en el lado derecho.

##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==

Determina si dos objetos GDI son lógicamente iguales.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Una referencia a una existente `CGdiObject`.

### <a name="remarks"></a>Comentarios

Determina si un objeto GDI en el lado izquierdo es igual a un objeto GDI en el lado derecho.

##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ

Recupera un identificador para el objeto adjunto de GDI de Windows; en caso contrario, es NULL si no hay ningún objeto está asociado.

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject

Restablece el origen de un pincel o restablece una paleta lógica.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Mientras `UnrealizeObject` es una función miembro de la `CGdiObject` (clase), debe invocarse únicamente en `CBrush` o `CPalette` objetos.

Para `CBrush` objetos, `UnrealizeObject` indica al sistema para restablecer la próxima vez que está seleccionado en un contexto de dispositivo de origen del pincel especificado. Si el objeto es un `CPalette` objeto, `UnrealizeObject` indica al sistema que tenga en cuenta la paleta como si hubiera no anteriormente se han logrado. La próxima vez que la aplicación llama a la [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) completamente, la función de la paleta especificada, el sistema reasigna la paleta lógica a la paleta del sistema.

El `UnrealizeObject` función no debe usarse con objetos estándar. El `UnrealizeObject` debe llamar a la función cada vez que se ha establecido un nuevo origen de pincel (por medio de la [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) función). El `UnrealizeObject` no se debe llamar la función para el pincel actualmente seleccionado o paleta seleccionado actualmente de cualquier contexto de presentación.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CBitmap (clase)](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush (clase)](../../mfc/reference/cbrush-class.md)<br/>
[CFont (clase)](../../mfc/reference/cfont-class.md)<br/>
[CPalette (clase)](../../mfc/reference/cpalette-class.md)<br/>
[CPen (clase)](../../mfc/reference/cpen-class.md)<br/>
[CRgn (clase)](../../mfc/reference/crgn-class.md)
