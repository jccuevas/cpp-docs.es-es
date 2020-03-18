---
title: Clase CPropExchange
ms.date: 11/04/2016
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
ms.openlocfilehash: e9ad7c363f2580200af20baeb0acd7a93c1f603b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426406"
---
# <a name="cpropexchange-class"></a>Clase CPropExchange

Admite la implementación de persistencia para controles OLE.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Intercambia una propiedad de objeto binario grande (BLOB).|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Intercambia una propiedad de fuente.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Intercambia una propiedad entre un control y un archivo.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Intercambia propiedades de cualquier tipo integrado.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Intercambia el número de versión de un control OLE.|
|[CPropExchange:: GetVersion](#getversion)|Recupera el número de versión de un control OLE.|
|[CPropExchange:: cuya IsAsynchronous](#isasynchronous)|Determina si los intercambios de propiedad se realizan de forma asincrónica.|
|[CPropExchange:: IsLoading](#isloading)|Indica si las propiedades se cargan o se guardan en el control.|

## <a name="remarks"></a>Observaciones

`CPropExchange` no tiene una clase base.

Establece el contexto y la dirección de un intercambio de propiedades.

La persistencia es el intercambio de la información de estado del control, normalmente representada por sus propiedades, entre el propio control y un medio.

El marco de trabajo crea un objeto derivado de `CPropExchange` cuando se le notifica que las propiedades de un control OLE se van a cargar o almacenar en un almacenamiento persistente.

El marco de trabajo pasa un puntero a este objeto `CPropExchange` a la función de `DoPropExchange` del control. Si usó un asistente para crear los archivos de inicio para el control, la función `DoPropExchange` del control llama a `COleControl::DoPropExchange`. La versión de la clase base intercambia las propiedades estándar del control. modifique la versión de la clase derivada para intercambiar las propiedades que ha agregado al control.

`CPropExchange` puede usarse para serializar las propiedades de un control o para inicializar las propiedades de un control al cargar o crear un control. Las funciones miembro `ExchangeProp` y `ExchangeFontProp` de `CPropExchange` pueden almacenar propiedades y cargarlas desde distintos medios.

Para obtener más información sobre el uso de `CPropExchange`, vea el artículo [controles ActiveX MFC: páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CPropExchange`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl. h

##  <a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Serializa una propiedad que almacena los datos de objetos binarios grandes (BLOB).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parámetros

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*phBlob*<br/>
Puntero a una variable que apunta a donde se almacena la propiedad (la variable suele ser un miembro de la clase).

*hBlobDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en, según corresponda, la variable a la que hace referencia *phBlob*. Si se especifica *hBlobDefault* , se usará como valor predeterminado de la propiedad. Este valor se usa si, por cualquier motivo, se produce un error en la serialización del control.

Las funciones `CArchivePropExchange::ExchangeBlobProp`, `CResetPropExchange::ExchangeBlobProp`y `CPropsetPropExchange::ExchangeBlobProp` invalidan esta función virtual pura.

##  <a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

Intercambia una propiedad de fuente entre un medio de almacenamiento y el control.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Parámetros

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*tipo*<br/>
Referencia a un objeto [CFontHolder](../../mfc/reference/cfontholder-class.md) que contiene la propiedad Font.

*pFontDesc*<br/>
Puntero a una estructura [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc) que contiene valores para inicializar el estado predeterminado de la propiedad de fuente cuando *pFontDispAmbient* es NULL.

*pFontDispAmbient*<br/>
Puntero a la interfaz `IFontDisp` de una fuente que se va a utilizar para inicializar el estado predeterminado de la propiedad Font.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Si la propiedad Font se carga desde el medio al control, las características de la fuente se recuperan del medio y el objeto `CFontHolder` al que hace referencia la *fuente* se inicializa con ellas. Si se está almacenando la propiedad Font, las características del objeto Font se escriben en el medio.

Las funciones `CArchivePropExchange::ExchangeFontProp`, `CResetPropExchange::ExchangeFontProp`y `CPropsetPropExchange::ExchangeFontProp` invalidan esta función virtual pura.

##  <a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

Intercambia una propiedad entre el control y un archivo.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>Parámetros

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*ppUnk*<br/>
Puntero a una variable que contiene un puntero a la interfaz `IUnknown` de la propiedad (esta variable normalmente es un miembro de la clase).

*suscripto*<br/>
IDENTIFICADOR de interfaz de la interfaz en la propiedad que utilizará el control.

*pUnkDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Si la propiedad se carga desde el archivo en el control, la propiedad se crea y se inicializa a partir del archivo. Si se está almacenando la propiedad, su valor se escribe en el archivo.

Las funciones `CArchivePropExchange::ExchangePersistentProp`, `CResetPropExchange::ExchangePersistentProp`y `CPropsetPropExchange::ExchangePersistentProp` invalidan esta función virtual pura.

##  <a name="exchangeprop"></a>CPropExchange::ExchangeProp

Intercambia una propiedad entre un medio de almacenamiento y el control.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Parámetros

*pszPropName*<br/>
Nombre de la propiedad que se va a intercambiar.

*vtProp*<br/>
Símbolo que especifica el tipo de la propiedad que se va a intercambiar. Los valores posibles son:

|Símbolo|Tipo de propiedad|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_BOOL|**BOOL**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**float**|
|VT_R8|**double**|

*pvProp*<br/>
Puntero al valor de la propiedad.

*pvDefault*<br/>
Puntero a un valor predeterminado para la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Si la propiedad se carga desde el medio en el control, el valor de la propiedad se recupera del medio y se almacena en el objeto al que apunta *pvProp*. Si la propiedad se está almacenando en el medio, el valor del objeto al que apunta *pvProp* se escribe en el medio.

Las funciones `CArchivePropExchange::ExchangeProp`, `CResetPropExchange::ExchangeProp`y `CPropsetPropExchange::ExchangeProp` invalidan esta función virtual pura.

##  <a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Lo llama el marco de trabajo para controlar la persistencia de un número de versión.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parámetros

*dwVersionLoaded*<br/>
Referencia a una variable en la que se almacenará el número de versión de los datos persistentes que se van a cargar.

*dwVersionDefault*<br/>
Número de versión actual del control.

*bConvert*<br/>
Indica si se deben convertir los datos persistentes a la versión actual o mantenerlos en la misma versión que se cargó.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; 0 en caso contrario.

##  <a name="getversion"></a>CPropExchange:: GetVersion

Llame a esta función para recuperar el número de versión del control.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valor devuelto

Número de versión del control.

##  <a name="isasynchronous"></a>CPropExchange:: cuya IsAsynchronous

Determina si los intercambios de propiedad se realizan de forma asincrónica.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si las propiedades se intercambian de forma asincrónica; de lo contrario, es FALSE.

##  <a name="isloading"></a>CPropExchange:: IsLoading

Llame a esta función para determinar si las propiedades se cargan o se guardan en el control.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se cargan las propiedades; de lo contrario, es 0.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControl::D oPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
