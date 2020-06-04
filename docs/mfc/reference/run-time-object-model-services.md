---
title: Servicios del modelo de objetos en tiempo de ejecución
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f1cefdad368ebcd006dcb4ecf653247147f36d03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372938"
---
# <a name="run-time-object-model-services"></a>Servicios del modelo de objetos en tiempo de ejecución

Las clases [CObject](../../mfc/reference/cobject-class.md) y [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) encapsulan varios servicios de objetos, incluido el acceso a la información de clase en tiempo de ejecución, la serialización y la creación de objetos dinámicos. Todas las clases derivadas de `CObject` heredar esta funcionalidad.

El acceso a la información de clase en tiempo de ejecución le permite determinar información sobre la clase de un objeto en tiempo de ejecución. La capacidad de determinar la clase de un objeto en tiempo de ejecución es útil cuando se necesita una comprobación de tipos adicional de argumentos de función y cuando se debe escribir código de propósito especial basado en la clase de un objeto. La información de clase en tiempo de ejecución no es compatible directamente con el lenguaje C++.

La serialización es el proceso de escribir o leer el contenido de un objeto hacia o desde un archivo. Puede usar la serialización para almacenar el contenido de un objeto incluso después de que se cierre la aplicación. A continuación, el objeto se puede leer desde el archivo cuando se reinicia la aplicación. Se dice que estos objetos de datos son "persistentes".

La creación dinámica de objetos permite crear un objeto de una clase especificada en tiempo de ejecución. Por ejemplo, los objetos de documento, vista y marco deben admitir la creación dinámica porque el marco de trabajo debe crearlos dinámicamente.

En la tabla siguiente se enumeran las macros MFC que admiten información de clase en tiempo de ejecución, serialización y creación dinámica.

Para obtener más información sobre estos servicios de objetos en tiempo de ejecución y la serialización, vea el artículo [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Macros de servicios de modelo de objetos en tiempo de ejecución

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Habilita el acceso a la información de clase en tiempo de ejecución (debe utilizarse en la declaración de clase).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Habilita la creación dinámica y el acceso a la información de clase en tiempo de ejecución (debe utilizarse en la declaración de clase).|
|[DECLARE_SERIAL](#declare_serial)|Habilita la serialización y el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Habilita el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Habilita la creación dinámica y el acceso a la información en tiempo de ejecución (debe usarse en la implementación de la clase).|
|[IMPLEMENT_SERIAL](#implement_serial)|Permite la serialización y el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|
|[RUNTIME_CLASS](#runtime_class)|Devuelve `CRuntimeClass` la estructura que corresponde a la clase con nombre.|

OLE requiere con frecuencia la creación dinámica de objetos en tiempo de ejecución. Por ejemplo, una aplicación de servidor OLE debe ser capaz de crear elementos OLE dinámicamente en respuesta a una solicitud de un cliente. Del mismo modo, un servidor de automatización debe ser capaz de crear elementos en respuesta a las solicitudes de los clientes de automatización.

La biblioteca Microsoft Foundation Class proporciona dos macros específicas de OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Creación dinámica de objetos OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[DECLARE_OLECREATE](#declare_olecreate)|Permite crear objetos a través de la automatización OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Declara las `GetUserTypeNameID` `GetMiscStatus` funciones miembro y de la clase de control.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Declara que el control OLE proporciona una lista de páginas de propiedades para mostrar sus propiedades.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Permite que el sistema OLE cree objetos.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementa las `GetUserTypeNameID` `GetMiscStatus` funciones miembro y de la clase de control.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) debe aparecer en el `DECLARE_OLECREATE`archivo de implementación para cualquier clase que utilice . |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Determina si la biblioteca de controles comunes implementa la API especificada.

### <a name="syntax"></a>Sintaxis

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parámetros

*proc*<br/>
Puntero a una cadena terminada en null que contiene el nombre de la función o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden bajo; la palabra de orden superior debe ser cero. Este parámetro debe estar en Unicode.

### <a name="remarks"></a>Observaciones

Utilice esta macro para determinar si la biblioteca de controles comunes es la función especificada por *proc* (en lugar de llamar a [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Requisitos

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Determina si la biblioteca de controles comunes implementa la API especificada (esta es la versión Unicode de [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Sintaxis

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parámetros

*proc*<br/>
Puntero a una cadena terminada en null que contiene el nombre de la función o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden bajo; la palabra de orden superior debe ser cero. Este parámetro debe estar en Unicode.

### <a name="remarks"></a>Observaciones

Utilice esta macro para determinar si la biblioteca de controles comunes es la función especificada por *proc* (en lugar de llamar a [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). Esta macro es la versión Unicode de AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Requisitos

afxcomctl32.h, afxcomctl32.inl

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC

Agrega la capacidad de tener acceso a información en tiempo de `CObject`ejecución sobre la clase de un objeto al derivar una clase de .

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

### <a name="remarks"></a>Observaciones

Agregue la macro DECLARE_DYNAMIC al módulo de encabezado (.h) para la clase y, a continuación, incluya ese módulo en todos los módulos .cpp que necesitan acceso a los objetos de esta clase.

Si utiliza las macros DECLARE_ DYNAMIC y IMPLEMENT_DYNAMIC como se describe, puede utilizar la macro RUNTIME_CLASS y la `CObject::IsKindOf` función para determinar la clase de los objetos en tiempo de ejecución.

Si DECLARE_DYNAMIC se incluye en la declaración de clase, IMPLEMENT_DYNAMIC debe incluirse en la implementación de la clase.

Para obtener más información sobre la macro DECLARE_DYNAMIC, vea Temas de [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

Consulte el ejemplo de [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Permite que `CObject`los objetos de las clases derivadas se creen dinámicamente en tiempo de ejecución.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

### <a name="remarks"></a>Observaciones

El marco de trabajo utiliza esta capacidad para crear nuevos objetos dinámicamente. Por ejemplo, la nueva vista creada al abrir un nuevo documento. Las clases de documento, vista y marco deben admitir la creación dinámica porque el marco de trabajo debe crearlas dinámicamente.

Agregue la macro DECLARE_DYNCREATE en el módulo .h para la clase y, a continuación, incluya ese módulo en todos los módulos .cpp que necesiten acceso a los objetos de esta clase.

Si DECLARE_DYNCREATE se incluye en la declaración de clase, IMPLEMENT_DYNCREATE debe incluirse en la implementación de la clase.

Para obtener más información sobre la macro DECLARE_DYNCREATE, vea Temas de [clase CObject](../../mfc/using-cobject.md).

> [!NOTE]
> La macro DECLARE_DYNCREATE incluye todas las funciones de DECLARE_DYNAMIC.

### <a name="example"></a>Ejemplo

Consulte el ejemplo de [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Declara las `GetUserTypeNameID` `GetMiscStatus` funciones miembro y de la clase de control.

### <a name="syntax"></a>Sintaxis

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control.

### <a name="remarks"></a>Observaciones

`GetUserTypeNameID`y `GetMiscStatus` son funciones virtuales puras, declaradas en `COleControl`. Dado que estas funciones son virtuales puras, deben invalidarse en la clase de control. Además de DECLARE_OLECTLTYPE, debe agregar la macro IMPLEMENT_OLECTLTYPE a la declaración de clase de control.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Declara que el control OLE proporciona una lista de páginas de propiedades para mostrar sus propiedades.

### <a name="syntax"></a>Sintaxis

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control que posee las páginas de propiedades.

### <a name="remarks"></a>Observaciones

Utilice `DECLARE_PROPPAGEIDS` la macro al final de la declaración de clase. A continuación, en el archivo .cpp que define `BEGIN_PROPPAGEIDS` las funciones miembro de la clase, use la `END_PROPPAGEIDS` macro, las entradas de macro para cada una de las páginas de propiedades del control y la macro para declarar el final de la lista de páginas de propiedades.

Para obtener más información sobre las páginas de propiedades, vea el artículo [Controles ActiveX: Páginas](../mfc-activex-controls-property-pages.md)de propiedades .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="declare_serial"></a><a name="declare_serial"></a>DECLARE_SERIAL

Genera el código de encabezado `CObject`C++ necesario para una clase derivada que se puede serializar.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

### <a name="remarks"></a>Observaciones

La serialización es el proceso de escribir o leer el contenido de un objeto hacia y desde un archivo.

Utilice la macro DECLARE_SERIAL en un módulo .h y, a continuación, incluya ese módulo en todos los módulos .cpp que necesitan acceso a los objetos de esta clase.

Si DECLARE_SERIAL se incluye en la declaración de clase, IMPLEMENT_SERIAL debe incluirse en la implementación de la clase.

La macro DECLARE_SERIAL incluye todas las funciones de DECLARE_DYNAMIC y DECLARE_DYNCREATE.

Puede utilizar la macro AFX_API `CArchive` para exportar automáticamente el operador de extracción para las clases que utilizan las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Entre corchetes las declaraciones de clase (ubicadas en el archivo .h) con el código siguiente:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Para obtener más información sobre la macro DECLARE_SERIAL, vea Temas de [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Genera el código C++ `CObject`necesario para una clase derivada dinámica con acceso en tiempo de ejecución al nombre de clase y la posición dentro de la jerarquía.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

*base_class_name*<br/>
Nombre de la clase base.

### <a name="remarks"></a>Observaciones

Utilice la macro IMPLEMENT_DYNAMIC en un módulo .cpp y, a continuación, vincule el código de objeto resultante solo una vez.

Para obtener más información, vea Temas de [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Permite que `CObject`los objetos de las clases derivadas se creen dinámicamente en tiempo de ejecución cuando se utilizan con la macro DECLARE_DYNCREATE.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

*base_class_name*<br/>
El nombre real de la clase base.

### <a name="remarks"></a>Observaciones

El marco de trabajo usa esta capacidad para crear nuevos objetos dinámicamente, por ejemplo, cuando lee un objeto del disco durante la serialización. Agregue la macro IMPLEMENT_DYNCREATE en el archivo de implementación de clase. Para obtener más información, vea Temas de [clase CObject](../../mfc/using-cobject.md).

Si utiliza las macros DECLARE_DYNCREATE y IMPLEMENT_DYNCREATE, puede usar `CObject::IsKindOf` la macro RUNTIME_CLASS y la función miembro para determinar la clase de los objetos en tiempo de ejecución.

Si DECLARE_DYNCREATE se incluye en la declaración de clase, IMPLEMENT_DYNCREATE debe incluirse en la implementación de la clase.

Tenga en cuenta que esta definición de macro invocará el constructor predeterminado para la clase. Si la clase implementa explícitamente un constructor no trivial, también debe implementar explícitamente el constructor predeterminado. El constructor predeterminado se puede agregar a las secciones de miembro **sprivado** o **protegido** de la clase para evitar que se llame desde fuera de la implementación de la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) debe aparecer en el archivo de implementación para cualquier clase que utilice DECLARE_OLECREATE.

### <a name="syntax"></a>Sintaxis

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

*external_name*<br/>
El nombre del objeto expuesto a otras aplicaciones (entre comillas).

*nFlags*<br/>
Contiene uno o varios de los siguientes indicadores:

- `afxRegInsertable`Permite que el control aparezca en el cuadro de diálogo Insertar objeto para objetos OLE.
- `afxRegApartmentThreading`Establece el modelo de subprocesamiento en el registro en ThreadingModel-Apartment.
- `afxRegFreeThreading`Establece el modelo de subprocesamiento en el registro en ThreadingModel-Free.

Puede combinar los `afxRegApartmentThreading` dos `afxRegFreeThreading` indicadores y establecer ThreadingModel-Both. Consulte [InprocServer32](/windows/win32/com/inprocserver32) en el Windows SDK para obtener más información sobre el registro del modelo de subprocesos.

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Componentes del CLSID de la clase.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Si utiliza IMPLEMENT_OLECREATE_FLAGS, puede especificar qué modelo de subprocesamiento admite el objeto mediante el parámetro *nFlags.* Si solo desea admitir el modelo de una sola pisada, utilice IMPLEMENT_OLECREATE.

El nombre externo es el identificador expuesto a otras aplicaciones. Las aplicaciones cliente usan el nombre externo para solicitar un objeto de esta clase de un servidor de automatización.

El identificador de clase OLE es un identificador único de 128 bits para el objeto. Consta de un **largo,** dos **PALABRAs**s y ocho **BYTE**s, representado por *l*, *w1*, *w2*, y *b1* a *b8* en la descripción de sintaxis. El Asistente para aplicaciones y los asistentes de código crean identificadores de clase OLE únicos según sea necesario.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementa las `GetUserTypeNameID` `GetMiscStatus` funciones miembro y de la clase de control.

### <a name="syntax"></a>Sintaxis

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control.

*idsUserTypeName*<br/>
El identificador de recurso de una cadena que contiene el nombre externo del control.

*dwOleMisc*<br/>
Enumeración que contiene uno o varios indicadores. Para obtener más información sobre esta enumeración, vea [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Además de IMPLEMENT_OLECTLTYPE, debe agregar la macro DECLARE_OLECTLTYPE a la declaración de clase de control.

La `GetUserTypeNameID` función miembro devuelve la cadena de recursos que identifica la clase de control. `GetMiscStatus`devuelve los bits OLEMISC para el control. Esta enumeración especifica una colección de valores que describen varias características del control. Para obtener una descripción completa de la configuración de OLEMISC, consulte [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) en el Windows SDK.

> [!NOTE]
> La configuración predeterminada utilizada por ActiveX ControlWizard es: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE y OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="implement_serial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL

Genera el código C++ `CObject`necesario para una clase derivada dinámica con acceso en tiempo de ejecución al nombre de clase y la posición dentro de la jerarquía.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

*base_class_name*<br/>
Nombre de la clase base.

*wSchema*<br/>
Un "número de versión" UINT que se codificará en el archivo para permitir que un programa de deserialización identifique y controle los datos creados por versiones anteriores del programa. El número de esquema de clase no debe ser -1.

### <a name="remarks"></a>Observaciones

Utilice la macro IMPLEMENT_SERIAL en un módulo .cpp; a continuación, vincule el código de objeto resultante una sola vez.

Puede utilizar la macro AFX_API `CArchive` para exportar automáticamente el operador de extracción para las clases que utilizan las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Entre corchetes las declaraciones de clase (ubicadas en el archivo .h) con el código siguiente:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Para obtener más información, vea Temas de [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="runtime_class"></a><a name="runtime_class"></a>RUNTIME_CLASS

Obtiene la estructura de clase en tiempo de ejecución del nombre de una clase C++.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase (no entre comillas).

### <a name="remarks"></a>Observaciones

RUNTIME_CLASS devuelve un puntero a una estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) para la clase especificada por *class_name*. Solo `CObject`las clases derivadas declaradas con DECLARE_DYNAMIC, DECLARE_DYNCREATE `CRuntimeClass` o DECLARE_SERIAL devolverán punteros a una estructura.

Para obtener más información, vea Temas de [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE

Permite crear `CCmdTarget`objetos de clases derivadas mediante la automatización OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

### <a name="remarks"></a>Observaciones

Esta macro permite que otras aplicaciones habilitadas para OLE creen objetos de este tipo.

Agregue la macro DECLARE_OLECREATE en el módulo .h para la clase y, a continuación, incluya ese módulo en todos los módulos .cpp que necesitan acceso a los objetos de esta clase.

Si DECLARE_OLECREATE se incluye en la declaración de clase, IMPLEMENT_OLECREATE debe incluirse en la implementación de la clase. Una declaración de clase con DECLARE_OLECREATE también debe usar DECLARE_DYNCREATE o DECLARE_SERIAL.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Esta macro o [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) debe aparecer en el `DECLARE_OLECREATE`archivo de implementación para cualquier clase que utilice .

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre real de la clase.

*external_name*<br/>
El nombre del objeto expuesto a otras aplicaciones (entre comillas).

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Componentes del CLSID de la clase.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Si utiliza IMPLEMENT_OLECREATE, de forma predeterminada, solo admite el modelo de subprocesoúnico único. Si utiliza IMPLEMENT_OLECREATE_FLAGS, puede especificar qué modelo de subprocesamiento admite el objeto mediante el parámetro *nFlags.*

El nombre externo es el identificador expuesto a otras aplicaciones. Las aplicaciones cliente usan el nombre externo para solicitar un objeto de esta clase de un servidor de automatización.

El identificador de clase OLE es un identificador único de 128 bits para el objeto. Consta de un **largo,** dos **PALABRAs**s y ocho **BYTE**s, representado por *l*, *w1*, *w2*, y *b1* a *b8* en la descripción de sintaxis. El Asistente para aplicaciones y los asistentes de código crean identificadores de clase OLE únicos según sea necesario.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[Aislamiento de la biblioteca de controles comunes de MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Clave CLSID](/windows/win32/com/clsid-key-hklm)
