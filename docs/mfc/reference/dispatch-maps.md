---
title: Mapas de envío | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d22c94513e80c4f353de9e10588f219a2d3be92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388076"
---
# <a name="dispatch-maps"></a>Mapas de envío

OLE Automation proporciona maneras de llamar a métodos y tener acceso a las propiedades en todas las aplicaciones. El mecanismo proporcionado por la biblioteca Microsoft Foundation Class para enviar estas solicitudes es el "mapa de envíos", que designa los nombres internos y externos de funciones de objetos y propiedades, así como los tipos de datos de las propiedades en Sí y de argumentos de función.

|Macro de mapa de envíos|Descripción|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Declara que un mapa de envíos se utilizará para exponer los métodos y propiedades (debe usarse en la declaración de clase) de una clase.|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Inicia la definición de un mapa de envíos.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Termina la definición de un mapa de envíos.|
|[DISP_FUNCTION](#disp_function)|Se usa en un mapa de envíos para definir una función de automatización OLE.|
|[DISP_PROPERTY](#disp_property)|Define una propiedad de automatización OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Define una propiedad de automatización OLE y nombres de las funciones Get y Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Define una propiedad de automatización OLE con una notificación.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Define una propiedad de automatización OLE que toma parámetros y los nombres de las funciones Get y Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Hace que el valor predeterminado de un objeto de una propiedad existente.|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

Si un `CCmdTarget`-clase derivada en el programa es compatible con automatización OLE, que la clase debe proporcionar un mapa de envíos para exponer sus métodos y propiedades.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Comentarios

Utilice el declare_dispatch_map (macro) al final de la declaración de clase. A continuación, en el. Archivo CPP que define las funciones miembro de la clase, use el begin_dispatch_map (macro). A continuación, puede incluir entradas de macro para cada uno de los métodos expuestos de la clase y propiedades (DISP_FUNCTION, DISP_PROPERTY y así sucesivamente). Por último, use el end_dispatch_map (macro).

> [!NOTE]
> Si se declara ningún miembro después DECLARE_DISPATCH_MAP, debe especificar un nuevo tipo de acceso ( **pública**, **privada**, o **protegido**) para ellos.

Ayudar los asistentes de código y el Asistente para aplicaciones en la creación de clases de automatización y en el mantenimiento de mapas de envío. Para obtener más información sobre mapas de envío, consulte [servidores de automatización](../../mfc/automation-servers.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP

Declara la definición de su mapa de envíos.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase que posee este mapa de envíos.

*baseClass*<br/>
Especifica el nombre de clase base *theClass*.

### <a name="remarks"></a>Comentarios

En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, iniciar el mapa de envíos con la begin_dispatch_map (macro), agregue entradas de macro para cada una de las funciones de envío y las propiedades y completar el mapa de envíos con el END_DISPATCH_ Macros de mapa.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP

Termina la definición de su mapa de envíos.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Comentarios

Se debe usar junto con BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION

Define una función de automatización OLE en un mapa de envíos.

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
Una lista separada por espacios de una o varias constantes que especifica la lista de parámetros de la función.

### <a name="remarks"></a>Comentarios

El *vtRetVal* argumento es de tipo VARTYPE. Los siguientes valores posibles para este argumento se toman de la `VARENUM` enumeración:

|Símbolo|Tipo devuelto|
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

El *vtsParams* argumento es una lista separada por espacios de los valores de la `VTS_*` constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo,

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Especifica una lista que contiene un entero corto seguido por un puntero a un entero corto.

El `VTS_` constantes y sus significados son los siguientes:

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
|VTS_PI2|__corto\*__|
|VTS_PI4|__Long\*__|
|VTS_PR4|__Float\*__|
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

## <a name="disp_property"></a>  DISP_PROPERTY

Define una propiedad de automatización OLE en un mapa de envíos.

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

*MemberName*<br/>
Nombre de la variable de miembro en el que se almacena la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de propiedad.

### <a name="remarks"></a>Comentarios

El *vtPropType* argumento es de tipo **VARTYPE**. Los valores posibles para este argumento se toman de la enumeración VARENUM:

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

Cuando un cliente externo cambia la propiedad, el valor de la variable de miembro especificada por *memberName* cambia; no hay ninguna notificación del cambio.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

Define una propiedad OLE automation y nombre de las funciones utilizadas para obtener y establecer el valor de propiedad en un mapa de envíos.

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
Nombre de la función miembro que se usa para obtener la propiedad.

*conjunto de miembros*<br/>
Nombre de la función miembro que se usa para establecer la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de propiedad.

### <a name="remarks"></a>Comentarios

El *memberGet* y *memberSet* funciones tienen firmas determinadas por la *vtPropType* argumento. El *memberGet* función no toma ningún argumento y devuelve un valor del tipo especificado por *vtPropType*. El *memberSet* función toma un argumento de tipo especificado por *vtPropType* y no devuelve nada.

El *vtPropType* argumento es de tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM. Para obtener una lista de estos valores, vea los comentarios sobre la *vtRetVal* parámetro [DISP_FUNCTION](#disp_function). Tenga en cuenta que no se permite VT_EMPTY, que aparece en la sección de comentarios DISP_FUNCTION, como un tipo de datos de propiedad.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

Define una propiedad de automatización OLE con una notificación en un mapa de envíos.

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

*MemberName*<br/>
Nombre de la variable de miembro en el que se almacena la propiedad.

*pfnAfterSet*<br/>
Nombre de la función de notificación para *szExternalName*.

*vtPropType*<br/>
Valor que especifica el tipo de propiedad.

### <a name="remarks"></a>Comentarios

A diferencia de las propiedades definidas con DISP_PROPERTY, una propiedad definida con DISP_PROPERTY_NOTIFY llamará automáticamente a la función especificada por *pfnAfterSet* cuando se cambia la propiedad.

El *vtPropType* argumento es de tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM:

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

## <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM

Define una propiedad que se accede con independiente `Get` y `Set` funciones miembro.

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
Nombre de la función miembro que se usa para obtener la propiedad.

*pfnSet*<br/>
Nombre de la función miembro que se usa para establecer la propiedad.

*vtPropType*<br/>
Valor que especifica el tipo de propiedad.

*vtsParams*<br/>
Una cadena separada por espacios `VTS_*` tipos de parámetro variant, uno para cada parámetro.

### <a name="remarks"></a>Comentarios

A diferencia de la macro DISP_PROPERTY_EX, esta macro permite especificar una lista de parámetros para la propiedad. Esto es útil para implementar propiedades indizadas o con parámetros.

### <a name="example"></a>Ejemplo

Considere la siguiente declaración de get y miembro del grupo de funciones que permiten al usuario solicitar una fila y columna específicas al obtener acceso a la propiedad:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Estos se corresponden con el siguiente DISP_PROPERTY_PARAM (macro) en el mapa de envíos de control:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Otro ejemplo, considere la siguiente operación get y miembro del grupo de funciones:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Estos se corresponden con el siguiente DISP_PROPERTY_PARAM (macro) en el mapa de envíos de control:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

Hace que el valor predeterminado de un objeto de una propiedad existente.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Nombre de la clase.

*pszName*<br/>
Nombre externo de la propiedad que representa el "valor" del objeto.

### <a name="remarks"></a>Comentarios

Un valor predeterminado puede hacer que el objeto de automatización más sencillo para aplicaciones de Visual Basic de programación.

El "valor predeterminado" del objeto es la propiedad que se recupera o establece si una referencia a un objeto no especifica una propiedad o función miembro.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
