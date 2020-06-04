---
title: Clase CComCoClass
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
ms.openlocfilehash: 11e724a982f3a2f404473dbdd34d848842cc8e14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320821"
---
# <a name="ccomcoclass-class"></a>Clase CComCoClass

Esta clase proporciona métodos para crear instancias de una clase y obtener sus propiedades.

## <a name="syntax"></a>Sintaxis

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `CComCoClass`de .

*pclsid*<br/>
Un puntero al CLSID del objeto.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCoClass::CreateInstance](#createinstance)|(Estático) Crea una instancia de la clase y consulta una interfaz.|
|[CComCoClass::Error](#error)|(Estático) Devuelve información de error enriquecida al cliente.|
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Estático) Devuelve el identificador de clase del objeto.|
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Estático) Reemplazar para devolver la descripción del objeto.|

## <a name="remarks"></a>Observaciones

`CComCoClass`proporciona métodos para recuperar el CLSID de un objeto, establecer información de error y crear instancias de la clase. Cualquier clase registrada en el mapa `CComCoClass`de objetos debe derivarse de .

`CComCoClass`también define el generador de clases predeterminado y el modelo de agregación para el objeto. `CComCoClass`utiliza las dos macros siguientes:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Declara que el generador de clases es [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Declara que el objeto se puede agregar.

Puede invalidar cualquiera de estos valores predeterminados especificando otra macro en la definición de clase. Por ejemplo, para utilizar [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) en lugar de `CComClassFactory`, especifique la macro [DECLARE_CLASSFACTORY2:](aggregation-and-class-factory-macros.md#declare_classfactory2)

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a>CComCoClass::CreateInstance

Utilice `CreateInstance` estas funciones para crear una instancia de un objeto COM y recuperar un puntero de interfaz sin usar la API COM.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parámetros

*Q*<br/>
La interfaz COM que se debe devolver a través *de pp*.

*punkOuter*<br/>
[en] El exterior desconocido o control desconocido del agregado.

*Pp*<br/>
[fuera] La dirección de una variable de puntero que recibe el puntero de interfaz solicitado si la creación se realiza correctamente.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar. Consulte [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) en el Windows SDK para obtener una descripción de los posibles valores devueltos.

### <a name="remarks"></a>Observaciones

Utilice la primera sobrecarga de esta función para la creación de objetos típicos; utilice la segunda sobrecarga cuando necesite agregar el objeto que se está creando.

La clase ATL que implementa el objeto COM necesario (es decir, la clase utilizada como primer parámetro de plantilla para [CComCoClass](../../atl/reference/ccomcoclass-class.md)) debe estar en el mismo proyecto que el código de llamada. La creación del objeto COM se lleva a cabo por el generador de clases registrado para esta clase ATL.

Estas funciones son útiles para crear objetos que ha impedido que se puedan crear externamente mediante la macro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.](object-map-macros.md#object_entry_non_createable_ex_auto) También son útiles en situaciones en las que desea evitar la API COM por razones de eficiencia.

Tenga en cuenta que la interfaz *Q* debe tener un IID asociado que se pueda recuperar mediante el operador [__uuidof.](../../cpp/uuidof-operator.md)

### <a name="example"></a>Ejemplo

En el ejemplo `CDocument` siguiente, es una clase ATL `CComCoClass` generada por `IDocument` el asistente derivada de la que implementa la interfaz. La clase se registra en el mapa de objetos con la macro OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO para que los clientes no puedan crear instancias del documento mediante [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication`es una CoClass que proporciona un método en una de sus propias interfaces COM para crear instancias de la clase de documento. El código siguiente muestra lo fácil que es crear `CreateInstance` instancias `CComCoClass` de la clase de documento mediante el miembro heredado de la clase base.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a>CComCoClass::Error

Esta función estática `IErrorInfo` configura la interfaz para proporcionar información de error al cliente.

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
[en] Cadena que describe el error. La versión `Error` Unicode de especifica que *lpszDesc* es de tipo LPCOLESTR; la versión ANSI especifica un tipo de LPCSTR.

*Iid*<br/>
[en] El IID de la interfaz que define el error o GUID_NULL (el valor predeterminado) si el error lo define el sistema operativo.

*hRes*<br/>
[en] El valor HRESULT que desea que se devuelva al autor de la llamada. El valor predeterminado es 0. Para obtener más información acerca de *hRes*, consulte Comentarios.

*nID*<br/>
[en] Identificador de recurso donde se almacena la cadena de descripción del error. Este valor debe estar entre 0x0200 y 0xFFFF, inclusive. En compilaciones de depuración, se producirá un **ASSERT** si *nID* no indexa una cadena válida. En las compilaciones de la versión, la cadena de descripción del error se establecerá en "Error desconocido."

*dwHelpID*<br/>
[en] Identificador de contexto de ayuda para el error.

*lpszHelpFile*<br/>
[en] La ruta de acceso y el nombre del archivo de ayuda que describe el error.

*hInst*<br/>
[en] El identificador del recurso. De forma predeterminada, `_AtlModule::GetResourceInstance`este `_AtlModule` parámetro es , donde está la instancia global de [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Para `Error`llamar a , `ISupportErrorInfo Interface` el objeto debe implementar la interfaz.

Si el *hRes* parámetro es `Error` distinto de cero, a continuación, devuelve el valor de *hRes*. Si *hRes* es cero, las `Error` primeras cuatro versiones de return DISP_E_EXCEPTION. Las dos últimas versiones devuelven el resultado de la macro **MAKE_HRESULT( 1, FACILITY_ITF,** *nID* **).**

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CComCoClass::GetObjectCLSID

Proporciona una forma coherente de recuperar el CLSID del objeto.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Valor devuelto

Identificador de clase del objeto.

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CComCoClass::GetObjectDescription

Esta función estática recupera la descripción de texto del objeto de clase.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Valor devuelto

Descripción del objeto de clase.

### <a name="remarks"></a>Observaciones

La implementación predeterminada devuelve NULL. Puede invalidar este método con la [macro DECLARE_OBJECT_DESCRIPTION.](object-map-macros.md#declare_object_description) Por ejemplo:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`es llamado `IComponentRegistrar::GetComponents`por . `IComponentRegistrar`es una interfaz de automatización que le permite registrar y anular el registro de componentes individuales en un archivo DLL. Al crear un objeto Deregistrador de componentes con el `IComponentRegistrar` Asistente para proyectos ATL, el asistente implementará automáticamente la interfaz. `IComponentRegistrar`normalmente lo utiliza Microsoft Transaction Server.

Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
