---
title: Mapas de envío
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: f1afa95d7c20d54f2015255a7e4e0d7ad9ae9c2b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856655"
---
# <a name="dispatch-maps"></a>Mapas de envío

La automatización OLE proporciona maneras de llamar a métodos y tener acceso a las propiedades de entre las aplicaciones. El mecanismo proporcionado por el biblioteca MFC para enviar estas solicitudes es el "mapa de envío", que designa los nombres internos y externos de las funciones y propiedades del objeto, así como los tipos de datos de las propias propiedades y de argumentos de la función.

|Macro de mapa de envío|Descripción|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Declara que se usará un mapa de envío para exponer los métodos y las propiedades de una clase (se debe usar en la declaración de clase).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Inicia la definición de un mapa de envío.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Finaliza la definición de un mapa de envío.|
|[DISP_FUNCTION](#disp_function)|Se usa en un mapa de envío para definir una función de automatización OLE.|
|[DISP_PROPERTY](#disp_property)|Define una propiedad de automatización OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Define una propiedad de automatización OLE y nombra las funciones Get y set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Define una propiedad de automatización OLE con notificación.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Define una propiedad de automatización OLE que toma parámetros y nombra las funciones Get y set.|
|[DISP_DEFVALUE](#disp_defvalue)|Convierte una propiedad existente en el valor predeterminado de un objeto.|

## <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

Si una clase derivada de `CCmdTarget`del programa admite la automatización OLE, esa clase debe proporcionar una asignación de envío para exponer sus métodos y propiedades.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Observaciones

Use la macro DECLARE_DISPATCH_MAP al final de la declaración de clase. Después, en. Archivo CPP que define las funciones miembro de la clase, utilice la macro BEGIN_DISPATCH_MAP. A continuación, incluya las entradas de macro para cada una de las propiedades y los métodos expuestos de la clase (DISP_FUNCTION, DISP_PROPERTY, etc.). Por último, use la macro END_DISPATCH_MAP.

> [!NOTE]
> Si declara miembros después DECLARE_DISPATCH_MAP, debe especificar un nuevo tipo de acceso ( **público**, **privado**o **protegido**) para ellos.

El Asistente para aplicaciones y los asistentes para código ayudan en la creación de clases de automatización y en el mantenimiento de mapas de envío. Para obtener más información sobre las asignaciones de envío, consulte [servidores de Automation](../../mfc/automation-servers.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Declara la definición del mapa de envío.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
Especifica el nombre de la clase a la que pertenece este mapa de envío.

*baseClass*<br/>
Especifica el nombre de la clase base de la *clase*.

### <a name="remarks"></a>Observaciones

En el archivo de implementación (. cpp) que define las funciones miembro de la clase, inicie el mapa de envío con la macro BEGIN_DISPATCH_MAP, agregue entradas de macro para cada una de las funciones y propiedades de distribución y complete el mapa de envío con el END_DISPATCH_ Macro de asignación.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="end_dispatch_map"></a>END_DISPATCH_MAP

Finaliza la definición del mapa de envío.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Observaciones

Se debe usar junto con BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_function"></a>DISP_FUNCTION

Define una función de automatización OLE en un mapa de envío.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
Nombre de la clase.

*pszName empiezan*<br/>
Nombre externo de la función.

*pfnMember*<br/>
Nombre de la función miembro.

*vtRetVal*<br/>
Valor que especifica el tipo de valor devuelto de la función.

*vtsParams*<br/>
Lista separada por espacios de una o más constantes que especifican la lista de parámetros de la función.

### <a name="remarks"></a>Observaciones

El argumento *vtRetVal* es de tipo VARTYPE. Los siguientes valores posibles para este argumento se toman de la enumeración `VARENUM`:

|Símbolo|Tipo de valor devuelto|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

El argumento *vtsParams* es una lista de valores separados por espacios de las constantes `VTS_*`. Uno o varios de estos valores separados por espacios (no comas) especifica la lista de parámetros de la función. Por ejemplo,

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

especifica una lista que contiene un entero corto seguido de un puntero a un entero corto.

Las constantes de `VTS_` y sus significados son las siguientes:

|Símbolo|Tipo de parámetro|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` o `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` o `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__\* breves__|
|VTS_PI4|__\* largo__|
|VTS_PR4|__\* flotante__|
|VTS_PR8|__doble\*__|
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

## <a name="disp_property"></a>DISP_PROPERTY

Define una propiedad de automatización OLE en un mapa de envío.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
Nombre de la clase.

*pszName empiezan*<br/>
Nombre externo de la propiedad.

*nombreDeMiembro*<br/>
Nombre de la variable miembro en la que se almacena la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

### <a name="remarks"></a>Observaciones

El argumento *vtPropType* es de tipo **VARTYPE**. Los valores posibles para este argumento se toman de la enumeración VARENUM:

|Símbolo|Tipo de propiedad|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Cuando un cliente externo cambia la propiedad, el valor de la variable miembro especificada por *memberName* cambia; no hay ninguna notificación del cambio.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_ex"></a>DISP_PROPERTY_EX

Define una propiedad de automatización OLE y el nombre de las funciones utilizadas para obtener y establecer el valor de la propiedad en un mapa de envío.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
Nombre de la clase.

*pszName empiezan*<br/>
Nombre externo de la propiedad.

*memberGet*<br/>
Nombre de la función miembro que se usa para obtener la propiedad.

*memberSet*<br/>
Nombre de la función miembro que se usa para establecer la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

### <a name="remarks"></a>Observaciones

Las funciones *memberGet* y *memberSet* tienen firmas determinadas por el argumento *vtPropType* . La función *memberGet* no toma ningún argumento y devuelve un valor del tipo especificado por *vtPropType*. La función *memberSet* toma un argumento del tipo especificado por *vtPropType* y no devuelve nada.

El argumento *vtPropType* es de tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM. Para obtener una lista de estos valores, consulte la sección Comentarios para el parámetro *vtRetVal* en [DISP_FUNCTION](#disp_function). Tenga en cuenta que VT_EMPTY, que se enumeran en el DISP_FUNCTION notas, no se permite como un tipo de datos de propiedad.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Define una propiedad de automatización OLE con notificación en un mapa de envío.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
Nombre de la clase.

*szExternalName*<br/>
Nombre externo de la propiedad.

*nombreDeMiembro*<br/>
Nombre de la variable miembro en la que se almacena la propiedad.

*pfnAfterSet*<br/>
Nombre de la función de notificación para *szExternalName*.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

### <a name="remarks"></a>Observaciones

A diferencia de las propiedades definidas con DISP_PROPERTY, una propiedad definida con DISP_PROPERTY_NOTIFY llamará automáticamente a la función especificada por *pfnAfterSet* cuando se cambie la propiedad.

El argumento *vtPropType* es de tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM:

|Símbolo|Tipo de propiedad|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
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

## <a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Define una propiedad a la que se tiene acceso con funciones miembro de `Get` y `Set` independientes.

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

*Clase*<br/>
Nombre de la clase.

*pszExternalName*<br/>
Nombre externo de la propiedad.

*pfnGet*<br/>
Nombre de la función miembro que se usa para obtener la propiedad.

*pfnSet*<br/>
Nombre de la función miembro que se usa para establecer la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de la propiedad.

*vtsParams*<br/>
Una cadena de tipos de parámetros Variant `VTS_*` separados por espacios, uno para cada parámetro.

### <a name="remarks"></a>Observaciones

A diferencia de la macro DISP_PROPERTY_EX, esta macro permite especificar una lista de parámetros para la propiedad. Esto resulta útil para implementar propiedades que se indexan o parametrizan.

### <a name="example"></a>Ejemplo

Considere la siguiente declaración de las funciones miembro get y set que permiten al usuario solicitar una fila y una columna específicas al obtener acceso a la propiedad:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Se corresponden con la siguiente DISP_PROPERTY_PARAM macro en el mapa de envío de controles:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Como otro ejemplo, considere las siguientes funciones miembro get y set:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Se corresponden con la siguiente DISP_PROPERTY_PARAM macro en el mapa de envío de controles:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_defvalue"></a>DISP_DEFVALUE

Convierte una propiedad existente en el valor predeterminado de un objeto.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
Nombre de la clase.

*pszName empiezan*<br/>
Nombre externo de la propiedad que representa el "valor" del objeto.

### <a name="remarks"></a>Observaciones

El uso de un valor predeterminado puede facilitar la programación del objeto de automatización para las aplicaciones Visual Basic.

El "valor predeterminado" del objeto es la propiedad que se recupera o establece cuando una referencia a un objeto no especifica una función de propiedad o miembro.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
