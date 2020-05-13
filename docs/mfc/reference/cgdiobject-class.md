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
ms.openlocfilehash: 0cd7a0e0ed500ee9394b00e8906640e9f950163b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373734"
---
# <a name="cgdiobject-class"></a>CGdiObject (clase)

Proporciona una clase base para diferentes clases de objetos de la interfaz de dispositivo gráfico (GDI) de Windows, tales como mapas de bits, regiones, pinceles, lápices, tablas y fuentes.

## <a name="syntax"></a>Sintaxis

```
class CGdiObject : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Construye un objeto `CGdiObject`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|Asocia un objeto GDI `CGdiObject` de Windows a un objeto.|
|[CGdiObject::CreateStockObject](#createstockobject)|Recupera un identificador de uno de los rotuladores, pinceles o fuentes predefinidos de Windows.|
|[CGdiObject::DeleteObject](#deleteobject)|Elimina el objeto GDI de `CGdiObject` Windows asociado al objeto de la memoria liberando todo el almacenamiento del sistema asociado al objeto.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Elimina los `CGdiObject` objetos `FromHandle`temporales creados por .|
|[CGdiObject::Detach](#detach)|Separa un objeto GDI `CGdiObject` de Windows de un objeto y devuelve un identificador al objeto GDI de Windows.|
|[CGdiObject::FromHandle](#fromhandle)|Devuelve un puntero `CGdiObject` a un objeto dado un identificador a un objeto GDI de Windows.|
|[CGdiObject::GetObject](#getobject)|Rellena un búfer con datos que describen el `CGdiObject` objeto GDI de Windows asociado al objeto.|
|[CGdiObject::GetObjectType](#getobjecttype)|Recupera el tipo del objeto GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Devuelve `m_hObject` **a** menos que sea NULL, en cuyo caso se devuelve NULL.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Restablece el origen de un pincel o restablece una paleta lógica.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGdiObject::operador !o](#operator_neq)|Determina si dos objetos GDI lógicamente no son iguales.|
|[CGdiObject::operador ?](#operator_eq_eq)|Determina si dos objetos GDI son lógicamente iguales.|
|[CGdiObject::operador HGDIOBJ](#operator_hgdiobj)|Recupera un HANDLE en el objeto GDI de Windows asociado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|Un HANDLE que contiene el HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN o HFONT asociado a este objeto.|

## <a name="remarks"></a>Observaciones

Nunca se `CGdiObject` crea un directamente. En su lugar, se crea un objeto a `CPen` `CBrush`partir de una de sus clases derivadas, como o .

Para obtener `CGdiObject`más información sobre , consulte [Objetos gráficos](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject::Attach

Asocia un objeto GDI `CGdiObject` de Windows a un objeto.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Un HANDLE para un objeto GDI de Windows (por ejemplo, HPEN o HBRUSH).

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo adjunto es correcto; de lo contrario 0.

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject::CGdiObject

Construye un objeto `CGdiObject`.

```
CGdiObject();
```

### <a name="remarks"></a>Observaciones

Nunca se `CGdiObject` crea un directamente. En su lugar, se crea un objeto a `CPen` `Cbrush`partir de una de sus clases derivadas, como o .

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject::CreateStockObject

Recupera un identificador de uno de los lápices, pinceles o fuentes GDI de Windows `CGdiObject` predefinidos y adjunta el objeto GDI al objeto.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Constante que especifica el tipo de objeto de stock deseado. Consulte el parámetro *fnObject* para [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) en el Windows SDK para obtener una descripción de los valores adecuados.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Llame a esta función con una de las clases derivadas que `CPen` corresponde al tipo de objeto GDI de Windows, como para un lápiz de valores.

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject::DeleteObject

Elimina el objeto GDI de Windows asociado de la memoria liberando todo el almacenamiento del sistema asociado con el objeto GDI de Windows.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto GDI se eliminó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El almacenamiento asociado `CGdiObject` con el objeto no se ve afectado por esta llamada. Una aplicación no `DeleteObject` debe `CGdiObject` llamar a un objeto que está seleccionado actualmente en un contexto de dispositivo.

Cuando se elimina un pincel de patrón, el mapa de bits asociado al pincel no se elimina. El mapa de bits debe eliminarse de forma independiente.

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject::DeleteTempMap

Llamado automáticamente `CWinApp` por el controlador `DeleteTempMap` de tiempo `CGdiObject` de `FromHandle`inactividad, elimina los objetos temporales creados por .

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Observaciones

`DeleteTempMap`separa el objeto GDI de `CGdiObject` Windows asociado a `CGdiObject` un objeto temporal antes de eliminar el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject::Detach

Separa un objeto GDI `CGdiObject` de Windows de un objeto y devuelve un identificador al objeto GDI de Windows.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Valor devuelto

A `HANDLE` al objeto GDI de Windows separado; de lo contrario NULL si no hay ningún objeto GDI asociado.

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject::FromHandle

Devuelve un puntero `CGdiObject` a un objeto dado un identificador a un objeto GDI de Windows.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Un HANDLE para un objeto GDI de Windows.

### <a name="return-value"></a>Valor devuelto

Un puntero `CGdiObject` a un que puede ser temporal o permanente.

### <a name="remarks"></a>Observaciones

Si `CGdiObject` un objeto aún no está asociado al `CGdiObject` objeto GDI de Windows, se crea y adjunta un objeto temporal.

Este `CGdiObject` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos gráficos temporales. Otra forma de decir esto es que el objeto temporal sólo es válido durante el procesamiento de un mensaje de ventana.

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject::GetObject

Rellena un búfer con datos que definen un objeto especificado.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parámetros

*nCount*<br/>
Especifica el número de bytes que se van a copiar en el búfer *lpObject.*

*lpObject*<br/>
Señala a un búfer proporcionado por el usuario que va a recibir la información.

### <a name="return-value"></a>Valor devuelto

El número de bytes recuperados; 0 si se produce un error.

### <a name="remarks"></a>Observaciones

La función recupera una estructura de datos cuyo tipo depende del tipo de objeto gráfico, como se muestra en la lista siguiente:

|Object|Tipo de búfer|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[Bits](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|No compatible|

Si el objeto `CBitmap` es `GetObject` un objeto, devuelve solo la información de ancho, alto y formato de color del mapa de bits. Los bits reales se pueden recuperar mediante [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Si el objeto `CPalette` es `GetObject` un objeto, recupera una PALABRA que especifica el número de entradas de la paleta. La función no recupera la estructura [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) que define la paleta. Una aplicación puede obtener información sobre las entradas de paleta llamando a [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject::GetObjectType

Recupera el tipo del objeto GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Valor devuelto

El tipo del objeto, si se realiza correctamente; de lo contrario 0. El valor puede ser uno de los siguientes:

- OBJ_BITMAP mapa de bits

- Cepillo OBJ_BRUSH

- Fuente OBJ_FONT

- OBJ_PAL Paleta

- pluma OBJ_PEN

- OBJ_EXTPEN pluma extendida

- Región OBJ_REGION

- OBJ_DC contexto del dispositivo

- OBJ_MEMDC Contexto del dispositivo de memoria

- OBJ_METAFILE Metafile

- contexto del dispositivo de metarchivo OBJ_METADC

- OBJ_ENHMETAFILE metaarchivo mejorado

- OBJ_ENHMETADC contexto de dispositivo de metarchivo mejorado

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject::GetSafeHandle

Devuelve `m_hObject` **a** menos que sea NULL, en cuyo caso se devuelve NULL.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Un HANDLE para el objeto GDI de Windows adjunto; de lo contrario NULL si no se adjunta ningún objeto.

### <a name="remarks"></a>Observaciones

Esto forma parte del paradigma de interfaz de identificador general y es útil cuando NULL es un valor válido o especial para un identificador.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject::m_hObject

Un HANDLE que contiene el HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE o HFONT asociado a este objeto.

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject::operador !o

Determina si dos objetos GDI lógicamente no son iguales.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Un puntero a `CGdiObject`un archivo .

### <a name="remarks"></a>Observaciones

Determina si un objeto GDI en el lado izquierdo no es igual a un objeto GDI en el lado derecho.

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject::operador ?

Determina si dos objetos GDI son lógicamente iguales.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Una referencia a `CGdiObject`un archivo .

### <a name="remarks"></a>Observaciones

Determina si un objeto GDI en el lado izquierdo es igual a un objeto GDI en el lado derecho.

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject::operador HGDIOBJ

Recupera un HANDLE en el objeto GDI de Windows adjunto; de lo contrario NULL si no se adjunta ningún objeto.

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject::UnrealizeObject

Restablece el origen de un pincel o restablece una paleta lógica.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Mientras `UnrealizeObject` que es `CGdiObject` una función miembro de `CBrush` `CPalette` la clase, se debe invocar solo en u objetos.

Para `CBrush` los `UnrealizeObject` objetos, indica al sistema que restablezca el origen del pincel especificado la próxima vez que se seleccione en un contexto de dispositivo. Si el objeto `CPalette` es `UnrealizeObject` un objeto, indica al sistema que realice la paleta como si no se hubiera realizado previamente. La próxima vez que la aplicación llame a la función [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) para la paleta especificada, el sistema reasigna completamente la paleta lógica a la paleta del sistema.

La `UnrealizeObject` función no debe utilizarse con objetos de stock. Se `UnrealizeObject` debe llamar a la función siempre que se establezca un nuevo origen de pincel (mediante la función [CDC::SetBrushOrg).](../../mfc/reference/cdc-class.md#setbrushorg) No `UnrealizeObject` se debe llamar a la función para el pincel seleccionado actualmente o la paleta seleccionada actualmente de cualquier contexto de visualización.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush (clase)](../../mfc/reference/cbrush-class.md)<br/>
[Clase CFont](../../mfc/reference/cfont-class.md)<br/>
[Clase CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Clase CPen](../../mfc/reference/cpen-class.md)<br/>
[Clase CRgn](../../mfc/reference/crgn-class.md)
