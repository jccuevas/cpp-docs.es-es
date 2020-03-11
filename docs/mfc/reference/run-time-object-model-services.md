---
title: Servicios del modelo de objetos en tiempo de ejecución
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f8b891467d91d0c945b6c59c90dbc49fd7cbcb30
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855363"
---
# <a name="run-time-object-model-services"></a>Servicios del modelo de objetos en tiempo de ejecución

Las clases [CObject](../../mfc/reference/cobject-class.md) y [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) encapsulan varios servicios de objeto, incluido el acceso a la información de clase en tiempo de ejecución, la serialización y la creación dinámica de objetos. Todas las clases derivadas de `CObject` heredan esta funcionalidad.

El acceso a la información de clase en tiempo de ejecución le permite determinar la información sobre la clase de un objeto en tiempo de ejecución. La capacidad de determinar la clase de un objeto en tiempo de ejecución es útil cuando se necesita comprobación de tipos adicional de argumentos de función y cuando se debe escribir código de propósito especial basado en la clase de un objeto. El lenguaje no admite directamente la C++ información de clase en tiempo de ejecución.

La serialización es el proceso de escribir o leer el contenido de un objeto en un archivo o desde él. Puede usar la serialización para almacenar el contenido de un objeto incluso después de salir de la aplicación. Después, el objeto se puede leer desde el archivo cuando se reinicie la aplicación. Estos objetos de datos se consideran "persistentes".

La creación dinámica de objetos permite crear un objeto de una clase especificada en tiempo de ejecución. Por ejemplo, los objetos de documento, vista y marco deben admitir la creación dinámica, ya que el marco debe crearlos dinámicamente.

En la tabla siguiente se enumeran las macros de MFC que admiten la información de clase en tiempo de ejecución, la serialización y la creación dinámica.

Para obtener más información sobre estos servicios de objeto en tiempo de ejecución y la serialización, vea el artículo [CObject (clase): obtener acceso a la información de clase en tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Macros de servicios de modelo de objetos en tiempo de ejecución

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Habilita el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Habilita la creación dinámica y el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase).|
|[DECLARE_SERIAL](#declare_serial)|Habilita la serialización y el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Habilita el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Habilita la creación dinámica y el acceso a la información en tiempo de ejecución (debe usarse en la implementación de la clase).|
|[IMPLEMENT_SERIAL](#implement_serial)|Permite la serialización y el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|
|[RUNTIME_CLASS](#runtime_class)|Devuelve el `CRuntimeClass` estructura que corresponde a la clase con nombre.|

OLE suele requerir la creación dinámica de objetos en tiempo de ejecución. Por ejemplo, una aplicación de servidor OLE debe ser capaz de crear elementos OLE dinámicamente en respuesta a una solicitud de un cliente. De forma similar, un servidor de automatización debe ser capaz de crear elementos en respuesta a las solicitudes de los clientes de automatización.

El biblioteca MFC proporciona dos macros específicas de OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Creación dinámica de objetos OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[DECLARE_OLECREATE](#declare_olecreate)|Permite crear objetos mediante la automatización OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Declara las funciones miembro `GetUserTypeNameID` y `GetMiscStatus` de la clase del control.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Declara que el control OLE proporciona una lista de páginas de propiedades para mostrar sus propiedades.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Permite que el sistema OLE cree objetos.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementa las funciones miembro `GetUserTypeNameID` y `GetMiscStatus` de la clase del control.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) debe aparecer en el archivo de implementación para cualquier clase que use `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Determina si la biblioteca de controles comunes implementa la API especificada.

### <a name="syntax"></a>Sintaxis

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parámetros

*proc*<br/>
Puntero a una cadena terminada en null que contiene el nombre de función o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden inferior; la palabra de orden superior debe ser cero. Este parámetro debe estar en Unicode.

### <a name="remarks"></a>Observaciones

Utilice esta macro para determinar si la biblioteca de controles comunes es la función especificada por *proc* (en lugar de llamar a [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Requisitos

afxcomctl32. h, afxcomctl32. INL

## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Determina si la biblioteca de controles comunes implementa la API especificada (esta es la versión Unicode de [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Sintaxis

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parámetros

*proc*<br/>
Puntero a una cadena terminada en null que contiene el nombre de función o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden inferior; la palabra de orden superior debe ser cero. Este parámetro debe estar en Unicode.

### <a name="remarks"></a>Observaciones

Utilice esta macro para determinar si la biblioteca de controles comunes es la función especificada por *proc* (en lugar de llamar a [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). Esta macro es la versión Unicode de AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Requisitos

afxcomctl32. h, afxcomctl32. INL

##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC

Agrega la capacidad de obtener acceso a la información en tiempo de ejecución sobre la clase de un objeto al derivar una clase de `CObject`.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

### <a name="remarks"></a>Observaciones

Agregue la macro DECLARE_DYNAMIC al módulo de encabezado (. h) de la clase y, a continuación, incluya ese módulo en todos los módulos. cpp que necesiten tener acceso a los objetos de esta clase.

Si usa las macros DECLARE_ DYNAMIC y IMPLEMENT_DYNAMIC, tal y como se describe, puede usar la macro RUNTIME_CLASS y la función `CObject::IsKindOf` para determinar la clase de los objetos en tiempo de ejecución.

Si DECLARE_DYNAMIC se incluye en la declaración de clase, IMPLEMENT_DYNAMIC debe incluirse en la implementación de la clase.

Para obtener más información sobre la macro DECLARE_DYNAMIC, vea temas de la [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Permite que los objetos de las clases derivadas de `CObject`se creen dinámicamente en tiempo de ejecución.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

### <a name="remarks"></a>Observaciones

El marco de trabajo usa esta capacidad para crear objetos nuevos dinámicamente. Por ejemplo, la nueva vista que se crea al abrir un nuevo documento. Las clases de documento, vista y marco deben admitir la creación dinámica, ya que el marco debe crearlas dinámicamente.

Agregue la macro DECLARE_DYNCREATE en el módulo. h para la clase y, a continuación, incluya ese módulo en todos los módulos. cpp que necesiten tener acceso a los objetos de esta clase.

Si DECLARE_DYNCREATE se incluye en la declaración de clase, IMPLEMENT_DYNCREATE debe incluirse en la implementación de la clase.

Para obtener más información sobre la macro DECLARE_DYNCREATE, vea temas de la [clase CObject](../../mfc/using-cobject.md).

> [!NOTE]
>  La macro DECLARE_DYNCREATE incluye toda la funcionalidad de DECLARE_DYNAMIC.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Declara las funciones miembro `GetUserTypeNameID` y `GetMiscStatus` de la clase del control.

### <a name="syntax"></a>Sintaxis

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre de la clase del control.

### <a name="remarks"></a>Observaciones

`GetUserTypeNameID` y `GetMiscStatus` son funciones virtuales puras, declaradas en `COleControl`. Dado que estas funciones son virtuales puras, se deben invalidar en la clase del control. Además de DECLARE_OLECTLTYPE, debe agregar la macro IMPLEMENT_OLECTLTYPE a la declaración de clase del control.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl. h

## <a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Declara que el control OLE proporciona una lista de páginas de propiedades para mostrar sus propiedades.

### <a name="syntax"></a>Sintaxis

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre de la clase de control que posee las páginas de propiedades.

### <a name="remarks"></a>Observaciones

Use la macro `DECLARE_PROPPAGEIDS` al final de la declaración de clase. A continuación, en el archivo. cpp que define las funciones miembro de la clase, utilice la macro `BEGIN_PROPPAGEIDS`, las entradas de macro para cada una de las páginas de propiedades de su control y la macro `END_PROPPAGEIDS` para declarar el final de la lista de páginas de propiedades.

Para obtener más información sobre las páginas de propiedades, vea el artículo [controles ActiveX: páginas de propiedades](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl. h

##  <a name="declare_serial"></a>DECLARE_SERIAL

Genera el C++ código de encabezado necesario para una clase derivada de `CObject`que se puede serializar.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

### <a name="remarks"></a>Observaciones

La serialización es el proceso de escribir o leer el contenido de un objeto en un archivo y desde él.

Use la macro DECLARE_SERIAL en un módulo. h y, a continuación, incluya ese módulo en todos los módulos. cpp que necesiten tener acceso a los objetos de esta clase.

Si DECLARE_SERIAL se incluye en la declaración de clase, IMPLEMENT_SERIAL debe incluirse en la implementación de la clase.

La macro DECLARE_SERIAL incluye toda la funcionalidad de DECLARE_DYNAMIC y DECLARE_DYNCREATE.

Puede usar la macro AFX_API para exportar automáticamente el operador de extracción `CArchive` para las clases que utilizan las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Corchete las declaraciones de clase (que se encuentran en el archivo. h) con el código siguiente:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Para obtener más información sobre la macro DECLARE_SERIAL, vea temas de la [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Genera el C++ código necesario para una clase derivada de `CObject`dinámica con acceso en tiempo de ejecución al nombre de la clase y la posición dentro de la jerarquía.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

*base_class_name*<br/>
Nombre de la clase base.

### <a name="remarks"></a>Observaciones

Use la macro IMPLEMENT_DYNAMIC en un módulo. cpp y, a continuación, vincule el código objeto resultante una sola vez.

Para obtener más información, vea temas de la [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Permite que los objetos de las clases derivadas de `CObject`se creen dinámicamente en tiempo de ejecución cuando se usan con la macro DECLARE_DYNCREATE.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

*base_class_name*<br/>
Nombre real de la clase base.

### <a name="remarks"></a>Observaciones

El marco de trabajo usa esta capacidad para crear objetos nuevos dinámicamente, por ejemplo, cuando lee un objeto del disco durante la serialización. Agregue la macro IMPLEMENT_DYNCREATE en el archivo de implementación de clase. Para obtener más información, vea temas de la [clase CObject](../../mfc/using-cobject.md).

Si usa las macros DECLARE_DYNCREATE y IMPLEMENT_DYNCREATE, puede utilizar la macro RUNTIME_CLASS y la función miembro `CObject::IsKindOf` para determinar la clase de los objetos en tiempo de ejecución.

Si DECLARE_DYNCREATE se incluye en la declaración de clase, IMPLEMENT_DYNCREATE debe incluirse en la implementación de la clase.

Tenga en cuenta que esta definición de macro invocará el constructor predeterminado para la clase. Si la clase implementa explícitamente un constructor no trivial, también debe implementar explícitamente el constructor predeterminado. Se puede Agregar el constructor predeterminado a las secciones de miembros **privados** o **protegidos** de la clase para evitar que se llame desde fuera de la implementación de la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) debe aparecer en el archivo de implementación para cualquier clase que use DECLARE_OLECREATE.

### <a name="syntax"></a>Sintaxis

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

*external_name*<br/>
El nombre de objeto expuesto a otras aplicaciones (entre comillas).

*nFlags*<br/>
Contiene una o varias de las marcas siguientes:

   - `afxRegInsertable` permite que el control aparezca en el cuadro de diálogo Insertar objeto para los objetos OLE.
   - `afxRegApartmentThreading` establece el modelo de subprocesos del registro en ThreadingModel = Apartment.
   - `afxRegFreeThreading` establece el modelo de subprocesos del registro en ThreadingModel = Free.

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/win32/com/inprocserver32) in the Windows SDK for more information on threading model registration.

componentes *l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*y *B8* del CLSID de la clase.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  Si usa IMPLEMENT_OLECREATE_FLAGS, puede especificar qué modelo de subprocesos admite el objeto mediante el parámetro *nFlags* . Si desea admitir solo el modelo de una sola línea, use IMPLEMENT_OLECREATE.

El nombre externo es el identificador expuesto a otras aplicaciones. Las aplicaciones cliente utilizan el nombre externo para solicitar un objeto de esta clase de un servidor de automatización.

El identificador de clase OLE es un identificador único de 128 bits para el objeto. Consta de una **longitud larga**, dos **palabras**y ocho **bytes**, como se representa mediante *l*, *W1*, *W2*y *B1* hasta *B8* en la descripción de la sintaxis. El Asistente para aplicaciones y los asistentes para código crean identificadores de clase OLE únicos según sea necesario.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementa las funciones miembro `GetUserTypeNameID` y `GetMiscStatus` de la clase del control.

### <a name="syntax"></a>Sintaxis

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre de la clase del control.

*idsUserTypeName*<br/>
El identificador de recurso de una cadena que contiene el nombre externo del control.

*dwOleMisc*<br/>
Una enumeración que contiene una o varias marcas. Para obtener más información sobre esta enumeración, vea [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Además de IMPLEMENT_OLECTLTYPE, debe agregar la macro DECLARE_OLECTLTYPE a la declaración de clase del control.

La función miembro `GetUserTypeNameID` devuelve la cadena de recurso que identifica la clase de control. `GetMiscStatus` devuelve los bits OLEMISC para el control. Esta enumeración especifica una colección de valores de configuración que describen las características varias del control. Para obtener una descripción completa de la configuración de OLEMISC, consulte [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) en el Windows SDK.

> [!NOTE]
>  La configuración predeterminada utilizada por el ControlWizard de ActiveX es: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE y OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxctl. h

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL

Genera el C++ código necesario para una clase derivada de `CObject`dinámica con acceso en tiempo de ejecución al nombre de la clase y la posición dentro de la jerarquía.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

*base_class_name*<br/>
Nombre de la clase base.

*wSchema*<br/>
Un UINT "número de versión" que se codificará en el archivo para permitir que un programa de deserialización identifique y controle los datos creados por versiones anteriores del programa. El número de esquema de clase no debe ser-1.

### <a name="remarks"></a>Observaciones

Use la macro IMPLEMENT_SERIAL en un módulo. cpp; a continuación, vincule solo una vez el código del objeto resultante.

Puede usar la macro AFX_API para exportar automáticamente el operador de extracción `CArchive` para las clases que utilizan las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Corchete las declaraciones de clase (que se encuentran en el archivo. h) con el código siguiente:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Para obtener más información, vea los temas de la [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="runtime_class"></a>RUNTIME_CLASS

Obtiene la estructura de clase en tiempo de ejecución desde el nombre C++ de una clase.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase (no entre comillas).

### <a name="remarks"></a>Observaciones

RUNTIME_CLASS devuelve un puntero a una estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) para la clase especificada por *CLASS_NAME*. Solo las clases derivadas de `CObject`declaradas con DECLARE_DYNAMIC, DECLARE_DYNCREATE o DECLARE_SERIAL devolverán punteros a una estructura de `CRuntimeClass`.

Para obtener más información, vea temas de la [clase CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="declare_olecreate"></a>DECLARE_OLECREATE

Permite crear objetos de clases derivadas de `CCmdTarget`mediante la automatización OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

### <a name="remarks"></a>Observaciones

Esta macro permite a otras aplicaciones habilitadas para OLE crear objetos de este tipo.

Agregue la macro DECLARE_OLECREATE en el módulo. h para la clase y, a continuación, incluya ese módulo en todos los módulos. cpp que necesiten tener acceso a los objetos de esta clase.

Si DECLARE_OLECREATE se incluye en la declaración de clase, IMPLEMENT_OLECREATE debe incluirse en la implementación de la clase. Una declaración de clase que usa DECLARE_OLECREATE también debe utilizar DECLARE_DYNCREATE o DECLARE_SERIAL.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Esta macro o [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) debe aparecer en el archivo de implementación para cualquier clase que use `DECLARE_OLECREATE`.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre real de la clase.

*external_name*<br/>
El nombre de objeto expuesto a otras aplicaciones (entre comillas).

componentes *l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*y *B8* del CLSID de la clase.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  Si utiliza IMPLEMENT_OLECREATE, de forma predeterminada, solo admitirá el modelo de subprocesos único. Si usa IMPLEMENT_OLECREATE_FLAGS, puede especificar qué modelo de subprocesos admite el objeto mediante el parámetro *nFlags* .

El nombre externo es el identificador expuesto a otras aplicaciones. Las aplicaciones cliente utilizan el nombre externo para solicitar un objeto de esta clase de un servidor de automatización.

El identificador de clase OLE es un identificador único de 128 bits para el objeto. Consta de una **longitud larga**, dos **palabras**y ocho **bytes**, como se representa mediante *l*, *W1*, *W2*y *B1* hasta *B8* en la descripción de la sintaxis. El Asistente para aplicaciones y los asistentes para código crean identificadores de clase OLE únicos según sea necesario.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[Aislamiento de la biblioteca de controles comunes de MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Clave CLSID](/windows/win32/com/clsid-key-hklm)
