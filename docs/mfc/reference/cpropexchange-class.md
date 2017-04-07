---
title: Clase CPropExchange | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CPropExchange class
- OLE controls, persistence
- controls [MFC], OLE
ms.assetid: ed872180-e770-4942-892a-92139d501fab
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 655d8e2f074c3bd12b1b52ece74efb844c7a9904
ms.lasthandoff: 02/24/2017

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
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Cambia una propiedad de objeto binario grande (BLOB).|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Cambia una propiedad de fuente.|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Cambia una propiedad de un control y un archivo.|  
|[CPropExchange::ExchangeProp](#exchangeprop)|Intercambia las propiedades de cualquier tipo integrado.|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|Intercambia el número de versión de un control OLE.|  
|[CPropExchange:: GetVersion](#getversion)|Recupera el número de versión de un control OLE.|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|Determina si los intercambios de propiedad se realizan asincrónicamente.|  
|[CPropExchange::IsLoading](#isloading)|Indica si se va propiedades cargado en el control o guardado de él.|  
  
## <a name="remarks"></a>Comentarios  
 `CPropExchange`no tiene una clase base.  
  
 Establece el contexto y la dirección de un cambio de propiedad.  
  
 La persistencia es el intercambio de información de estado del control, que normalmente se representan mediante sus propiedades, entre el control y un medio.  
  
 El marco de trabajo construye un objeto derivado de `CPropExchange` cuando se notifica que son propiedades de un control OLE que cargarse desde o almacenamiento almacenado en persistente.  
  
 El marco de trabajo pasa un puntero a este `CPropExchange` objeto para el control `DoPropExchange` (función). Si utiliza un Asistente para crear los archivos de inicio para el control, el control `DoPropExchange` llamadas a funciones `COleControl::DoPropExchange`. La versión de la clase base intercambia las propiedades del control stock; modificar la versión de la clase derivada a propiedades de exchange que ha agregado al control.  
  
 `CPropExchange`puede utilizarse para serializar las propiedades de un control o inicializar las propiedades de un control durante la carga o la creación de un control. El `ExchangeProp` y `ExchangeFontProp` funciones miembro de `CPropExchange` pueden almacenar propiedades y cargarlos desde un medio diferente.  
  
 Para obtener más información sobre el uso de `CPropExchange`, vea el artículo [controles ActiveX de MFC: páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CPropExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp  
 Serializa una propiedad que almacena datos de objeto binario grande (BLOB).  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `phBlob`  
 Puntero a una variable que apunta a donde se almacena la propiedad (variable normalmente es un miembro de la clase).  
  
 `hBlobDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad es de lectura o escrito a, según corresponda, la variable hace referencia a `phBlob`. Si `hBlobDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, la serialización del control se produce un error.  
  
 Las funciones **CArchivePropExchange::ExchangeBlobProp**, **CResetPropExchange::ExchangeBlobProp**, y **CPropsetPropExchange::ExchangeBlobProp** reemplazar esta función virtual pura.  
  
##  <a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp  
 Cambia una propiedad de fuente entre un medio de almacenamiento y el control.  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `font`  
 Una referencia a un [CFontHolder](../../mfc/reference/cfontholder-class.md) objeto que contiene la propiedad font.  
  
 `pFontDesc`  
 Un puntero a un [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782) estructura que contiene los valores para inicializar el estado predeterminado de la propiedad font cuando `pFontDispAmbient` es **NULL**.  
  
 `pFontDispAmbient`  
 Un puntero a la **IFontDisp** interfaz de una fuente que se utilizará para inicializar el estado predeterminado de la propiedad font.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Si se carga desde el medio de la propiedad font para el control, las características de la fuente se recuperan desde el medio y la `CFontHolder` hacen referencia al objeto `font` se inicializa con ellos. Si se va a almacenar la propiedad font, las características en el objeto de fuente se escriben en el medio.  
  
 Las funciones **CArchivePropExchange::ExchangeFontProp**, **CResetPropExchange::ExchangeFontProp**, y **CPropsetPropExchange::ExchangeFontProp** reemplazar esta función virtual pura.  
  
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
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `ppUnk`  
 Un puntero a una variable que contiene un puntero a la propiedad **IUnknown** interfaz (esta variable normalmente es un miembro de la clase).  
  
 `iid`  
 Identificador de interfaz de la interfaz en la propiedad que se va a utilizar el control.  
  
 `pUnkDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Si la propiedad se está cargando desde el archivo al control, la propiedad se crea y se inicializa desde el archivo. Si se va a almacenar la propiedad, su valor se escribe en el archivo.  
  
 Las funciones **CArchivePropExchange::ExchangePersistentProp**, **CResetPropExchange::ExchangePersistentProp**, y **CPropsetPropExchange::ExchangePersistentProp** reemplazar esta función virtual pura.  
  
##  <a name="exchangeprop"></a>CPropExchange::ExchangeProp  
 Cambia una propiedad de un medio de almacenamiento y el control.  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `vtProp`  
 Un símbolo que especifica el tipo de la propiedad que se intercambian. Los valores posibles son:  
  
|Símbolo|Tipo de propiedad|  
|------------|-------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_BOOL`|**BOOL**|  
|`VT_BSTR`|`CString`|  
|`VT_CY`|**CY**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
  
 `pvProp`  
 Puntero al valor de la propiedad.  
  
 *pvDefault*  
 Puntero a un valor predeterminado para la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Si se carga desde el medio de la propiedad al control, el valor de propiedad es recuperado desde el medio y almacenado en el objeto al que señala `pvProp`. Si la propiedad se va a almacenar en el medio, el valor del objeto indicado por `pvProp` se escribe en el medio.  
  
 Las funciones **CArchivePropExchange::ExchangeProp**, **CResetPropExchange::ExchangeProp**, y **CPropsetPropExchange::ExchangeProp** reemplazar esta función virtual pura.  
  
##  <a name="exchangeversion"></a>CPropExchange::ExchangeVersion  
 Llamado por el marco de trabajo para controlar la persistencia de un número de versión.  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwVersionLoaded*  
 Referencia a una variable donde se almacenará el número de versión de los datos persistentes que se está cargados.  
  
 `dwVersionDefault`  
 El número de versión actual del control.  
  
 `bConvert`  
 Indica si se debe convertir los datos persistentes en la versión actual o mantenerlo en la misma versión que se cargó.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la función se realiza correctamente; en caso contrario, es 0.  
  
##  <a name="getversion"></a>CPropExchange:: GetVersion  
 Llame a esta función para recuperar el número de versión del control.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de versión del control.  
  
##  <a name="isasynchronous"></a>CPropExchange::IsAsynchronous  
 Determina si los intercambios de propiedad se realizan asincrónicamente.  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si son propiedades de forma asincrónica, intercambia lo contrario, FALSE.  
  
##  <a name="isloading"></a>CPropExchange::IsLoading  
 Llame a esta función para determinar si se están propiedades cargadas en el control o guardado de él.  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se cargan las propiedades; en caso contrario, 0.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [COleControl:: DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)




