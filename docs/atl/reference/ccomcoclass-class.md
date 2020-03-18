---
title: CComCoClass (clase)
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 5b4e39fa4d93893d288bb8de03d8a71b671be087
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423337"
---
# <a name="ccomcoclass-class"></a>CComCoClass (clase)

Esta clase proporciona métodos para crear instancias de una clase y obtener sus propiedades.

## <a name="syntax"></a>Sintaxis

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `CComCoClass`.

*pclsid*<br/>
Puntero al CLSID del objeto.

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCoClass:: CreateInstance](#createinstance)|Estático Crea una instancia de la clase y consulta una interfaz.|
|[CComCoClass:: error](#error)|Estático Devuelve información de error enriquecida al cliente.|
|[CComCoClass:: GetObjectCLSID](#getobjectclsid)|Estático Devuelve el identificador de clase del objeto.|
|[CComCoClass:: GetObjectDescription](#getobjectdescription)|Estático Invalide para devolver la descripción del objeto.|

## <a name="remarks"></a>Observaciones

`CComCoClass` proporciona métodos para recuperar el CLSID de un objeto, establecer la información de error y crear instancias de la clase. Cualquier clase registrada en el mapa de objetos se debe derivar de `CComCoClass`.

`CComCoClass` también define el generador de clases predeterminado y el modelo de agregación para el objeto. `CComCoClass` usa las dos macros siguientes:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Declara que el generador de clases es [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Declara que se puede Agregar el objeto.

Puede invalidar cualquiera de estos valores predeterminados especificando otra macro en la definición de clase. Por ejemplo, para usar [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) en lugar de `CComClassFactory`, especifique la macro [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="createinstance"></a>CComCoClass:: CreateInstance

Use estas funciones de `CreateInstance` para crear una instancia de un objeto COM y recuperar un puntero de interfaz sin usar la API de COM.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parámetros

*Q*<br/>
La interfaz COM que se debe devolver mediante *PP*.

*punkOuter*<br/>
de El externo desconocido o que controla el desconocido del agregado.

*páginas*<br/>
enuncia Dirección de una variable de puntero que recibe el puntero de interfaz solicitado Si la creación se realiza correctamente.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar. Vea [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) en el Windows SDK para obtener una descripción de los posibles valores devueltos.

### <a name="remarks"></a>Observaciones

Use la primera sobrecarga de esta función para la creación de objetos típica; Use la segunda sobrecarga cuando necesite agregar el objeto que se va a crear.

La clase ATL que implementa el objeto COM requerido (es decir, la clase que se usa como primer parámetro de plantilla en [CComCoClass](../../atl/reference/ccomcoclass-class.md)) debe estar en el mismo proyecto que el código de llamada. La creación del objeto COM se realiza mediante el generador de clases registrado para esta clase ATL.

Estas funciones son útiles para crear objetos que se han impedido que se puedan crear externamente mediante el uso de la macro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) . También son útiles en situaciones en las que desea evitar la API de COM por motivos de eficacia.

Tenga en cuenta que la interfaz *Q* debe tener asociado un IID que se pueda recuperar mediante el operador [__uuidof](../../cpp/uuidof-operator.md) .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, `CDocument` es una clase ATL generada por el asistente derivada de `CComCoClass` que implementa la interfaz `IDocument`. La clase se registra en el mapa de objetos con la OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO macro para que los clientes no puedan crear instancias del documento mediante [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication` es una coclase que proporciona un método en una de sus propias interfaces COM para crear instancias de la clase de documento. En el código siguiente se muestra lo fácil que es crear instancias de la clase de documento mediante el `CreateInstance` miembro heredado de la clase base `CComCoClass`.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>CComCoClass:: error

Esta función estática configura la interfaz `IErrorInfo` para proporcionar información de error al cliente.

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parámetros

*lpszDesc*<br/>
de Cadena que describe el error. La versión Unicode de `Error` especifica que *lpszDesc* es de tipo LPCOLESTR; la versión ANSI especifica un tipo de LPCSTR.

*suscripto*<br/>
de IID de la interfaz que define el error o GUID_NULL (el valor predeterminado) si el sistema operativo define el error.

*hRes*<br/>
de HRESULT que se va a devolver al autor de la llamada. El valor predeterminado es 0. Para obtener más información sobre *hRes*, consulte la sección Comentarios.

*nID*<br/>
de Identificador de recurso donde se almacena la cadena de Descripción del error. Este valor debe estar entre 0x0200 y 0xFFFF, ambos inclusive. En las compilaciones de depuración, se producirá una **aserción** si *nID* no indiza una cadena válida. En las compilaciones de versión, la cadena de Descripción del error se establecerá en "error desconocido".

*dwHelpID*<br/>
de Identificador del contexto de ayuda para el error.

*lpszHelpFile*<br/>
de La ruta de acceso y el nombre del archivo de ayuda que describe el error.

*hInst*<br/>
de Identificador del recurso. De forma predeterminada, este parámetro es `_AtlModule::GetResourceInstance`, donde `_AtlModule` es la instancia global de [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Para llamar a `Error`, el objeto debe implementar la interfaz `ISupportErrorInfo Interface`.

Si el parámetro *hRes* es distinto de cero, `Error` devuelve el valor de *hRes*. Si *hRes* es cero, las cuatro primeras versiones de `Error` devuelven DISP_E_EXCEPTION. Las dos últimas versiones devuelven el resultado de la macro **MAKE_HRESULT (1, FACILITY_ITF,** *nID* **)** .

##  <a name="getobjectclsid"></a>CComCoClass:: GetObjectCLSID

Proporciona una manera coherente de recuperar el CLSID del objeto.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Valor devuelto

Identificador de clase del objeto.

##  <a name="getobjectdescription"></a>CComCoClass:: GetObjectDescription

Esta función estática recupera la descripción de texto para el objeto de clase.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Valor devuelto

La descripción del objeto de clase.

### <a name="remarks"></a>Observaciones

La implementación predeterminada devuelve NULL. Puede invalidar este método con la macro [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) . Por ejemplo:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`IComponentRegistrar::GetComponents`llama a `GetObjectDescription`. `IComponentRegistrar` es una interfaz de automatización que permite registrar y anular el registro de componentes individuales en un archivo DLL. Al crear un objeto de registrador de componentes con el Asistente para proyectos ATL, el asistente implementará automáticamente la interfaz `IComponentRegistrar`. Microsoft Transaction Server usa normalmente `IComponentRegistrar`.

Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../../atl/atl-class-overview.md)
