---
title: CPropExchange (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8b63de74a044a55362c2ebafc814fcf0136434d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216847"
---
# <a name="cpropexchange-class"></a>CPropExchange (clase)
Admite la implementación de persistencia para controles OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Intercambia una propiedad de objeto binario grande (BLOB).|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Intercambia una propiedad de fuente.|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Intercambia una propiedad de un control y un archivo.|  
|[CPropExchange::ExchangeProp](#exchangeprop)|Intercambia las propiedades de cualquier tipo integrado.|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|Intercambia el número de versión de un control OLE.|  
|[CPropExchange:: GetVersion](#getversion)|Recupera el número de versión de un control OLE.|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|Determina si los intercambios de propiedad se realizan asincrónicamente.|  
|[CPropExchange::IsLoading](#isloading)|Indica si se va las propiedades de carga en el control o se guardó desde él.|  
  
## <a name="remarks"></a>Comentarios  
 `CPropExchange` no tiene una clase base.  
  
 Establece el contexto y la dirección de un cambio de propiedad.  
  
 Persistencia es el intercambio de información de estado del control, que normalmente se representan mediante sus propiedades, entre el propio control y un medio.  
  
 El marco de trabajo construye un objeto derivado de `CPropExchange` cuando se notifica que son propiedades de un control OLE que se cargue desde o almacenamiento almacenado en persistente.  
  
 El marco de trabajo pasa un puntero a este `CPropExchange` objeto para el control `DoPropExchange` función. Si usa un Asistente para crear los archivos de inicio para el control, el control `DoPropExchange` llamadas de función `COleControl::DoPropExchange`. La versión de la clase base intercambia las propiedades del control estándar; modificar la versión de la clase derivada a propiedades de exchange que ha agregado al control.  
  
 `CPropExchange` puede usarse para serializar las propiedades de un control o inicializar las propiedades de un control durante la carga o la creación de un control. El `ExchangeProp` y `ExchangeFontProp` funciones miembro de `CPropExchange` pueden almacenar propiedades a y cargarlos desde un medio diferente.  
  
 Para obtener más información sobre el uso de `CPropExchange`, consulte el artículo [controles ActiveX MFC: páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CPropExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="exchangeblobprop"></a>  CPropExchange::ExchangeBlobProp  
 Serializa una propiedad que almacena los datos de objeto binario grande (BLOB).  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pszPropName*  
 El nombre de la propiedad que se intercambian.  
  
 *phBlob*  
 Puntero a una variable que apunta a donde se almacena la propiedad (la variable normalmente es un miembro de la clase).  
  
 *hBlobDefault*  
 Valor predeterminado para la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el intercambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad es de lectura o escrito a, según corresponda, la variable al que hace referencia *phBlob*. Si *hBlobDefault* se especifica, se usará como valor predeterminado de la propiedad. Este valor se utiliza si, por cualquier motivo, la serialización del control se produce un error.  
  
 Las funciones `CArchivePropExchange::ExchangeBlobProp`, `CResetPropExchange::ExchangeBlobProp`, y `CPropsetPropExchange::ExchangeBlobProp` reemplazar esta función virtual pura.  
  
##  <a name="exchangefontprop"></a>  CPropExchange::ExchangeFontProp  
 Intercambia entre un medio de almacenamiento y el control de una propiedad de fuente.  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pszPropName*  
 El nombre de la propiedad que se intercambian.  
  
 *fuente*  
 Una referencia a un [CFontHolder](../../mfc/reference/cfontholder-class.md) objeto que contiene la propiedad font.  
  
 *pFontDesc*  
 Un puntero a un [FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc) estructura que contiene los valores para inicializar el estado predeterminado de la propiedad font cuando *pFontDispAmbient* es NULL.  
  
 *pFontDispAmbient*  
 Un puntero a la `IFontDisp` interfaz de una fuente que se utilizará para inicializar el estado predeterminado de la propiedad font.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el intercambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Si se carga desde el medio de la propiedad font al control, características de la fuente se recuperan desde el medio y la `CFontHolder` hacen referencia al objeto *fuente* se inicializa con ellos. Si se va a almacenar la propiedad font, las características en el objeto de fuente se escriben en el medio.  
  
 Las funciones `CArchivePropExchange::ExchangeFontProp`, `CResetPropExchange::ExchangeFontProp`, y `CPropsetPropExchange::ExchangeFontProp` reemplazar esta función virtual pura.  
  
##  <a name="exchangepersistentprop"></a>  CPropExchange::ExchangePersistentProp  
 Intercambia una propiedad entre el control y un archivo.  
  
```  
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,  
    LPUNKNOWN* ppUnk,  
    REFIID iid,  
    LPUNKNOWN pUnkDefault) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pszPropName*  
 El nombre de la propiedad que se intercambian.  
  
 *ppUnk*  
 Un puntero a una variable que contiene un puntero a la propiedad `IUnknown` interfaz (esta variable es normalmente un miembro de la clase).  
  
 *IID*  
 Id. de interfaz de la interfaz en la propiedad que se va a usar el control.  
  
 *pUnkDefault*  
 Valor predeterminado para la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el intercambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Si la propiedad se está cargando desde el archivo al control, la propiedad se crea e inicializa desde el archivo. Si se va a almacenar la propiedad, su valor se escribe en el archivo.  
  
 Las funciones `CArchivePropExchange::ExchangePersistentProp`, `CResetPropExchange::ExchangePersistentProp`, y `CPropsetPropExchange::ExchangePersistentProp` reemplazar esta función virtual pura.  
  
##  <a name="exchangeprop"></a>  CPropExchange::ExchangeProp  
 Intercambia una propiedad de un medio de almacenamiento y el control.  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pszPropName*  
 El nombre de la propiedad que se intercambian.  
  
 *vtProp*  
 Un símbolo que especifica el tipo de la propiedad que se intercambian. Los valores posibles son:  
  
|Símbolo|Tipo de propiedad|  
|------------|-------------------|  
|VT_I2|**short**|  
|VT_I4|**long**|  
|VT_BOOL|**BOOL**|  
|VT_BSTR|`CString`|  
|VT_CY|**CY**|  
|VT_R4|**float**|  
|VT_R8|**double**|  
  
 *pvProp*  
 Puntero al valor de la propiedad.  
  
 *pvDefault*  
 Puntero a un valor predeterminado para la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el intercambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Si se carga desde el medio de la propiedad al control, el valor de propiedad se recuperan desde el medio de y almacenado en el objeto al que señala *pvProp*. Si la propiedad se va a almacenar en el medio, el valor del objeto que apunta *pvProp* se escribe en el medio.  
  
 Las funciones `CArchivePropExchange::ExchangeProp`, `CResetPropExchange::ExchangeProp`, y `CPropsetPropExchange::ExchangeProp` reemplazar esta función virtual pura.  
  
##  <a name="exchangeversion"></a>  CPropExchange::ExchangeVersion  
 Lo llama el marco de trabajo para controlar la persistencia de un número de versión.  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwVersionLoaded*  
 Referencia a una variable donde se almacenará el número de versión de los datos persistentes que se está cargados.  
  
 *dwVersionDefault*  
 El número de versión actual del control.  
  
 *bConvert*  
 Indica si se debe convertir los datos persistentes a la versión actual o que se mantenga en la misma versión que se cargó.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.  
  
##  <a name="getversion"></a>  CPropExchange:: GetVersion  
 Llame a esta función para recuperar el número de versión del control.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de versión del control.  
  
##  <a name="isasynchronous"></a>  CPropExchange::IsAsynchronous  
 Determina si los intercambios de propiedad se realizan asincrónicamente.  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si las propiedades intercambia de forma asincrónica, lo contrario, FALSE.  
  
##  <a name="isloading"></a>  CPropExchange::IsLoading  
 Llame a esta función para determinar si se va las propiedades de carga para el control o guarda de él.  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se van a cargar las propiedades; en caso contrario, es 0.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)



