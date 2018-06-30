---
title: Mapas de envío | Documentos de Microsoft
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
ms.openlocfilehash: 107dba503c11d3810f75dcd4ee6e6f5af47008fc
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122985"
---
# <a name="dispatch-maps"></a>Mapas de envío

Automatización OLE proporciona métodos para llamar a métodos y tener acceso a propiedades en todas las aplicaciones. El mecanismo proporcionado por la biblioteca Microsoft Foundation Class para enviar estas solicitudes es el "mapa de envíos", que designa los nombres internos y externos de funciones de objetos y propiedades, así como los tipos de datos de las propiedades en Sí y de argumentos de función.

|Macro de mapa de envíos|Descripción|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Declara que se utilizará un mapa de envíos para exponer métodos y propiedades (debe usarse en la declaración de clase) de una clase.|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Inicia la definición de un mapa de envíos.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Termina la definición de un mapa de envíos.|
|[DISP_FUNCTION](#disp_function)|Se utiliza en un mapa de envíos para definir una función de automatización OLE.|
|[DISP_PROPERTY](#disp_property)|Define una propiedad de automatización OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Define una propiedad de automatización OLE y nombres de las funciones Get y Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Define una propiedad de automatización OLE con notificación.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Define una propiedad de automatización OLE que toma parámetros y nombres de las funciones Get y Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Convierte el valor predeterminado de un objeto de una propiedad existente.|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

Si un `CCmdTarget`-clase derivada en el programa es compatible con la automatización OLE, que la clase debe proporcionar un mapa de envíos para exponer sus métodos y propiedades.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Comentarios

Utilice la macro DECLARE_DISPATCH_MAP al final de la declaración de clase. A continuación, en el. Los archivos CPP que define las funciones miembro de la clase, use la macro BEGIN_DISPATCH_MAP. A continuación, puede incluir entradas de macro para cada uno de los métodos expuestos de la clase y propiedades (DISP_FUNCTION, DISP_PROPERTY y así sucesivamente). Por último, utilice la macro END_DISPATCH_MAP.

> [!NOTE]
> Si declara los miembros después de DECLARE_DISPATCH_MAP, debe especificar un nuevo tipo de acceso ( **público**, **privada**, o **protegido**) para ellos.

Los asistentes de Asistente para aplicaciones y código ayudar en la creación de clases de automatización así como en el mantenimiento de mapas de envío. Para obtener más información sobre los mapas de envío, consulte [servidores de automatización](../../mfc/automation-servers.md).

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

*theClass*  
Especifica el nombre de la clase a la que pertenece este mapa de envíos.

*baseClass*  
Especifica el nombre de clase base *theClass*.

### <a name="remarks"></a>Comentarios

En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, iniciar el mapa de envíos con la macro BEGIN_DISPATCH_MAP, agregue entradas de macro para cada una de las propiedades y funciones de envío y completar el mapa de envíos con la END_DISPATCH_ Macros de mapa.

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

*theClass*  
Nombre de la clase.

*pszName*  
Nombre externo de la función.

*pfnMember*  
Nombre de la función miembro.

*vtRetVal*  
Valor que especifica el tipo de valor devuelto de la función.

*vtsParams*  
Una lista separada por espacios de una o varias constantes que especifica la lista de parámetros de la función.

### <a name="remarks"></a>Comentarios

El *vtRetVal* argumento es del tipo VARTYPE. Los siguientes valores posibles para este argumento se toman de la `VARENUM` enumeración:

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

El *vtsParams* argumento es una lista separada por espacios de valores de la `VTS_*` constantes. Uno o varios de estos valores separados por espacios (no por comas) especifican la lista de parámetros de la función. Por ejemplo,

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Especifica una lista que contiene un entero corto seguido por un puntero a un entero corto.

El `VTS_` constantes y sus significados son los siguientes:

|Símbolo|tipo de parámetro|
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
|VTS_PR4|__float\*__|
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

*theClass*  
Nombre de la clase.

*pszName*  
Nombre externo de la propiedad.

*nombre de usuario registrado*  
Nombre de la variable de miembro en el que se almacena la propiedad.

*vtPropType*  
Valor que especifica el tipo de propiedad.

### <a name="remarks"></a>Comentarios

El *vtPropType* argumento es del tipo **VARTYPE**. Los valores posibles para este argumento se toman de la enumeración VARENUM:

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

Cuando un cliente externo cambia la propiedad, el valor de la variable de miembro especificado por *memberName* cambia; no hay ninguna notificación del cambio.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

Define una propiedad de automatización OLE y el nombre de las funciones utilizadas para obtener y establecer el valor de propiedad en un mapa de envíos.

```cpp
DISP_PROPERTY_EX(
  theClass,
  pszName,
  memberGet,
  memberSet,
  vtPropType)
```

### <a name="parameters"></a>Parámetros

*theClass*  
Nombre de la clase.

*pszName*  
Nombre externo de la propiedad.

*memberGet*  
Nombre de la función de miembro que se utiliza para obtener la propiedad.

*conjunto de miembros*  
Nombre de la función de miembro que se usa para establecer la propiedad.

*vtPropType*  
Valor que especifica el tipo de propiedad.

### <a name="remarks"></a>Comentarios

El *memberGet* y *memberSet* funciones tengan firmas determinadas por la *vtPropType* argumento. El *memberGet* función no toma ningún argumento y devuelve un valor del tipo especificado por *vtPropType*. El *memberSet* función toma un argumento del tipo especificado por *vtPropType* y no devuelve nada.

El *vtPropType* argumento es del tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM. Para obtener una lista de estos valores, vea la sección Comentarios para el *vtRetVal* parámetro en [DISP_FUNCTION](#disp_function). Tenga en cuenta que no se permite VT_EMPTY, aparecen en la sección de comentarios DISP_FUNCTION, como un tipo de datos de propiedad.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

Define una propiedad de automatización OLE con notificación en un mapa de envíos.

```cpp
DISP_PROPERTY_NOTIFY(
  theClass,
  szExternalName,
  memberName,
  pfnAfterSet,
  vtPropType)
```

### <a name="parameters"></a>Parámetros

*theClass*  
Nombre de la clase.

*szExternalName*  
Nombre externo de la propiedad.

*nombre de usuario registrado*  
Nombre de la variable de miembro en el que se almacena la propiedad.

*pfnAfterSet*  
Nombre de la función de notificación para *szExternalName*.

*vtPropType*  
Valor que especifica el tipo de propiedad.

### <a name="remarks"></a>Comentarios

A diferencia de propiedades definidas con DISP_PROPERTY, una propiedad definida con DISP_PROPERTY_NOTIFY llamará automáticamente a la función especificada por *pfnAfterSet* cuando se cambia la propiedad.

El *vtPropType* argumento es del tipo VARTYPE. Los valores posibles para este argumento se toman de la enumeración VARENUM:

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

Define una propiedad que se obtiene acceso con independiente `Get` y `Set` funciones miembro.

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

*theClass*  
Nombre de la clase.

*pszExternalName*  
Nombre externo de la propiedad.

*pfnGet*  
Nombre de la función de miembro que se utiliza para obtener la propiedad.

*pfnSet*  
Nombre de la función de miembro que se usa para establecer la propiedad.

*vtPropType*  
Valor que especifica el tipo de propiedad.

*vtsParams*  
Una cadena separada por espacios `VTS_*` tipos de parámetro variant, uno para cada parámetro.

### <a name="remarks"></a>Comentarios

A diferencia de la macro DISP_PROPERTY_EX, esta macro permite especificar una lista de parámetros para la propiedad. Esto es útil para implementar propiedades indizadas o con parámetros.

### <a name="example"></a>Ejemplo

Considere la siguiente declaración de get y miembro del grupo de funciones que permiten al usuario a solicitar una fila y columna específicas al obtener acceso a la propiedad:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Estos se corresponden con la siguiente macro DISP_PROPERTY_PARAM en el mapa de envíos del control:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Como otro ejemplo, considere la posibilidad de get siguiente y miembro del grupo de funciones:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Estos se corresponden con la siguiente macro DISP_PROPERTY_PARAM en el mapa de envíos del control:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

Convierte el valor predeterminado de un objeto de una propiedad existente.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parámetros

*theClass*  
Nombre de la clase.

*pszName*  
Nombre externo de la propiedad que representa el "valor" del objeto.

### <a name="remarks"></a>Comentarios

Con un valor predeterminado, puede realizar el proceso de programar el objeto de automatización más sencillo para aplicaciones de Visual Basic.

El "valor predeterminado" del objeto es la propiedad que se recuperan o se establecen cuando una referencia a un objeto no especifica una propiedad o función miembro.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)  
