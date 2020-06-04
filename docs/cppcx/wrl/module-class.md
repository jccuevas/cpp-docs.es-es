---
title: Module (clase)
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: afd2edacefdf5d62b50a03c0a8c37f13ee5d9c9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371317"
---
# <a name="module-class"></a>Module (clase)

Representa una colección de objetos relacionados.

## <a name="syntax"></a>Sintaxis

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>Parámetros

*moduleType*<br/>
Combinación de uno o varios valores de enumeración [ModuleType.](moduletype-enumeration.md)

## <a name="members"></a>Miembros

### <a name="protected-classes"></a>Clases protegidas

Nombre                                                                                | Descripción
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Módulo::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica en un lambda, functor o puntero a función.
[Módulo::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante un objeto y su puntero a un método miembro.
[Módulo::ReleaseNotifier](module-releasenotifier-class.md)               | Invoca un controlador de eventos cuando se libera el último objeto de un módulo.

### <a name="public-constructors"></a>Constructores públicos

Nombre                             | Descripción
-------------------------------- | -----------------------------------------------------------
[Módulo::-Módulo](#tilde-module) | Desinicializa la instancia `Module` actual de la clase.

### <a name="protected-constructors"></a>Constructores protegidos

Nombre                      | Descripción
------------------------- | ---------------------------------------------------
[Módulo::Módulo](#module) | Inicializa una nueva instancia de la clase `Module`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                    | Descripción
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Módulo::Crear](#create)                               | Crea una instancia de un módulo.
[Module::DecrementObjectCount](#decrementobjectcount)   | Disminuye el número de objetos rastreados por el módulo.
[Módulo::GetActivationFactory](#getactivationfactory)   | Obtiene una fábrica de activación para el módulo.
[Módulo::GetClassObject](#getclassobject)               | Recupera una memoria caché de generadores de clases.
[Módulo::GetModule](#getmodule)                         | Crea una instancia de un módulo.
[Módulo::GetObjectCount](#getobjectcount)               | Recupera el número de objetos administrados por este módulo.
[Módulo::IncrementObjectCount](#incrementobjectcount)   | Incrementa el número de objetos rastreados por el módulo.
[Módulo::RegisterCOMObject](#registercomobject)         | Registra uno o más objetos COM para que otras aplicaciones puedan conectarse a ellos.
[Módulo::RegisterObjects](#registerobjects)             | Registra objetos COM o Windows Runtime para que otras aplicaciones puedan conectarse a ellos.
[Módulo::RegisterWinRTObject](#registerwinrtobject)     | Registra uno o varios objetos de Windows Runtime para que otras aplicaciones puedan conectarse a ellos.
[Módulo::Terminar](#terminate)                         | Hace que todas las fábricas creadas por el módulo se apaguen.
[Módulo::UnregisterCOMObject](#unregistercomobject)     | Anula el registro de uno o varios objetos COM, lo que impide que otras aplicaciones se conecten a ellos.
[Module::UnregisterObjects](#unregisterobjects)         | Anula el registro de los objetos en el módulo especificado para que otras aplicaciones no puedan conectarse a ellos.
[Módulo::UnregisterWinRTObject](#unregisterwinrtobject) | Anula el registro de uno o varios objetos de Windows Runtime para que otras aplicaciones no puedan conectarse a ellos.

### <a name="protected-methods"></a>Métodos protegidos

Nombre                      | Descripción
------------------------- | --------------------------------
[Módulo::Crear](#create) | Crea una instancia de un módulo.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                                         | Descripción
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Módulo::objectCount_](#objectcount)         | Realiza un seguimiento de cuántas clases se han creado con la función [Make.](make-function.md)
[Módulo::releaseNotifier_](#releasenotifier) | Mantiene un puntero `ReleaseNotifier` a un objeto.

### <a name="macros"></a>Macros

Nombre                                                                   | Descripción
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | Rellena una memoria caché interna que contiene un generador que puede crear una instancia de la clase especificada. Esta macro especifica los parámetros predeterminados de ID de grupo y de fábrica.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Rellena una memoria caché interna que contiene un generador que puede crear una instancia de la clase especificada. Esta macro le permite especificar un parámetro de fábrica determinado.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Rellena una memoria caché interna que contiene un generador que puede crear una instancia de la clase especificada. Esta macro le permite especificar determinados parámetros de ID de fábrica y grupo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Módulo::-Módulo

Desinicializa la instancia `Module` actual de la clase.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Módulo::Crear

Crea una instancia de un módulo.

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de módulo.

*devolución de llamada*<br/>
Se llama cuando se libera el último objeto de instancia del módulo.

*object*<br/>
Los parámetros *de objeto* y *método* se utilizan en combinación. Apunta al último objeto de instancia cuando se libera el último objeto de instancia del módulo.

*method*<br/>
Los parámetros *de objeto* y *método* se utilizan en combinación. Apunta al método del último objeto de instancia cuando se libera el último objeto de instancia del módulo.

### <a name="return-value"></a>Valor devuelto

Referencia al módulo.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>Module::DecrementObjectCount

Disminuye el número de objetos rastreados por el módulo.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Valor devuelto

El conteo antes de la operación de decremento.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Módulo::GetActivationFactory

Obtiene una fábrica de activación para el módulo.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parámetros

*pActivatibleClassId*<br/>
IID de una clase en tiempo de ejecución.

*ppIFactory*<br/>
IActivationFactory para la clase de tiempo de ejecución especificada.

*Nombredeservidor*<br/>
El nombre de un subconjunto de generadores de clases en el módulo actual. Especifique el nombre del servidor utilizado en la macro `nullptr` [ActivatableClassWithFactoryEx](activatableclass-macros.md) o especifique para obtener el nombre de servidor predeterminado.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, el HRESULT devuelto por GetActivationFactory.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Módulo::GetClassObject

Retreives un caché de fábricas de clases.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
ID de clase.

*riid*<br/>
ID de interfaz que solicite.

*Ppv*<br/>
Puntero al objeto devuelto.

*Nombredeservidor*<br/>
El nombre del servidor que `ActivatableClassWithFactory`se `ActivatableClassWithFactoryEx`especifica `ActivatableClass` en la , , o macro; o `nullptr` para obtener el nombre de servidor predeterminado.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Utilice este método solo para COM, no para Windows Runtime. Este método expone `IClassFactory` solo los métodos.

## <a name="modulegetmodule"></a><a name="getmodule"></a>Módulo::GetModule

Crea una instancia de un módulo.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a un módulo.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Módulo::GetObjectCount

Recupera el número de objetos administrados por este módulo.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número actual de objetos administrados por este módulo.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Módulo::IncrementObjectCount

Incrementa el número de objetos rastreados por el módulo.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de incremento.

## <a name="modulemodule"></a><a name="module"></a>Módulo::Módulo

Inicializa una nueva instancia de la clase `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Observaciones

Este constructor está protegido y `new` no se puede llamar con la palabra clave. En su lugar, llame a [Module::GetModule](#getmodule) o [Module::Create](#create).

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Módulo::objectCount_

Realiza un seguimiento de cuántas clases se han creado con la función [Make.](make-function.md)

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Módulo::RegisterCOMObject

Registra uno o más objetos COM para que otras aplicaciones puedan conectarse a ellos.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Parámetros

*Nombredeservidor*<br/>
Nombre completo de un servidor.

*Clsid*<br/>
Matriz de CLSAD para registrar.

*factories*<br/>
Matriz de interfaces IUnknown de los objetos de clase cuya disponibilidad se está publicando.

*cookies*<br/>
Cuando se completa la operación, una matriz de punteros a valores que identifican los objetos de clase que se registraron. Estos valores se utilizan más adelante revocar el registro.

*count*<br/>
El número de CLSAD que se deben registrar.

### <a name="return-value"></a>Valor devuelto

S_OK si successfu; de lo contrario, un HRESULT como CO_E_OBJISREG que indica el motivo por el que se produjo un error en la operación.

### <a name="remarks"></a>Observaciones

Los objetos COM se registran con el enumerador CLSCTX_LOCAL_SERVER de la enumeración CLSCTX.

El tipo de conexión a los objetos registrados se especifica mediante una combinación del parámetro de plantilla *comflag* actual y el enumerador de REGCLS_SUSPENDED de la enumeración REGCLS.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Módulo::RegisterObjects

Registra objetos COM o Windows Runtime para que otras aplicaciones puedan conectarse a ellos.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parámetros

*Módulo*<br/>
Matriz de objetos COM o Windows Runtime.

*Nombredeservidor*<br/>
Nombre del servidor que creó los objetos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el motivo por el que falló la operación.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Módulo::RegisterWinRTObject

Registra uno o varios objetos de Windows Runtime para que otras aplicaciones puedan conectarse a ellos.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parámetros

*Nombredeservidor*<br/>
Nombre que especifica un subconjunto de objetos afectados por esta operación.

*activatableClassIds*<br/>
Matriz de CLSIR activables para registrar.

*Galleta*<br/>
Valor que identifica los objetos de clase que se registraron. Este valor se utiliza más adelante para revocar el registro.

*count*<br/>
El número de objetos que se registrarán.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un error HRESULT como CO_E_OBJISREG que indica el motivo por el que se produjo un error en la operación.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Módulo::releaseNotifier_

Mantiene un puntero `ReleaseNotifier` a un objeto.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Módulo::Terminar

Hace que todas las fábricas creadas por el módulo se apaguen.

```cpp
void Terminate();
```

### <a name="remarks"></a>Observaciones

Libera las fábricas en la memoria caché.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Módulo::UnregisterCOMObject

Anula el registro de uno o varios objetos COM, lo que impide que otras aplicaciones se conecten a ellos.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parámetros

*Nombredeservidor*<br/>
(Sin usar)

*cookies*<br/>
Matriz de punteros a valores que identifican los objetos de clase que se van a anular el registro. La matriz fue creada por el [RegisterCOMObject](#registercomobject) método.

*count*<br/>
El número de clases que se anula el registro.

### <a name="return-value"></a>Valor devuelto

S_OK si esta operación se realiza correctamente; de lo contrario, un error HRESULT que indica el motivo por el que la operación falló.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Module::UnregisterObjects

Anula el registro de los objetos en el módulo especificado para que otras aplicaciones no puedan conectarse a ellos.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parámetros

*Módulo*<br/>
Puntero a un módulo.

*Nombredeservidor*<br/>
Nombre calificado que especifica un subconjunto de objetos afectados por esta operación.

### <a name="return-value"></a>Valor devuelto

S_OK si esta operación se realiza correctamente; de lo contrario, un error HRESULT que indica el motivo por el que esta operación falló.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Módulo::UnregisterWinRTObject

Anula el registro de uno o varios objetos de Windows Runtime para que otras aplicaciones no puedan conectarse a ellos.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parámetros

*Galleta*<br/>
Puntero a un valor que identifica el objeto de clase cuyo registro se va a revocar.
