---
title: Persistencia de los controles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 42e70f9e48339eddb2a5af4fa288400cce01f490
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855776"
---
# <a name="persistence-of-ole-controls"></a>Persistencia de los controles OLE

Una funcionalidad de los controles OLE es la persistencia de propiedades (o la serialización), que permite al control OLE leer o escribir valores de propiedad en un archivo o una secuencia. Una aplicación contenedora puede usar la serialización para almacenar los valores de propiedad de un control incluso después de que la aplicación haya destruido el control. Los valores de propiedad del control OLE se pueden leer a continuación desde el archivo o el flujo cuando se crea una nueva instancia del control en un momento posterior.

### <a name="persistence-of-ole-controls"></a>Persistencia de los controles OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Intercambia una propiedad de control que almacena datos de objetos binarios grandes (BLOB).|
|[PX_Bool](#px_bool)|Intercambia una propiedad de control de tipo **bool**.|
|[PX_Color](#px_color)|Intercambia una propiedad de color de un control.|
|[PX_Currency](#px_currency)|Intercambia una propiedad de control de tipo **CY**.|
|[PX_DataPath](#px_datapath)|Intercambia una propiedad de control de tipo `CDataPathProperty`.|
|[PX_Double](#px_double)|Intercambia una propiedad de control de tipo **Double**.|
|[PX_Font](#px_font)|Intercambia una propiedad de fuente de un control.|
|[PX_Float](#px_float)|Intercambia una propiedad de control de tipo **float**.|
|[PX_IUnknown](#px_iunknown)|Intercambia una propiedad de control de tipo no definido.|
|[PX_Long](#px_long)|Intercambia una propiedad de control de tipo **Long**.|
|[PX_Picture](#px_picture)|Intercambia una propiedad de imagen de un control.|
|[PX_Short](#px_short)|Intercambia una propiedad de control de tipo **Short**.|
|[PX_ULong](#px_ulong)|Intercambia una propiedad de control de tipo **ULong**.|
|[PX_UShort](#px_ushort)|Intercambia una propiedad de control de tipo **USHORT**.|
|[PXstring](#px_string)|Intercambia una propiedad de control de cadena de caracteres.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Intercambia las propiedades relacionadas con la fuente de un control VBX en una propiedad Font de control OLE.|

Además, se proporciona la función global `AfxOleTypeMatchGuid` para comprobar si hay una coincidencia entre un TYPEDES y un GUID determinado.

##  <a name="px_blob"></a>PX_Blob

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad que almacena datos de objetos binarios grandes (BLOB).

```
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*hBlob*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*hBlobDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *hBlob*, según corresponda. Esta variable se debe inicializar en NULL antes de llamar inicialmente a `PX_Blob` por primera vez (normalmente, esto se puede hacer en el constructor del control). Si se especifica *hBlobDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en la inicialización o el proceso de serialización del control.

Los identificadores *hBlob* y *hBlobDefault* hacen referencia a un bloque de memoria que contiene lo siguiente:

- DWORD que contiene la longitud, en bytes, de los datos binarios siguientes, seguido inmediatamente de

- Bloque de memoria que contiene los datos binarios reales.

Tenga en cuenta que `PX_Blob` asignará memoria, mediante la API de [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) de Windows, al cargar propiedades de tipo de BLOB. Usted es responsable de liberar esta memoria. Por consiguiente, el destructor del control debe llamar a [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) en los identificadores de propiedad de tipo de BLOB para liberar cualquier memoria asignada al control.

##  <a name="px_bool"></a>PX_Bool

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo BOOL.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*bValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*bDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *bValue*, según corresponda. Si se especifica *bDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_color"></a>PX_Color

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo OLE_COLOR.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*clrValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*clrDefault*<br/>
Valor predeterminado de la propiedad, tal y como lo define el desarrollador del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *clrValue*, según corresponda. Si se especifica *clrDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_currency"></a>PX_Currency

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo **Currency**.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*cyValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*cyDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *cyValue*, según corresponda. Si se especifica *cyDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_datapath"></a>PX_DataPath

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de ruta de acceso de datos de tipo [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*dataPathProperty*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Las propiedades de ruta de acceso de datos implementan propiedades de control asincrónicas. El valor de la propiedad se leerá o escribirá en la variable a la que hace referencia *dataPathProperty*, según corresponda.

##  <a name="px_double"></a>PX_Double

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo **Double**.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*doubleValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*doubleDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *doubleValue*, según corresponda. Si se especifica *doubleDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_font"></a>PX_Font

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo Font.

```
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*tipo*<br/>
Referencia a un objeto `CFontHolder` que contiene la propiedad Font.

*pFontDesc*<br/>
Puntero a una estructura `FONTDESC` que contiene los valores que se van a usar para inicializar el estado predeterminado de la propiedad Font, en el caso de que *pFontDispAmbient* sea NULL.

*pFontDispAmbient*<br/>
Puntero a la interfaz `IFontDisp` de una fuente que se va a utilizar para inicializar el estado predeterminado de la propiedad Font.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en `font`, una referencia `CFontHolder`, si es necesario. Si se especifican *pFontDesc* y *pFontDispAmbient* , se usan para inicializar el valor predeterminado de la propiedad, cuando sea necesario. Estos valores se usan si, por cualquier motivo, se produce un error en el proceso de serialización del control. Normalmente, se pasa NULL para *pFontDesc* y el valor ambiente devuelto por `COleControl::AmbientFont` para *pFontDispAmbient*. Tenga en cuenta que el objeto de fuente devuelto por `COleControl::AmbientFont` debe liberarse mediante una llamada a la función miembro `IFontDisp::Release`.

##  <a name="px_float"></a>PX_Float

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo **float**.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*floatValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*floatDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *floatValue*, según corresponda. Si se especifica *floatDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_iunknown"></a>PX_IUnknown

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad representada por un objeto que tiene una interfaz derivada de `IUnknown`.

```
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*pUnk*<br/>
Referencia a una variable que contiene la interfaz del objeto que representa el valor de la propiedad.

*suscripto*<br/>
IDENTIFICADOR de interfaz que indica qué interfaz del objeto de propiedad utiliza el control.

*pUnkDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *pUnk*, según corresponda. Si se especifica *pUnkDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_long"></a>PX_Long

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo **Long**.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*Valor l*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*lDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *lValue*, según corresponda. Si se especifica *lDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_picture"></a>PX_Picture

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de imagen del control.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*PICT*<br/>
Referencia a un objeto [CPictureHolder](../../mfc/reference/cpictureholder-class.md) donde se almacena la propiedad (normalmente una variable miembro de la clase).

*pictDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *PICT*, según corresponda. Si se especifica *pictDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_short"></a>PX_Short

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo **Short**.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*sValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*sDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *sValue*, según corresponda. Si se especifica *sDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_ulong"></a>PX_ULong

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo **ULong**.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*ulValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*ulDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *ulValue*, según corresponda. Si se especifica *ulDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_ushort"></a>PX_UShort

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de tipo **Short sin signo**.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*usValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*usDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *usValue*, según corresponda. Si se especifica *usDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_string"></a>PXstring

Llame a esta función dentro de la función miembro `DoPropExchange` del control para serializar o inicializar una propiedad de cadena de caracteres.

```
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
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*strValue*<br/>
Referencia a la variable en la que se almacena la propiedad (normalmente una variable miembro de la clase).

*strDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en la variable a la que hace referencia *strValue*, según corresponda. Si se especifica *strDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en el proceso de serialización del control.

##  <a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Llame a esta función dentro de la función miembro de `DoPropExchange` del control para inicializar una propiedad de fuente convirtiendo las propiedades relacionadas con la fuente de un control VBX.

```
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parámetros

*pPX*<br/>
Puntero al objeto [CPropExchange](../../mfc/reference/cpropexchange-class.md) (normalmente se pasa como parámetro a `DoPropExchange`).

*tipo*<br/>
La propiedad Font del control OLE que contendrá las propiedades relacionadas con la fuente VBX convertidas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Esta función solo se debe usar en un control OLE diseñado como reemplazo directo de un control VBX. Cuando el entorno de desarrollo de Visual Basic convierte un formulario que contiene un control VBX para usar el control OLE de reemplazo correspondiente, llamará a la función de `IDataObject::SetData` del control y pasará un conjunto de propiedades que contenga los datos de la propiedad del control VBX. Esta operación, a su vez, hace que se invoque la función de `DoPropExchange` del control. `DoPropExchange` puede llamar a `PX_VBXFontConvert` para convertir las propiedades relacionadas con la fuente del control VBX (por ejemplo, "FontName", "FontSize", etc.) en los componentes correspondientes de la propiedad Font del control OLE.

solo se debe llamar a `PX_VBXFontConvert` cuando el control se está convirtiendo realmente desde una aplicación de formulario de VBX. Por ejemplo:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
