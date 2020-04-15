---
title: Clase CComObjectRootEx
ms.date: 11/04/2016
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: e8db86f6214f95cd9bb08d3b5f6c6c1a38ca475c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327602"
---
# <a name="ccomobjectrootex-class"></a>Clase CComObjectRootEx

Esta clase proporciona métodos para controlar la administración de recuento de referencias de objetos para objetos no agregados y agregados.

## <a name="syntax"></a>Sintaxis

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parámetros

*ThreadModel*<br/>
La clase cuyos métodos implementan el modelo de subprocesos deseado. Puede elegir explícitamente el modelo de subprocesos estableciendo *ThreadModel* en [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Puede aceptar el modelo de subprocesos predeterminado del servidor estableciendo *ThreadModel* en [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) o [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Constructor.|
|[InternalAddRef](#internaladdref)|Incrementa el recuento de referencias para un objeto no agregado.|
|[InternalRelease](#internalrelease)|Disminuye el recuento de referencias para un objeto no agregado.|
|[Bloquear](#lock)|Si el modelo de subprocesos es multiproceso, obtiene la propiedad de un objeto de sección crítica.|
|[Desbloquear](#unlock)|Si el modelo de subprocesos es multiproceso, libera la propiedad de un objeto de sección crítica.|

### <a name="ccomobjectrootbase-methods"></a>Métodos CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Invalide la clase para realizar cualquier inicialización requerida por el objeto.|
|[FinalRelease](#finalrelease)|Invalide la clase para realizar cualquier limpieza requerida por el objeto.|
|[OuterAddRef](#outeraddref)|Incrementa el recuento de referencias de un objeto agregado.|
|[OuterQueryInterface](#outerqueryinterface)|Delega en `IUnknown` el exterior de un objeto agregado.|
|[OuterRelease](#outerrelease)|Disminuye el recuento de referencias para un objeto agregado.|

### <a name="static-functions"></a>Funciones estáticas

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Delega `IUnknown` en el de un objeto no agregado.|
|[ObjectMain](#objectmain)|Se llama durante la inicialización y terminación del módulo para las clases derivadas enumeradas en el mapa de objetos.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_dwRef](#m_dwref)|Con `m_pOuterUnknown`, parte de un sindicato. Se utiliza cuando el objeto no se `AddRef` agrega `Release`para contener el recuento de referencias de y .|
|[m_pOuterUnknown](#m_pouterunknown)|Con `m_dwRef`, parte de un sindicato. Se utiliza cuando el objeto se agrega para contener un puntero a la desconocida externa.|

## <a name="remarks"></a>Observaciones

`CComObjectRootEx`controla la administración del recuento de referencias de objetos para objetos no agregados y agregados. Contiene el recuento de referencias de objeto si el objeto no se está agregando y mantiene el puntero a la incógnita externa si el objeto se está agregando. Para los objetos agregados, `CComObjectRootEx` se pueden utilizar métodos para controlar el error del objeto interno que se va a construir y para proteger el objeto externo de la eliminación cuando se liberan interfaces internas o se elimina el objeto interno.

Una clase que implementa un servidor `CComObjectRootEx` COM debe heredar de o [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Si la definición de clase especifica la macro `CComPolyObject<CYourClass>` `IClassFactory::CreateInstance` [DECLARE_POLY_AGGREGATABLE,](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) ATL crea una instancia de when se llama. Durante la creación, se comprueba el valor de la incógnita externa. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si el desconocido externo `IUnknown` no es NULL, se implementa para un objeto agregado.

Si la clase no especifica la macro DECLARE_POLY_AGGREGATABLE, `CAggComObject<CYourClass>` ATL crea una `CComObject<CYourClass>` instancia de objetos agregados o una instancia de objetos no agregados.

La ventaja `CComPolyObject` de usar es `CComAggObject` que `CComObject` evita tener ambos y en el módulo para manejar los casos agregados y no agregados. Un `CComPolyObject` solo objeto controla ambos casos. Por lo tanto, sólo existe una copia de la vtable y una copia de las funciones en el módulo. Si su vtable es grande, esto puede disminuir sustancialmente el tamaño del módulo. Sin embargo, si la `CComPolyObject` vtable es pequeña, el uso puede dar lugar a un tamaño de `CComAggObject` `CComObject`módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, tal como son y .

Si el objeto se agrega, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) se implementa por `CComAggObject` o `CComPolyObject`. Estas `QueryInterface`clases delegan `CComObjectRootEx`, `OuterQueryInterface` `AddRef` `OuterAddRef`, `OuterRelease` y `Release` llama a 's , , y para reenviar al desconocido externo. Normalmente, se `CComObjectRootEx::FinalConstruct` reemplaza en la clase para crear `CComObjectRootEx::FinalRelease` los objetos agregados y se invalida para liberar los objetos agregados.

Si el objeto no `IUnknown` está agregado, `CComObject` `CComPolyObject`se implementa mediante o . En este caso, `QueryInterface` `AddRef`las `Release` llamadas a `CComObjectRootEx`, `InternalQueryInterface` `InternalAddRef`, `InternalRelease` y se delegan en 's , , y para realizar las operaciones reales.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx

El constructor inicializa el recuento de referencias en 0.

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct

Puede invalidar este método en la clase derivada para realizar cualquier inicialización necesaria para el objeto.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en el éxito o uno de los valores HRESULT de error estándar.

### <a name="remarks"></a>Observaciones

De forma `CComObjectRootEx::FinalConstruct` predeterminada, simplemente devuelve S_OK.

Hay ventajas para realizar `FinalConstruct` la inicialización en lugar del constructor de la clase:

- No puede devolver un código de estado de un constructor, `FinalConstruct`pero puede devolver un valor HRESULT mediante 's valor devuelto. Cuando se crean objetos de la clase utilizando el generador de clases estándar proporcionado por ATL, este valor devuelto se propaga de nuevo al cliente COM, lo que le permite proporcionar información de error detallada.

- No se pueden llamar a funciones virtuales a través del mecanismo de función virtual desde el constructor de una clase. Llamar a una función virtual desde el constructor de una clase da como resultado una llamada resuelta estáticamente a la función tal como se define en ese momento en la jerarquía de herencia. Las llamadas a funciones virtuales puras producen errores del vinculador.

   La clase no es la clase más derivada de la jerarquía de herencia: se basa en una clase derivada proporcionada por ATL para proporcionar parte de su funcionalidad. Hay una buena probabilidad de que la inicialización necesite usar las características proporcionadas por esa clase (esto es ciertamente cierto cuando los objetos de la clase necesitan agregar otros objetos), pero el constructor de la clase no tiene forma de tener acceso a esas características. El código de construcción de la clase se ejecuta antes de que se construya completamente la clase más derivada.

   Sin `FinalConstruct` embargo, se llama inmediatamente después de que la clase más derivada se construye completamente, lo que le permite llamar a funciones virtuales y usar la implementación de recuento de referencias proporcionada por ATL.

### <a name="example"></a>Ejemplo

Normalmente, invalide este método en `CComObjectRootEx` la clase derivada de para crear cualquier objeto agregado. Por ejemplo:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Si se produce un error en la construcción, puede devolver un error. También puede utilizar la [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) de macro para proteger el objeto externo de eliminarse si, durante la creación, el objeto agregado interno incrementa el recuento de referencias y, a continuación, reduce el recuento a 0.

Esta es una manera típica de crear un agregado:

- Agregue `IUnknown` un puntero al objeto de clase e inicialícelo en NULL en el constructor.

- Reemplazar `FinalConstruct` para crear el agregado.

- Utilice `IUnknown` el puntero que definió como parámetro para la macro [COM_INTERFACE_ENTRY_AGGREGATE.](com-interface-entry-macros.md#com_interface_entry_aggregate)

- Reemplazar `FinalRelease` para `IUnknown` liberar el puntero.

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx::FinalRelease

Puede invalidar este método en la clase derivada para realizar cualquier limpieza necesaria para el objeto.

```
void FinalRelease();
```

### <a name="remarks"></a>Observaciones

De forma `CComObjectRootEx::FinalRelease` predeterminada, no hace nada.

Realizar la `FinalRelease` limpieza en es preferible a agregar código al destructor de la clase, `FinalRelease` ya que el objeto todavía está completamente construido en el punto en el que se llama. Esto le permite tener acceso seguro a los métodos proporcionados por la clase más derivada. Esto es especialmente importante para liberar cualquier objeto agregado antes de la eliminación.

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx::InternalAddRef

Incrementa el recuento de referencias de un objeto no agregado en 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos y pruebas.

### <a name="remarks"></a>Observaciones

Si el modelo de subprocesos es multiproceso, `InterlockedIncrement` se usa para evitar que más de un subproceso cambie el recuento de referencias al mismo tiempo.

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface

Recupera un puntero a la interfaz solicitada.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*pEsto*<br/>
[en] Puntero al objeto que contiene el mapa COM `QueryInterface`de interfaces expuestas a .

*pEntries*<br/>
[en] Puntero a `_ATL_INTMAP_ENTRY` la estructura que tiene acceso a un mapa de interfaces disponibles.

*Iid*<br/>
[en] GUID de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz especificado en *iid*, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

`InternalQueryInterface` solo administra interfaces de la tabla de asignación COM. Si el objeto se `InternalQueryInterface` agrega, no delega en el desconocido externo. Puede introducir interfaces en la tabla de mapas COM con la [macro COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) o una de sus variantes.

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx::InternalRelease

Disminuye el recuento de referencias de un objeto no agregado en 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones que no son de depuración y de depuración, esta función devuelve un valor que puede ser útil para diagnósticos o pruebas. El valor exacto devuelto depende de muchos factores, como el sistema operativo utilizado, y puede ser, o no, el recuento de referencias.

### <a name="remarks"></a>Observaciones

Si el modelo de subprocesos es multiproceso, `InterlockedDecrement` se usa para evitar que más de un subproceso cambie el recuento de referencias al mismo tiempo.

## <a name="ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx::Lock

Si el modelo de subprocesos es multiproceso, este método llama a la función de API de Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), que espera hasta que el subproceso pueda tomar la propiedad del objeto de sección crítica obtenido a través de un miembro de datos privados.

```
void Lock();
```

### <a name="remarks"></a>Observaciones

Cuando el código protegido termina de ejecutarse, el subproceso debe llamar `Unlock` para liberar la propiedad de la sección crítica.

Si el modelo de subprocesos es de un solo subproceso, este método no hace nada.

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a>CComObjectRootEx::m_dwRef

Parte de una unión que tiene acceso a cuatro bytes de memoria.

```
long m_dwRef;
```

### <a name="remarks"></a>Observaciones

Con `m_pOuterUnknown`, parte de una unión:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si el objeto no se agrega, `AddRef` el `Release` recuento `m_dwRef`de referencias al que se tiene acceso y se almacena en . Si se agrega el objeto, el puntero al desconocido externo se almacena en [m_pOuterUnknown](#m_pouterunknown).

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown

Parte de una unión que tiene acceso a cuatro bytes de memoria.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Observaciones

Con `m_dwRef`, parte de una unión:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si el objeto se agrega, el puntero al `m_pOuterUnknown`desconocido externo se almacena en . Si el objeto no se agrega, `AddRef` el `Release` recuento de referencias al que se tiene acceso y se almacena en [m_dwRef](#m_dwref).

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx::ObjectMain

Para cada clase enumerada en el mapa de objetos, se llama a esta función una vez cuando se inicializa el módulo y otra vez cuando se termina.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parámetros

*bStarting*<br/>
[fuera] El valor es TRUE si se inicializa la clase; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El valor del parámetro *bStarting* indica si el módulo se está inicializando o terminando. La implementación `ObjectMain` predeterminada de no hace nada, pero puede invalidar esta función en la clase para inicializar o limpiar los recursos que desea asignar para la clase. Tenga `ObjectMain` en cuenta que se llama antes de que se soliciten instancias de la clase.

`ObjectMain`se llama desde el punto de entrada del archivo DLL, por lo que el tipo de operación que puede realizar la función de punto de entrada está restringido. Para obtener más información sobre estas restricciones, vea DLL y Comportamiento de la biblioteca en tiempo de ejecución de [Visual C++](../../build/run-time-library-behavior.md) y [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootEx::OuterAddRef

Incrementa el recuento de referencias del desconocido externo de una agregación.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos y pruebas.

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface

Recupera un puntero indirecto a la interfaz solicitada.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] GUID de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz especificado en *iid*, o NULL si la agregación no admite la interfaz.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx::OuterRelease

Disminuye el recuento de referencias del desconocido externo de una agregación.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones que no son de depuración, siempre devuelve 0. En compilaciones de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas.

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx::Unlock

Si el modelo de subprocesos es multiproceso, este método llama a la función de API de Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), que libera la propiedad del objeto de sección crítica obtenido a través de un miembro de datos privados.

```
void Unlock();
```

### <a name="remarks"></a>Observaciones

Para obtener la propiedad, `Lock`el subproceso debe llamar a . Cada llamada `Lock` requiere una llamada `Unlock` correspondiente para liberar la propiedad de la sección crítica.

Si el modelo de subprocesos es de un solo subproceso, este método no hace nada.

## <a name="see-also"></a>Consulte también

[Clase CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Clase CComObject](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (Clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
