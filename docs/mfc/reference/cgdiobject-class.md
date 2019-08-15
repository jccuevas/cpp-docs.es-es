---
title: Clase CGdiObject
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
ms.openlocfilehash: ea82e2c667dcbd476d22ed23085d409b448b27ed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506254"
---
# <a name="cgdiobject-class"></a>Clase CGdiObject

Proporciona una clase base para diferentes clases de objetos de la interfaz de dispositivo gráfico (GDI) de Windows, tales como mapas de bits, regiones, pinceles, lápices, tablas y fuentes.

## <a name="syntax"></a>Sintaxis

```
class CGdiObject : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Construye un objeto `CGdiObject`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|Adjunta un objeto GDI de Windows a un `CGdiObject` objeto.|
|[CGdiObject::CreateStockObject](#createstockobject)|Recupera un identificador de uno de los lápices, pinceles o fuentes predefinidos de Windows.|
|[CGdiObject::DeleteObject](#deleteobject)|Elimina el objeto GDI de Windows adjunto al objeto `CGdiObject` de la memoria liberando todo el almacenamiento del sistema asociado al objeto.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Elimina los objetos temporales `CGdiObject` creados por. `FromHandle`|
|[CGdiObject::Detach](#detach)|Desasocia un objeto GDI de Windows de `CGdiObject` un objeto y devuelve un identificador al objeto GDI de Windows.|
|[CGdiObject::FromHandle](#fromhandle)|Devuelve un puntero a un `CGdiObject` objeto dado un identificador a un objeto GDI de Windows.|
|[CGdiObject::GetObject](#getobject)|Rellena un búfer con datos que describen el objeto GDI de Windows asociado al `CGdiObject` objeto.|
|[CGdiObject::GetObjectType](#getobjecttype)|Recupera el tipo del objeto GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Devuelve `m_hObject` a menos que sea NULL, en cuyo caso se devuelve NULL.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Restablece el origen de un pincel o restablece una paleta lógica.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGdiObject:: Operator! =](#operator_neq)|Determina si dos objetos GDI no son iguales lógicamente.|
|[CGdiObject::operator ==](#operator_eq_eq)|Determina si dos objetos GDI son lógicamente iguales.|
|[CGdiObject:: Operator HGDIOBJ](#operator_hgdiobj)|Recupera un identificador para el objeto GDI de Windows asociado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|IDENTIFICADOR que contiene el HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN o HFONT adjuntado a este objeto.|

## <a name="remarks"></a>Comentarios

Nunca se crea un `CGdiObject` directamente. En su lugar, se crea un objeto a partir de una de sus clases `CPen` derivadas, como o `CBrush`.

Para obtener más información `CGdiObject`sobre, vea [objetos gráficos](../../mfc/graphic-objects.md).

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

Distinto de cero si los datos adjuntos son correctos; de lo contrario, es 0.

##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject

Construye un objeto `CGdiObject`.

```
CGdiObject();
```

### <a name="remarks"></a>Comentarios

Nunca se crea un `CGdiObject` directamente. En su lugar, se crea un objeto a partir de una de sus clases `CPen` derivadas, como o `Cbrush`.

##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject

Recupera un identificador de uno de los lápices, pinceles, o fuentes de Windows GDI predefinidos, y asocia el objeto GDI al `CGdiObject` objeto.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Constante que especifica el tipo de objeto estándar deseado. Vea el parámetro *fnObject* para [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) en el Windows SDK para obtener una descripción de los valores adecuados.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función con una de las clases derivadas que corresponde al tipo de objeto GDI de Windows `CPen` , como para un lápiz bursátil.

##  <a name="deleteobject"></a>  CGdiObject::DeleteObject

Elimina el objeto GDI de Windows adjunto de la memoria liberando todo el almacenamiento del sistema asociado con el objeto GDI de Windows.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto GDI se eliminó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta llamada no afecta al `CGdiObject` almacenamiento asociado al objeto. Una aplicación no debe llamar `DeleteObject` a en `CGdiObject` un objeto que está seleccionado actualmente en un contexto de dispositivo.

Cuando se elimina un pincel de patrón, no se elimina el mapa de bits asociado al pincel. El mapa de bits debe eliminarse de forma independiente.

##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap

Llamado automáticamente por el `CWinApp` controlador de tiempo de inactividad, `DeleteTempMap` elimina todos `CGdiObject` los objetos temporales `FromHandle`creados por.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Comentarios

`DeleteTempMap`Desasocia el objeto GDI de Windows asociado a un `CGdiObject` objeto temporal antes de eliminar `CGdiObject` el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>  CGdiObject::Detach

Desasocia un objeto GDI de Windows de `CGdiObject` un objeto y devuelve un identificador al objeto GDI de Windows.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Valor devuelto

`HANDLE` En el objeto GDI de Windows desasociado; de lo contrario, es NULL si no se adjunta ningún objeto GDI.

##  <a name="fromhandle"></a>  CGdiObject::FromHandle

Devuelve un puntero a un `CGdiObject` objeto dado un identificador a un objeto GDI de Windows.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
IDENTIFICADOR de un objeto GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CGdiObject` que puede ser temporal o permanente.

### <a name="remarks"></a>Comentarios

Si aún `CGdiObject` no se ha adjuntado un objeto al objeto GDI de Windows `CGdiObject` , se crea y se adjunta un objeto temporal.

Este objeto `CGdiObject` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal solo es válido durante el procesamiento de un mensaje de ventana.

##  <a name="getobject"></a>  CGdiObject::GetObject

Rellena un búfer con datos que definen un objeto especificado.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parámetros

*nCount*<br/>
Especifica el número de bytes que se van a copiar en el búfer de *lpObject* .

*lpObject*<br/>
Señala a un búfer proporcionado por el usuario que va a recibir la información.

### <a name="return-value"></a>Valor devuelto

Número de bytes recuperados; de lo contrario, 0 si se produce un error.

### <a name="remarks"></a>Comentarios

La función recupera una estructura de datos cuyo tipo depende del tipo de objeto gráfico, tal como se muestra en la lista siguiente:

|Object|Tipo de búfer|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|No compatible|

Si el objeto es un `CBitmap` objeto, `GetObject` solo devuelve la información de ancho, alto y formato de color del mapa de bits. Los bits reales se pueden recuperar mediante [CBitmap:: GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Si el objeto es un `CPalette` objeto, `GetObject` recupera una palabra que especifica el número de entradas de la paleta. La función no recupera la estructura [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) que define la paleta. Una aplicación puede obtener información sobre las entradas de la paleta llamando a [CPalette:: GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType

Recupera el tipo del objeto GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo del objeto, si es correcto; de lo contrario, es 0. El valor puede ser uno de los siguientes:

- Mapa de bits OBJ_BITMAP

- Pincel OBJ_BRUSH

- Fuente OBJ_FONT

- Paleta OBJ_PAL

- Lápiz OBJ_PEN

- Lápiz extendido OBJ_EXTPEN

- Región OBJ_REGION

- Contexto de dispositivo de OBJ_DC

- Contexto de dispositivo de memoria OBJ_MEMDC

- Metarchivo OBJ_METAFILE

- OBJ_METADC contexto de dispositivo de metarchivo

- Metarchivo mejorado de OBJ_ENHMETAFILE

- OBJ_ENHMETADC contexto de dispositivo de metarchivo mejorado

##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle

Devuelve `m_hObject` a menos que sea NULL, en cuyo caso se devuelve NULL.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR del objeto GDI de Windows adjunto; de lo contrario, es NULL si no hay ningún objeto asociado.

### <a name="remarks"></a>Comentarios

Esto forma parte del paradigma general de la interfaz de control y es útil cuando NULL es un valor válido o especial para un identificador.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

IDENTIFICADOR que contiene el HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE o HFONT adjuntado a este objeto.

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>CGdiObject:: Operator! =

Determina si dos objetos GDI no son iguales lógicamente.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Puntero a un existente `CGdiObject`.

### <a name="remarks"></a>Comentarios

Determina si un objeto GDI en el lado izquierdo no es igual a un objeto GDI en el lado derecho.

##  <a name="operator_eq_eq"></a>CGdiObject:: Operator = =

Determina si dos objetos GDI son lógicamente iguales.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Referencia a un existente `CGdiObject`.

### <a name="remarks"></a>Comentarios

Determina si un objeto GDI en el lado izquierdo es igual a un objeto GDI en el lado derecho.

##  <a name="operator_hgdiobj"></a>CGdiObject:: Operator HGDIOBJ

Recupera un identificador para el objeto GDI de Windows adjunto; de lo contrario, es NULL si no hay ningún objeto asociado.

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

Aunque `UnrealizeObject` es una función miembro de la `CGdiObject` clase, solo se debe invocar en `CBrush` objetos o `CPalette` .

En `CBrush` el caso `UnrealizeObject` de los objetos, indica al sistema que restablezca el origen del pincel determinado la próxima vez que se seleccione en un contexto de dispositivo. Si el objeto es un `CPalette` objeto, `UnrealizeObject` indica al sistema que se dé cuenta de la paleta como si no se hubiera realizado previamente. La próxima vez que la aplicación llame a la función [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) para la paleta especificada, el sistema reasigna completamente la paleta lógica a la paleta del sistema.

La `UnrealizeObject` función no se debe usar con objetos stock. Se `UnrealizeObject` debe llamar a la función cada vez que se establece un nuevo origen de pincel (por medio de la función [CDC:: SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) ). No `UnrealizeObject` se debe llamar a la función para el pincel seleccionado actualmente o la paleta seleccionada actualmente de cualquier contexto de presentación.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CBitmap (clase)](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush (clase)](../../mfc/reference/cbrush-class.md)<br/>
[CFont (clase)](../../mfc/reference/cfont-class.md)<br/>
[CPalette (clase)](../../mfc/reference/cpalette-class.md)<br/>
[CPen (clase)](../../mfc/reference/cpen-class.md)<br/>
[CRgn (clase)](../../mfc/reference/crgn-class.md)
