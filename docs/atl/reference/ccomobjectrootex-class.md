---
title: CComObjectRootEx (clase)
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
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497051"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx (clase)

Esta clase proporciona métodos para controlar la administración del recuento de referencias de objetos para los objetos no agregados y los agregados.

## <a name="syntax"></a>Sintaxis

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parámetros

*ThreadModel*<br/>
Clase cuyos métodos implementan el modelo de subprocesos deseado. Puede elegir explícitamente el modelo de subprocesos estableciendo *ThreadModel* en [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Puede aceptar el modelo de subprocesos predeterminado del servidor estableciendo *ThreadModel* en [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) o [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Constructor.|
|[InternalAddRef](#internaladdref)|Incrementa el recuento de referencias para un objeto no agregado.|
|[InternalRelease](#internalrelease)|Disminuye el recuento de referencias para un objeto no agregado.|
|[Bloquea](#lock)|Si el modelo de subprocesos es multiproceso, obtiene la propiedad de un objeto de sección crítica.|
|[Pulsa](#unlock)|Si el modelo de subprocesos es multiproceso, libera la propiedad de un objeto de sección crítica.|

### <a name="ccomobjectrootbase-methods"></a>Métodos CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Invalide en la clase para realizar cualquier inicialización que requiera el objeto.|
|[FinalRelease](#finalrelease)|Invalide en la clase para realizar cualquier limpieza que necesite el objeto.|
|[OuterAddRef](#outeraddref)|Incrementa el recuento de referencias de un objeto agregado.|
|[OuterQueryInterface](#outerqueryinterface)|Delega en el exterior `IUnknown` de un objeto agregado.|
|[OuterRelease](#outerrelease)|Disminuye el recuento de referencias para un objeto agregado.|

### <a name="static-functions"></a>Funciones estáticas

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Delega en `IUnknown` de un objeto no agregado.|
|[ObjectMain](#objectmain)|Se llama durante la inicialización y terminación del módulo para las clases derivadas que se enumeran en el mapa de objetos.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_dwRef](#m_dwref)|Con `m_pOuterUnknown`, parte de una Unión. Se utiliza cuando el objeto no se agrega para contener el recuento de `AddRef` referencias `Release`de y.|
|[m_pOuterUnknown](#m_pouterunknown)|Con `m_dwRef`, parte de una Unión. Se utiliza cuando el objeto se agrega para que contenga un puntero al desconocido externo.|

## <a name="remarks"></a>Comentarios

`CComObjectRootEx`controla la administración del recuento de referencias de objeto para los objetos no agregados y los agregados. Contiene el recuento de referencias de objeto si el objeto no se agrega y mantiene el puntero al objeto desconocido externo si se agrega el objeto. En el caso de los `CComObjectRootEx` objetos agregados, los métodos se pueden usar para controlar el error del objeto interno que se va a construir y para proteger el objeto externo de la eliminación cuando se liberan interfaces internas o se elimina el objeto interno.

Una clase que implementa un servidor com debe heredar de `CComObjectRootEx` o [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Si la definición de clase especifica la macro [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) , ATL crea una instancia `CComPolyObject<CYourClass>` de `IClassFactory::CreateInstance` cuando se llama a. Durante la creación, se comprueba el valor de la desconocido externa. Si es null, `IUnknown` se implementa para un objeto no agregado. Si el desconocido externo no es null, `IUnknown` se implementa para un objeto agregado.

Si la clase no especifica la macro DECLARE_POLY_AGGREGATABLE, ATL crea una instancia de `CAggComObject<CYourClass>` para los objetos agregados o una instancia de `CComObject<CYourClass>` para los objetos no agregados.

La ventaja de usar `CComPolyObject` es que evita `CComAggObject` tener y `CComObject` en el módulo para controlar los casos agregados y no agregados. Un solo `CComPolyObject` objeto controla ambos casos. Por lo tanto, solo existe una copia de vtable y una copia de las funciones en el módulo. Si su vtable es grande, esto puede reducir considerablemente el tamaño del módulo. Sin embargo, si la tabla vtable es pequeña `CComPolyObject` , el uso de puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no `CComAggObject` agregado `CComObject`, como son y.

Si el objeto se agrega, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) se implementa mediante `CComAggObject` o. `CComPolyObject` Estas `QueryInterface`clases delegan `AddRef` `CComObjectRootEx` `OuterRelease` las llamadas a `OuterAddRef`, y a ,,yparareenviaraldesconocidoexterno.`OuterQueryInterface` `Release` Normalmente, invalide `CComObjectRootEx::FinalConstruct` en la clase para crear los objetos agregados e invalide `CComObjectRootEx::FinalRelease` para liberar los objetos agregados.

Si el objeto no se agrega, `IUnknown` se implementa mediante `CComObject` o `CComPolyObject`. En este caso, las llamadas `QueryInterface`a `AddRef`, y `Release` se delegan a `CComObjectRootEx` `InternalQueryInterface`, `InternalAddRef`y `InternalRelease` para realizar las operaciones reales.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx

El constructor inicializa el recuento de referencias en 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

Puede invalidar este método en la clase derivada para realizar cualquier inicialización necesaria para el objeto.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Devuelva S_OK si se ejecuta correctamente o uno de los valores de error estándar de HRESULT.

### <a name="remarks"></a>Comentarios

De forma predeterminada `CComObjectRootEx::FinalConstruct` , simplemente Devuelve S_OK.

Hay ventajas en la realización de la `FinalConstruct` inicialización en lugar del constructor de la clase:

- No se puede devolver un código de estado desde un constructor, pero se puede devolver un valor HRESULT `FinalConstruct`mediante el valor devuelto de. Cuando se crean objetos de la clase mediante el generador de clases estándar proporcionado por ATL, este valor devuelto se propaga de vuelta al cliente COM, lo que le permite proporcionarle información detallada del error.

- No se puede llamar a funciones virtuales a través del mecanismo de función virtual desde el constructor de una clase. La llamada a una función virtual desde el constructor de una clase da lugar a una llamada resuelta estáticamente a la función tal y como se define en ese punto de la jerarquía de herencia. Las llamadas a funciones virtuales puras generan errores del enlazador.

   La clase no es la clase derivada más en la jerarquía de herencia, sino que se basa en una clase derivada proporcionada por ATL para proporcionar parte de su funcionalidad. Existe la posibilidad de que la inicialización tenga que usar las características proporcionadas por esa clase (esto es realmente cierto cuando los objetos de la clase necesitan agregar otros objetos), pero el constructor de la clase no tiene ninguna manera de tener acceso a esas características. El código de construcción de la clase se ejecuta antes de que la clase más derivada se construya por completo.

   Sin embargo `FinalConstruct` , se llama a inmediatamente después de que la clase más derivada esté totalmente construida, lo que le permite llamar a funciones virtuales y usar la implementación del recuento de referencias que proporciona ATL.

### <a name="example"></a>Ejemplo

Normalmente, Invalide este método en la clase `CComObjectRootEx` derivada de para crear objetos agregados. Por ejemplo:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Si se produce un error en la construcción, puede devolver un error. También puede usar la macro [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) para evitar que se elimine el objeto externo si, durante la creación, el objeto agregado interno incrementa el recuento de referencias y, a continuación, disminuye el recuento a 0.

Esta es una forma típica de crear un agregado:

- Agregue un `IUnknown` puntero al objeto de clase e Inicialícelo en null en el constructor.

- Invalide `FinalConstruct` para crear el agregado.

- Use el `IUnknown` puntero que definió como parámetro para la macro [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) .

- Invalide `FinalRelease` para `IUnknown` liberar el puntero.

##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease

Puede invalidar este método en la clase derivada para realizar cualquier limpieza necesaria para el objeto.

```
void FinalRelease();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada `CComObjectRootEx::FinalRelease` , no hace nada.

Es preferible `FinalRelease` realizar la limpieza en para agregar código al destructor de la clase, ya que el objeto todavía está totalmente construido en el punto `FinalRelease` en el que se llama a. Esto le permite tener acceso de forma segura a los métodos proporcionados por la clase más derivada. Esto es especialmente importante para liberar cualquier objeto agregado antes de la eliminación.

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

Incrementa el recuento de referencias de un objeto no agregado en 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para los diagnósticos y las pruebas.

### <a name="remarks"></a>Comentarios

Si el modelo de subprocesos es multiproceso, `InterlockedIncrement` se usa para evitar que más de un subproceso cambie el recuento de referencias al mismo tiempo.

##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface

Recupera un puntero a la interfaz solicitada.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*pThis*<br/>
de Un puntero al objeto que contiene el mapa COM de las interfaces expuestas a `QueryInterface`.

*pEntries*<br/>
de Puntero a la `_ATL_INTMAP_ENTRY` estructura que tiene acceso a un mapa de interfaces disponibles.

*iid*<br/>
de GUID de la interfaz que se solicita.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz especificado en *IID*o null si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

`InternalQueryInterface` solo administra interfaces de la tabla de asignación COM. Si se agrega el objeto, `InternalQueryInterface` no delega en el desconocido externo. Puede especificar interfaces en la tabla de asignación COM con la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) o una de sus variantes.

##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease

Disminuye el recuento de referencias de un objeto no agregado en 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones que no son de depuración y de depuración, esta función devuelve un valor que puede ser útil para diagnósticos o pruebas. El valor exacto devuelto depende de muchos factores, como el sistema operativo utilizado, y puede o no ser el recuento de referencias.

### <a name="remarks"></a>Comentarios

Si el modelo de subprocesos es multiproceso, `InterlockedDecrement` se usa para evitar que más de un subproceso cambie el recuento de referencias al mismo tiempo.

##  <a name="lock"></a>  CComObjectRootEx::Lock

Si el modelo de subprocesos es multiproceso, este método llama a la función de la API de Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), que espera hasta que el subproceso pueda asumir la propiedad del objeto de sección crítica obtenido a través de un miembro de datos privado.

```
void Lock();
```

### <a name="remarks"></a>Comentarios

Cuando el código protegido termina de ejecutarse, el subproceso `Unlock` debe llamar a para liberar la propiedad de la sección crítica.

Si el modelo de subproceso es de subproceso único, este método no hace nada.

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

Parte de una Unión que tiene acceso a cuatro bytes de memoria.

```
long m_dwRef;
```

### <a name="remarks"></a>Comentarios

Con `m_pOuterUnknown`, parte de una Unión:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si no se agrega el objeto, el recuento de referencias al que `AddRef` tiene `Release` acceso y se `m_dwRef`almacena en. Si se agrega el objeto, el puntero al desconocido externo se almacena en [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown

Parte de una Unión que tiene acceso a cuatro bytes de memoria.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Comentarios

Con `m_dwRef`, parte de una Unión:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Si se agrega el objeto, el puntero al desconocido externo se almacena en `m_pOuterUnknown`. Si no se agrega el objeto, el recuento de referencias al que `AddRef` tiene `Release` acceso y se almacena en [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain

Para cada clase enumerada en el mapa de objetos, esta función se llama una vez cuando se inicializa el módulo y de nuevo cuando se termina.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parámetros

*bStarting*<br/>
enuncia El valor es TRUE si se está inicializando la clase; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El valor del parámetro *bStarting* indica si el módulo se está inicializando o finalizando. La implementación predeterminada de `ObjectMain` no hace nada, pero puede invalidar esta función en la clase para inicializar o limpiar los recursos que desea asignar para la clase. Tenga en `ObjectMain` cuenta que se llama a este método antes de que se soliciten las instancias de la clase.

`ObjectMain`se llama a desde el punto de entrada de la DLL, por lo que el tipo de operación que puede realizar la función de punto de entrada está restringido. Para obtener más información sobre estas restricciones, vea [archivos dll C++ y comportamiento de la biblioteca en tiempo de ejecución de Visual](../../build/run-time-library-behavior.md) y [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

Incrementa el recuento de referencias de la desconocida externa de una agregación.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para los diagnósticos y las pruebas.

##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface

Recupera un puntero indirecto a la interfaz solicitada.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
de GUID de la interfaz que se solicita.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz especificado en *IID*, o null si la agregación no admite la interfaz.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease

Disminuye el recuento de referencias de la desconocida externa de una agregación.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones que no son de depuración, siempre devuelve 0. En compilaciones de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas.

##  <a name="unlock"></a>  CComObjectRootEx::Unlock

Si el modelo de subprocesos es multiproceso, este método llama a la función de la API [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)de Win32, que libera la propiedad del objeto de sección crítica obtenido a través de un miembro de datos privado.

```
void Unlock();
```

### <a name="remarks"></a>Comentarios

Para obtener la propiedad, el subproceso `Lock`debe llamar a. Cada llamada a `Lock` requiere una llamada correspondiente a `Unlock` para liberar la propiedad de la sección crítica.

Si el modelo de subproceso es de subproceso único, este método no hace nada.

## <a name="see-also"></a>Vea también

[CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject (clase)](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
