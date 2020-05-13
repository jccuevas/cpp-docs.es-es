---
title: Persistencia de los controles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 88707da503b1d1cdc809827dc4d1bac0ccad9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373010"
---
# <a name="persistence-of-ole-controls"></a>Persistencia de los controles OLE

Una capacidad de los controles OLE es la persistencia de propiedades (o serialización), que permite al control OLE leer o escribir valores de propiedad en y desde un archivo o secuencia. Una aplicación contenedora puede usar la serialización para almacenar los valores de propiedad de un control incluso después de que la aplicación haya destruido el control. Los valores de propiedad del control OLE, a continuación, se pueden leer desde el archivo o secuencia cuando se crea una nueva instancia del control en un momento posterior.

### <a name="persistence-of-ole-controls"></a>Persistencia de los controles OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Intercambia una propiedad de control que almacena datos de objetos binarios grandes (BLOB).|
|[PX_Bool](#px_bool)|Intercambia una propiedad de control de tipo **BOOL**.|
|[PX_Color](#px_color)|Intercambia una propiedad de color de un control.|
|[PX_Currency](#px_currency)|Intercambia una propiedad de control de tipo **CY**.|
|[PX_DataPath](#px_datapath)|Intercambia una propiedad `CDataPathProperty`de control de tipo .|
|[PX_Double](#px_double)|Intercambia una propiedad de control de tipo **double**.|
|[PX_Font](#px_font)|Intercambia una propiedad de fuente de un control.|
|[PX_Float](#px_float)|Intercambia una propiedad de control de tipo **float**.|
|[PX_IUnknown](#px_iunknown)|Intercambia una propiedad de control de tipo indefinido.|
|[PX_Long](#px_long)|Intercambia una propiedad de control de tipo **long**.|
|[PX_Picture](#px_picture)|Intercambia una propiedad de imagen de un control.|
|[PX_Short](#px_short)|Intercambia una propiedad de control de tipo **short**.|
|[PX_ULong](#px_ulong)|Intercambia una propiedad de control de tipo **ULONG**.|
|[PX_UShort](#px_ushort)|Intercambia una propiedad de control de tipo **USHORT**.|
|[PXstring](#px_string)|Intercambia una propiedad de control de cadena de caracteres.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Intercambia las propiedades relacionadas con la fuente de un control VBX en una propiedad de fuente de control OLE.|

Además, `AfxOleTypeMatchGuid` se proporciona la función global para probar una coincidencia entre un TYPEDESC y un GUID determinado.

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad que almacena datos binarios de objetos grandes (BLOB).

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*hBlob*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*hBlobDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *hBlob*, según corresponda. Esta variable debe inicializarse en NULL `PX_Blob` antes de llamar inicialmente por primera vez (normalmente, esto se puede hacer en el constructor del control). Si se especifica *hBlobDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de inicialización o serialización del control.

Los identificadores *hBlob* y *hBlobDefault* hacen referencia a un bloque de memoria que contiene lo siguiente:

- Un DWORD que contiene la longitud, en bytes, de los datos binarios que sigue, seguido inmediatamente por

- Un bloque de memoria que contiene los datos binarios reales.

Tenga `PX_Blob` en cuenta que asignará memoria, mediante la API [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) de Windows, al cargar propiedades de tipo BLOB. Usted es responsable de liberar esta memoria. Por lo tanto, el destructor del control debe llamar a [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) en cualquier identificador de propiedad de tipo BLOB para liberar la memoria asignada al control.

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo BOOL.

```cpp
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*bValor*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*bPredeterminado*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *bValue*, según corresponda. Si se especifica *bDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_color"></a><a name="px_color"></a>PX_Color

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo OLE_COLOR.

```cpp
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*clrValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*clrDefault*<br/>
Valor predeterminado de la propiedad, tal como lo define el desarrollador del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *clrValue*, según corresponda. Si se especifica *clrDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo **currency**.

```cpp
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*cyValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*cyDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *cyValue*, según corresponda. Si se especifica *cyDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de ruta de acceso de datos de tipo [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```cpp
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*dataPathProperty*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Las propiedades de ruta de acceso de datos implementan propiedades de control asincrónicas. El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *dataPathProperty*, según corresponda.

## <a name="px_double"></a><a name="px_double"></a>PX_Double

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo **double**.

```cpp
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*doubleValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*doubleDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *doubleValue*, según corresponda. Si se especifica *doubleDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_font"></a><a name="px_font"></a>PX_Font

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo font.

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*Fuente*<br/>
Una referencia `CFontHolder` a un objeto que contiene la propiedad font.

*pFontDesc*<br/>
Un puntero `FONTDESC` a una estructura que contiene los valores que se utilizarán para inicializar el estado predeterminado de la propiedad font, en el caso de *que pFontDispAmbient* sea NULL.

*pFontDispAmbient*<br/>
Puntero a `IFontDisp` la interfaz de una fuente que se usará para inicializar el estado predeterminado de la propiedad font.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se `font`lee `CFontHolder` o se escribe en , una referencia, cuando corresponda. Si se especifican *pFontDesc* y *pFontDispAmbient,* se usan para inicializar el valor predeterminado de la propiedad, cuando sea necesario. Estos valores se usan si, por cualquier motivo, se produce un error en el proceso de serialización del control. Normalmente, se pasa NULL para *pFontDesc* `COleControl::AmbientFont` y el valor ambiente devuelto por para *pFontDispAmbient*. Tenga en cuenta que `COleControl::AmbientFont` el objeto de fuente `IFontDisp::Release` devuelto por debe liberarse mediante una llamada a la función miembro.

## <a name="px_float"></a><a name="px_float"></a>PX_Float

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo **float**.

```cpp
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*floatValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*floatDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *floatValue*, según corresponda. Si se especifica *floatDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

Llame a esta función `DoPropExchange` dentro de la función miembro del control `IUnknown`para serializar o inicializar una propiedad representada por un objeto que tiene una interfaz derivada.

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*Punk*<br/>
Referencia a una variable que contiene la interfaz del objeto que representa el valor de la propiedad.

*Iid*<br/>
Un identificador de interfaz que indica qué interfaz del objeto de propiedad utiliza el control.

*pUnkDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *pUnk*, según corresponda. Si se especifica *pUnkDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_long"></a><a name="px_long"></a>PX_Long

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo **long**.

```cpp
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*lValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*lDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *lValue*, según corresponda. Si se especifica *lDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad picture del control.

```cpp
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*Pict*<br/>
Referencia a un [CPictureHolder](../../mfc/reference/cpictureholder-class.md) objeto donde se almacena la propiedad (normalmente una variable miembro de la clase).

*pictDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *pict*, según corresponda. Si se especifica *pictDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_short"></a><a name="px_short"></a>PX_Short

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo **short**.

```cpp
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*sValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*sDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *sValue*, según corresponda. Si se especifica *sDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo **ULONG**.

```cpp
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
Nombre de la propiedad que se está intercambiando.

*ulValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*ulDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *ulValue*, según corresponda. Si se especifica *ulDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de tipo **unsigned short**.

```cpp
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
Nombre de la propiedad que se está intercambiando.

*usValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*usDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *usValue*, según corresponda. Si se especifica *usDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="pxstring"></a><a name="px_string"></a>PXstring

Llame a esta función `DoPropExchange` dentro de la función miembro del control para serializar o inicializar una propiedad de cadena de caracteres.

```cpp
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*strValue*<br/>
Referencia a la variable donde se almacena la propiedad (normalmente una variable miembro de la clase).

*strDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *strValue*, según corresponda. Si se especifica *strDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en el proceso de serialización del control.

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Llame a esta función `DoPropExchange` dentro de la función miembro del control para inicializar una propiedad de fuente mediante la conversión de las propiedades relacionadas con la fuente de un control VBX.

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se `DoPropExchange`pasa como parámetro a ).

*Fuente*<br/>
Propiedad font del control OLE que contendrá las propiedades relacionadas con la fuente VBX convertidas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Esta función solo la debe usar un control OLE que esté diseñado como un reemplazo directo para un control VBX. Cuando el entorno de desarrollo de Visual Basic convierte un formulario que contiene un control `IDataObject::SetData` VBX para usar el control OLE de reemplazo correspondiente, llamará a la función del control, pasando un conjunto de propiedades que contiene los datos de propiedad del control VBX. Esta operación, a su vez, hace que se invoque la función del `DoPropExchange` control. `DoPropExchange`puede `PX_VBXFontConvert` llamar para convertir las propiedades relacionadas con la fuente del control VBX (por ejemplo, "FontName", "FontSize", etc.) en los componentes correspondientes de la propiedad font del control OLE.

`PX_VBXFontConvert`sólo debe llamarse cuando el control se está convirtiendo realmente desde una aplicación de formulario VBX. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Vea también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
