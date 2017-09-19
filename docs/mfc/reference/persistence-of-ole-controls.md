---
title: Persistencia de los controles OLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE controls, persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b8bbf72a1ea16b37dabf88c5d41a34b1a03ba0d1
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="persistence-of-ole-controls"></a>Persistencia de los controles OLE
Una capacidad de controles OLE es la persistencia de propiedad (o serialización), lo que permite el control OLE leer o escribir valores de propiedad a y desde un archivo o secuencia. Una aplicación contenedora puede utilizar la serialización para almacenar valores de propiedad de un control incluso después de que la aplicación ha destruido el control. Los valores de propiedad del control OLE se puede leer desde el archivo o secuencia cuando una nueva instancia del control se crea en un momento posterior.  
  
### <a name="persistence-of-ole-controls"></a>Persistencia de los controles OLE  
  
|||  
|-|-|  
|[PX_Blob](#px_blob)|Cambia una propiedad de control que almacena datos de objeto binario grande (BLOB).|  
|[PX_Bool](#px_bool)|Intercambia una propiedad de control de tipo **BOOL**.|  
|[PX_Color](#px_color)|Cambia una propiedad de color de un control.|  
|[PX_Currency](#px_currency)|Intercambia una propiedad de control de tipo **CY**.|  
|[PX_DataPath](#px_datapath)|Intercambia una propiedad de control de tipo `CDataPathProperty`.|  
|[PX_Double](#px_double)|Intercambia una propiedad de control de tipo **doble**.|  
|[PX_Font](#px_font)|Cambia una propiedad de fuente de un control.|  
|[PX_Float](#px_float)|Intercambia una propiedad de control de tipo **float**.|  
|[PX_IUnknown](#px_iunknown)|Cambia una propiedad de control de un tipo no definido.|  
|[PX_Long](#px_long)|Intercambia una propiedad de control de tipo **largo**.|  
|[PX_Picture](#px_picture)|Cambia una propiedad de imagen de un control.|  
|[PX_Short](#px_short)|Intercambia una propiedad de control de tipo **breve**.|  
|[PX_ULong](#px_ulong)|Intercambia una propiedad de control de tipo **ULONG**.|  
|[PX_UShort](#px_ushort)|Intercambia una propiedad de control de tipo **USHORT**.|  
|[PXstring](#px_string)|Cambia una propiedad de control de la cadena de caracteres.|  
|[PX_VBXFontConvert](#px_vbxfontconvert)|Intercambia VBX relacionadas con la fuente propiedades de un control en una propiedad de fuente del control OLE.|  
  
 Además, el `AfxOleTypeMatchGuid` se proporciona una función global para buscar una coincidencia entre un `TYPEDESC` y un GUID determinado.  
  
##  <a name="px_blob"></a>PX_Blob  
 Llame a esta función dentro del control `DoPropExchange` la función miembro para serializar o inicializar una propiedad que almacena datos de objeto binario grande (BLOB).  
  
```  
 
BOOL  
PX_Blob(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    HGLOBAL& 
hBlob  ,  
    HGLOBAL 
hBlobDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `hBlob`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `hBlobDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leer o escribir en la variable hace referencia a `hBlob`, según corresponda. Esta variable se debe inicializar para **NULL** antes de llamar inicialmente `PX_Blob` por primera vez (normalmente, esto puede hacerse en el constructor del control). Si `hBlobDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización o de inicialización del control.  
  
 Los controladores de `hBlob` y `hBlobDefault` hacen referencia a un bloque de memoria que contiene lo siguiente:  
  
-   Un `DWORD` que contiene la longitud, en bytes, de los datos binarios que sigue, seguido inmediatamente  
  
-   Un bloque de memoria que contiene los datos binarios reales.  
  
 Tenga en cuenta que `PX_Blob` asignará memoria, utilizando las ventanas de [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) API, al cargar las propiedades de tipo BLOB. Es responsable de liberar esta memoria. Por lo tanto, debe llamar al destructor del control de [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) en cualquier propiedad de tipo BLOB identificadores para liberar hasta cualquier memoria asignada al control.  
  
##  <a name="px_bool"></a>PX_Bool  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **BOOL**.  
  
```  
 
BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& bValue);

BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& 
bValue  ,  
    BOOL bDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `bValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `bDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leer o escribir en la variable hace referencia a `bValue`, según corresponda. Si `bDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_color"></a>PX_Color  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **OLE_COLOR**.  
  
```  
 
BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& 
clrValue  ,  
    OLE_COLOR 
clrDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `clrValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `clrDefault`  
 Valor predeterminado de la propiedad definida por el desarrollador del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leer o escribir en la variable hace referencia a `clrValue`, según corresponda. Si `clrDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_currency"></a>PX_Currency  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **moneda**.  
  
```  
 
BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& cyValue);

BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& 
cyValue  ,  
    CY cyDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `cyValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `cyDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leer o escribir en la variable hace referencia a `cyValue`, según corresponda. Si `cyDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_datapath"></a>PX_DataPath  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de ruta de acceso de datos de tipo [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).  
  
```  
 
BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    LPCTSTR 
pszPropName,  
    CDataPathProperty& dataPathProperty);

BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    CDataPathProperty& dataPathProperty);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `dataPathProperty`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Propiedades de la ruta de acceso de datos implementan propiedades de control asincrónico. Valor de la propiedad se leer o escribir en la variable hace referencia a `dataPathProperty`, según corresponda.  
  
##  <a name="px_double"></a>PX_Double  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **doble**.  
  
```  
 
BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& doubleValue);

BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& 
doubleValue  ,  
    double doubleDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `doubleValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `doubleDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a `doubleValue`, según corresponda. Si `doubleDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_font"></a>PX_Font  
 Llame a esta función dentro del control `DoPropExchange` la función miembro para serializar o inicializar una propiedad de fuente de tipo.  
  
```  
 
BOOL  
PX_Font(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CFontHolder& 
font  ,  
    const 
FONTDESC  
FAR* 
pFontDesc  
= 
NULL,  
    LPFONTDISP 
pFontDispAmbient  
= NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `font`  
 Una referencia a un `CFontHolder` objeto que contiene la propiedad font.  
  
 `pFontDesc`  
 Un puntero a un **FONTDESC** estructura que contiene los valores para utilizar al inicializar el estado predeterminado de la propiedad de fuente, en el caso donde `pFontDispAmbient` es **NULL**.  
  
 `pFontDispAmbient`  
 Un puntero a la **IFontDisp** interfaz de una fuente que se utilizará al inicializar el estado predeterminado de la propiedad font.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en `font`, un `CFontHolder` de referencia, cuando sea necesario. Si `pFontDesc` y `pFontDispAmbient` se especifica, se utilizan para inicializar el valor de la propiedad predeterminado, cuando sea necesario. Estos valores se usan si, por alguna razón, falla el proceso de serialización del control. Normalmente, se pasa **NULL** de `pFontDesc` y el valor ambiente devuelto por `COleControl::AmbientFont` para `pFontDispAmbient`. Tenga en cuenta que el objeto de fuente devuelto por `COleControl::AmbientFont` debe liberarse mediante una llamada a la **IFontDisp::Release** función miembro.  
  
##  <a name="px_float"></a>PX_Float  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **float**.  
  
```  
 
BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& floatValue);

BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& 
floatValue  ,  
    float floatDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `floatValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `floatDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a `floatValue`, según corresponda. Si `floatDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_iunknown"></a>PX_IUnknown  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad representada por un objeto con un **IUnknown**-interfaz derivada.  
  
```  
 
BOOL  
PX_IUnknown(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    LPUNKNOWN& 
pUnk  ,  
    REFIID 
iid  ,  
    LPUNKNOWN 
pUnkDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 *pUnk*  
 Referencia a una variable que contiene la interfaz del objeto que representa el valor de la propiedad.  
  
 `iid`  
 Un identificador de interfaz que indica qué interfaz del objeto de propiedad se utiliza el control.  
  
 `pUnkDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a *pUnk*, según corresponda. Si `pUnkDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_long"></a>PX_Long  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **largo**.  
  
```  
 
BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& lValue);

BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& 
lValue  ,  
    long lDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `lValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `lDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a `lValue`, según corresponda. Si `lDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_picture"></a>PX_Picture  
 Llame a esta función dentro del control `DoPropExchange` la función miembro para serializar o inicializar una propiedad de imagen del control.  
  
```  
 
BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& pict);

BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& 
pict  ,  
    CPictureHolder& pictDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `pict`  
 Hacer referencia a un [CPictureHolder](../../mfc/reference/cpictureholder-class.md) donde se almacena la propiedad de objeto (normalmente, una variable miembro de la clase).  
  
 `pictDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a `pict`, según corresponda. Si `pictDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_short"></a>PX_Short  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **breve**.  
  
```  
 
BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& sValue);

BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& 
sValue  ,  
    short sDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `sValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `sDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a `sValue`, según corresponda. Si `sDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_ulong"></a>PX_ULong  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo **ULONG**.  
  
```  
 
BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& ulValue);

BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& 
ulValue  ,  
    long ulDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 Nombre de la propiedad que se intercambian.  
  
 `ulValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `ulDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a `ulValue`, según corresponda. Si `ulDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_ushort"></a>PX_UShort  
 Llame a esta función dentro del control `DoPropExchange` función miembro para serializar o inicializar una propiedad de tipo `unsigned` **breve**.  
  
```  
 
BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& usValue);

BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& 
usValue  ,  
    USHORT usDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 Nombre de la propiedad que se intercambian.  
  
 *usValue*  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 *usDefault*  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a *usValue*, según corresponda. Si *usDefault* se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_string"></a>PXstring  
 Llame a esta función dentro del control **DoPropExchange** función miembro para serializar o inicializar una propiedad de cadena de caracteres.  
  
```  
 
BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& strValue);

BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& 
strValue  ,  
    CString strDefault);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `pszPropName`  
 El nombre de la propiedad que se intercambian.  
  
 `strValue`  
 Referencia a la variable donde se almacena la propiedad (normalmente, una variable miembro de la clase).  
  
 `strDefault`  
 Valor predeterminado de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Valor de la propiedad se leen o escriben en la variable hace referencia a `strValue`, según corresponda. Si `strDefault` se especifica, se utilizará como valor predeterminado de la propiedad. Este valor se utiliza si, por alguna razón, falla el proceso de serialización del control.  
  
##  <a name="px_vbxfontconvert"></a>PX_VBXFontConvert  
 Llame a esta función dentro del control `DoPropExchange` la función miembro para inicializar una propiedad de fuente mediante la conversión de propiedades de relacionadas con la fuente de un control VBX.  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Puntero a la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto (normalmente se pasa como parámetro a `DoPropExchange`).  
  
 `font`  
 La propiedad font del control OLE que contendrá las propiedades relacionadas con la fuente VBX convertidas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cambio se realizó correctamente; 0 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe usarse únicamente por un control OLE que se ha diseñado como un reemplazo directo para un control VBX. Cuando el entorno de desarrollo de Visual Basic convierte un formulario que contenga un control VBX para usar el control OLE de reemplazo correspondiente, el control llama **IDataObject:: SetData** función, pasa un conjunto de propiedades que contiene los datos de propiedad del control VBX. Esta operación, a su vez, hace que el control `DoPropExchange` función que se invocará. `DoPropExchange`puede llamar a `PX_VBXFontConvert` para convertir las VBX propiedades del control relacionadas con la fuente (por ejemplo, "FontName," "FontSize", etc.) en los componentes correspondientes de la propiedad font del control OLE.  
  
 `PX_VBXFontConvert`sólo debería llamarse cuando el control se va a convertir en realidad desde una aplicación de formulario VBX. Por ejemplo:  
  
 [!code-cpp[NVC_MFCActiveXControl&#14;](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl&#15;](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

