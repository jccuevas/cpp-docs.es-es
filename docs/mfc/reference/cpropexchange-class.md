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
ms.openlocfilehash: 7818b15e502bb32640d6b9dbfe1a6e4927c70650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363989"
---
# <a name="cpropexchange-class"></a>Clase CPropExchange

Admite la implementación de persistencia para controles OLE.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Intercambia una propiedad de objeto binario grande (BLOB).|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Intercambia una propiedad de fuente.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Intercambia una propiedad entre un control y un archivo.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Intercambia propiedades de cualquier tipo integrado.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Intercambia el número de versión de un control OLE.|
|[CPropExchange::GetVersion](#getversion)|Recupera el número de versión de un control OLE.|
|[CpropExchange::Isasynchronous](#isasynchronous)|Determina si los intercambios de propiedades se realizan de forma asincrónica.|
|[CpropExchange::IsLoading](#isloading)|Indica si las propiedades se cargan en el control o se guardan desde él.|

## <a name="remarks"></a>Observaciones

`CPropExchange`no tiene una clase base.

Establece el contexto y la dirección de un intercambio de propiedades.

La persistencia es el intercambio de la información de estado del control, normalmente representada por sus propiedades, entre el propio control y un medio.

El marco de trabajo construye `CPropExchange` un objeto derivado de cuando se notifica que las propiedades de un control OLE se van a cargar o almacenar en el almacenamiento persistente.

El marco de trabajo `CPropExchange` pasa un puntero `DoPropExchange` a este objeto a la función del control. Si usó un asistente para crear los archivos de `DoPropExchange` inicio `COleControl::DoPropExchange`para el control, la función del control llama . La versión de clase base intercambia las propiedades de stock del control; Modificar la versión de la clase derivada para intercambiar las propiedades que ha agregado al control.

`CPropExchange`se puede usar para serializar las propiedades de un control o inicializar las propiedades de un control al cargar o crear un control. Las `ExchangeProp` `ExchangeFontProp` funciones `CPropExchange` miembro y de los miembros pueden almacenar propiedades y cargarlas desde diferentes medios.

Para obtener más `CPropExchange`información sobre el uso , vea el artículo Controles ActiveX de [MFC: Páginas](../../mfc/mfc-activex-controls-property-pages.md)de propiedades .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CPropExchange`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Serializa una propiedad que almacena datos de objetos binarios grandes (BLOB).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parámetros

*pszPropName*<br/>
El nombre de la propiedad que se está intercambiando.

*phBlob*<br/>
Puntero a una variable que apunta a donde se almacena la propiedad (variable suele ser un miembro de la clase).

*hBlobDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El valor de la propiedad se lee o se escribe en, según corresponda, en la variable a la que hace *referencia phBlob*. Si se especifica *hBlobDefault,* se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, se produce un error en la serialización del control.

Las `CArchivePropExchange::ExchangeBlobProp`funciones `CResetPropExchange::ExchangeBlobProp` `CPropsetPropExchange::ExchangeBlobProp` , , e invalidan esta función virtual pura.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

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
El nombre de la propiedad que se está intercambiando.

*Fuente*<br/>
Una referencia a un [CFontHolder](../../mfc/reference/cfontholder-class.md) objeto que contiene la propiedad font.

*pFontDesc*<br/>
Un puntero a una estructura [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc) que contiene valores para inicializar el estado predeterminado de la propiedad font cuando *pFontDispAmbient* es NULL.

*pFontDispAmbient*<br/>
Puntero a `IFontDisp` la interfaz de una fuente que se usará para inicializar el estado predeterminado de la propiedad font.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Si la propiedad font se carga desde el medio al control, las características `CFontHolder` de la fuente se recuperan del medio y el objeto al que hace referencia la *fuente* se inicializa con ellas. Si se almacena la propiedad font, las características del objeto de fuente se escriben en el medio.

Las `CArchivePropExchange::ExchangeFontProp`funciones `CResetPropExchange::ExchangeFontProp` `CPropsetPropExchange::ExchangeFontProp` , , e invalidan esta función virtual pura.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

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
El nombre de la propiedad que se está intercambiando.

*ppUnk*<br/>
Un puntero a una variable que contiene `IUnknown` un puntero a la interfaz de la propiedad (esta variable suele ser un miembro de la clase).

*Iid*<br/>
Identificador de interfaz de la interfaz en la propiedad que utilizará el control.

*pUnkDefault*<br/>
Valor predeterminado de la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Si la propiedad se carga desde el archivo al control, la propiedad se crea e inicializa desde el archivo. Si la propiedad se almacena, su valor se escribe en el archivo.

Las `CArchivePropExchange::ExchangePersistentProp`funciones `CResetPropExchange::ExchangePersistentProp` `CPropsetPropExchange::ExchangePersistentProp` , , e invalidan esta función virtual pura.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp

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
El nombre de la propiedad que se está intercambiando.

*vtProp*<br/>
Símbolo que especifica el tipo de la propiedad que se está intercambiando. Los valores posibles son:

|Símbolo|Tipo de propiedad|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**Largo**|
|VT_BOOL|**Bool**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**Flotador**|
|VT_R8|**double**|

*pvProp*<br/>
Un puntero al valor de la propiedad.

*pvDefault*<br/>
Puntero a un valor predeterminado para la propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el intercambio se realizó correctamente; 0 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Si la propiedad se carga desde el medio al control, el valor de la propiedad se recupera del medio y se almacena en el objeto al que apunta *pvProp*. Si la propiedad se almacena en el medio, el valor del objeto al que apunta *pvProp* se escribe en el medio.

Las `CArchivePropExchange::ExchangeProp`funciones `CResetPropExchange::ExchangeProp` `CPropsetPropExchange::ExchangeProp` , , e invalidan esta función virtual pura.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Llamado por el marco de trabajo para controlar la persistencia de un número de versión.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parámetros

*dwVersionLoaded*<br/>
Referencia a una variable donde se almacenará el número de versión de los datos persistentes que se están cargando.

*dwVersionDefault*<br/>
El número de versión actual del control.

*bConvertir*<br/>
Indica si se deben convertir datos persistentes a la versión actual o mantenerlos en la misma versión que se cargó.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; 0 en caso contrario.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange::GetVersion

Llame a esta función para recuperar el número de versión del control.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valor devuelto

El número de versión del control.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CpropExchange::Isasynchronous

Determina si los intercambios de propiedades se realizan de forma asincrónica.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si las propiedades se intercambian de forma asincrónica, de lo contrario FALSE.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CpropExchange::IsLoading

Llame a esta función para determinar si las propiedades se cargan en el control o se guardan desde él.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se están cargando propiedades; de lo contrario 0.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
