---
title: Mapas de envío
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 59dd8c7a7b0b930ffdb68fd96410fd73aeb02e81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365753"
---
# <a name="dispatch-maps"></a>Mapas de envío

Automatización OLE proporciona formas de llamar a métodos y tener acceso a propiedades entre aplicaciones. El mecanismo proporcionado por la biblioteca microsoft Foundation Class para distribuir estas solicitudes es el "mapa de distribución", que designa los nombres internos y externos de las funciones y propiedades de objeto, así como los tipos de datos de las propias propiedades y de los argumentos de función.

|Macro de mapa de distribución|Descripción|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Declara que se usará un mapa de distribución para exponer los métodos y propiedades de una clase (debe usarse en la declaración de clase).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Inicia la definición de un mapa de distribución.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Finaliza la definición de un mapa de distribución.|
|[DISP_FUNCTION](#disp_function)|Se utiliza en un mapa de distribución para definir una función de automatización OLE.|
|[DISP_PROPERTY](#disp_property)|Define una propiedad de automatización OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Define una propiedad de automatización OLE y nombra las funciones Get y Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Define una propiedad de automatización OLE con notificación.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Define una propiedad de automatización OLE que toma parámetros y nombra las funciones Get y Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Convierte una propiedad existente en el valor predeterminado de un objeto.|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

Si `CCmdTarget`una clase derivada del programa admite la automatización OLE, esa clase debe proporcionar un mapa de distribución para exponer sus métodos y propiedades.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Observaciones

Utilice la macro DECLARE_DISPATCH_MAP al final de la declaración de clase. Luego, en el archivo . CPP que define las funciones miembro para la clase, utilice la macro BEGIN_DISPATCH_MAP. A continuación, incluya entradas de macro para cada uno de los métodos y propiedades expuestos de la clase (DISP_FUNCTION, DISP_PROPERTY, etc.). Por último, utilice la macro END_DISPATCH_MAP.

> [!NOTE]
> Si declara algún miembro después de DECLARE_DISPATCH_MAP, debe especificar un nuevo tipo de acceso ( **public**, **private**o **protected**) para ellos.

El Asistente para aplicaciones y los asistentes de código ayudan a crear clases de automatización y a mantener mapas de distribución. Para obtener más información sobre los mapas de distribución, consulte [Servidores de automatización](../../mfc/automation-servers.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Declara la definición del mapa de envío.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase propietaria de este mapa de distribución.

*baseClass*<br/>
Especifica el nombre de clase base de *theClass*.

### <a name="remarks"></a>Observaciones

En el archivo de implementación (.cpp) que define las funciones miembro de la clase, inicie el mapa de distribución con la macro BEGIN_DISPATCH_MAP, agregue entradas de macro para cada una de las funciones y propiedades de envío y complete el mapa de distribución con la macro END_DISPATCH_MAP.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

Finaliza la definición del mapa de envío.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Observaciones

Debe utilizarse junto con BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

Define una función de automatización OLE en un mapa de distribución.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la función.

*pfnMember*<br/>
Nombre de la función miembro.

*vtRetVal*<br/>
Valor que especifica el tipo de valor devuelto de la función.

*vtsParams*<br/>
Una lista separada por espacios de una o más constantes que especifican la lista de parámetros de la función.

### <a name="remarks"></a>Observaciones

El argumento *vtRetVal* es de tipo VARTYPE. Los siguientes valores posibles para este `VARENUM` argumento se toman de la enumeración:

|Símbolo|Tipo de valor devuelto|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**Largo**|
|VT_R4|**Flotador**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

El argumento *vtsParams* es una lista de `VTS_*` valores separados por espacios de las constantes. Uno o varios de estos valores separados por espacios (no comas) especifican la lista de parámetros de la función. Por ejemplo,

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

especifica una lista que contiene un entero corto seguido de un puntero a un entero corto.

Las `VTS_` constantes y sus significados son los siguientes:

|Símbolo|Tipo de parámetro|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**Largo**|
|VTS_R4|**Flotador**|
|VTS_R8|**double**|
|VTS_CY|`const CY` o `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` o `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__short\*__|
|VTS_PI4|__Largo\*__|
|VTS_PR4|__Flotador\*__|
|VTS_PR8|__Doble\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Sin parámetros|

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property"></a><a name="disp_property"></a>DISP_PROPERTY

Define una propiedad de automatización OLE en un mapa de distribución.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la propiedad.

*memberName*<br/>
Nombre de la variable miembro en la que se almacena la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

### <a name="remarks"></a>Observaciones

El argumento *vtPropType* es de tipo **VARTYPE**. Los valores posibles para este argumento se toman de la enumeración VARENUM:

|Símbolo|Tipo de propiedad|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**Largo**|
|VT_R4|**Flotador**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Cuando un cliente externo cambia la propiedad, cambia el valor de la variable miembro especificada por *memberName;* no hay notificación del cambio.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

Define una propiedad de automatización OLE y el nombre de las funciones utilizadas para obtener y establecer el valor de la propiedad en un mapa de distribución.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la propiedad.

*memberGet*<br/>
Nombre de la función miembro utilizada para obtener la propiedad.

*memberSet*<br/>
Nombre de la función miembro utilizada para establecer la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

### <a name="remarks"></a>Observaciones

Las funciones *memberGet* y *memberSet* tienen firmas determinadas por el argumento *vtPropType.* La función *memberGet* no toma ningún argumento y devuelve un valor del tipo especificado por *vtPropType*. La función *memberSet* toma un argumento del tipo especificado por *vtPropType* y no devuelve nada.

El argumento *vtPropType* es de tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM. Para obtener una lista de estos valores, vea el parámetro Comentarios para el parámetro *vtRetVal* en [DISP_FUNCTION](#disp_function). Tenga en cuenta que VT_EMPTY, que se enumeran en el DISP_FUNCTION comentarios, no está permitido como un tipo de datos de propiedad.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Define una propiedad de automatización OLE con notificación en un mapa de distribución.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*szExternalName*<br/>
Nombre externo de la propiedad.

*memberName*<br/>
Nombre de la variable miembro en la que se almacena la propiedad.

*pfnAfterSet*<br/>
Nombre de la función de notificación para *szExternalName*.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

### <a name="remarks"></a>Observaciones

A diferencia de las propiedades definidas con DISP_PROPERTY, una propiedad definida con DISP_PROPERTY_NOTIFY llamará automáticamente a la función especificada por *pfnAfterSet* cuando se cambia la propiedad.

El argumento *vtPropType* es de tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM:

|Símbolo|Tipo de propiedad|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**Largo**|
|VT_R4|**Flotador**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_param"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Define una propiedad `Get` a `Set` la que se tiene acceso con funciones independientes y miembros.

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszExternalName*<br/>
Nombre externo de la propiedad.

*pfnGet*<br/>
Nombre de la función miembro utilizada para obtener la propiedad.

*pfnSet*<br/>
Nombre de la función miembro utilizada para establecer la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

*vtsParams*<br/>
Una cadena de `VTS_*` tipos de parámetros de variante separados por espacios, uno para cada parámetro.

### <a name="remarks"></a>Observaciones

A diferencia de la macro DISP_PROPERTY_EX, esta macro permite especificar una lista de parámetros para la propiedad. Esto es útil para implementar propiedades que están indizadas o parametrizadas.

### <a name="example"></a>Ejemplo

Considere la siguiente declaración de funciones miembro get y set que permiten al usuario solicitar una fila y columna específicaales al acceder a la propiedad:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Estos corresponden a la siguiente macro DISP_PROPERTY_PARAM en el mapa de distribución de control:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Como otro ejemplo, considere las siguientes funciones miembro get y set:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Estos corresponden a la siguiente macro DISP_PROPERTY_PARAM en el mapa de distribución de control:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

Convierte una propiedad existente en el valor predeterminado de un objeto.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la propiedad que representa el "valor" del objeto.

### <a name="remarks"></a>Observaciones

El uso de un valor predeterminado puede facilitar la programación del objeto de automatización para aplicaciones de Visual Basic.

El "valor predeterminado" del objeto es la propiedad que se recupera o establece cuando una referencia a un objeto no especifica una propiedad o función miembro.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
