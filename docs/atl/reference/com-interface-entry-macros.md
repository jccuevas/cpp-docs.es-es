---
title: Macros de entrada de interfaz COM
ms.date: 03/28/2017
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: bb7498f639f463290a4a6593ef7c0fbac09b539b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326676"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY Macros

Estas macros introducen las interfaces de un objeto en `QueryInterface`su mapa COM para que se pueda acceder a ellas mediante . El orden de las entradas en el mapa COM es que las `QueryInterface`interfaces de orden se comprobarán para un IID coincidente durante .

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Ingresa las interfaces en la correspondencia de la interfaz COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Utilice esta macro para desambiguar dos ramas de herencia.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Utilice esta macro para entrar en la interfaz en el mapa COM y especificar su IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Igual que [COM_INTERFACE_ENTRY2](#com_interface_entry2), excepto que puede especificar un IID diferente.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Cuando se consulta la interfaz identificada `COM_INTERFACE_ENTRY_AGGREGATE` por `punk` *iid,* reenvía a .|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto si *punk* es NULL, crea automáticamente el agregado descrito por el *clsid*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Igual que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), excepto que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*y, si *punk* es NULL, crear automáticamente el agregado descrito por el *clsid*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Hace que el programa llame a [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) cuando se consulta la interfaz especificada.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Guarda los datos específicos de la interfaz para cada instancia.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Expone sus interfaces de desmontaje.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Procesa el mapa COM de la clase base cuando el procesamiento alcanza esta entrada en el mapa COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Un mecanismo general para enlazar a `QueryInterface` la lógica de ATL.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Igual que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), excepto que la consulta de cualquier IID da como resultado una llamada a *func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Devuelve E_NOINTERFACE y finaliza el procesamiento de mapas COM cuando se consulta la interfaz especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

Ingresa las interfaces en la correspondencia de la interfaz COM.

### <a name="syntax"></a>Sintaxis

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre de una interfaz de la que deriva el objeto de clase directamente.

### <a name="remarks"></a>Observaciones

Normalmente, este es el tipo de entrada que se utiliza con más frecuencia.

### <a name="example"></a>Ejemplo

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

Utilice esta macro para desambiguar dos ramas de herencia.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre de una interfaz que desea exponer desde el objeto.

*x2*<br/>
[en] El nombre de la rama de herencia desde la que se expone *x.*

### <a name="remarks"></a>Observaciones

Por ejemplo, si deriva el objeto de clase `IDispatch` de dos `IDispatch` interfaces duales, expone mediante COM_INTERFACE_ENTRY2 ya que se puede obtener de cualquiera de las interfaces.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

Utilice esta macro para entrar en la interfaz en el mapa COM y especificar su IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] Guid de la interfaz expuesta.

*X*<br/>
[en] El nombre de la clase cuya vtable se expondrá como la interfaz identificada por *iid*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Igual que [COM_INTERFACE_ENTRY2](#com_interface_entry2), excepto que puede especificar un IID diferente.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] El GUID que está especificando para la interfaz.

*X*<br/>
[en] El nombre de una interfaz de la que deriva el objeto de clase directamente.

*x2*<br/>
[en] El nombre de una segunda interfaz de la que deriva el objeto de clase directamente.

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Cuando se consulta la interfaz identificada por *iid,* COM_INTERFACE_ENTRY_AGGREGATE reenvía al *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] El GUID de la interfaz consultada.

*Punk*<br/>
[en] El nombre `IUnknown` de un puntero.

### <a name="remarks"></a>Observaciones

Se supone que el parámetro *punk* apunta a la incógnita interna de un agregado o a NULL, en cuyo caso se omite la entrada. Normalmente, se `CoCreate` agregaría `FinalConstruct`en .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] El nombre `IUnknown` de un puntero.

### <a name="remarks"></a>Observaciones

Si se produce un error en la consulta de interfaz, el procesamiento de la asignación COM continúa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto si *punk* es NULL, crea automáticamente el agregado descrito por el *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] El GUID de la interfaz consultada.

*Punk*<br/>
[en] El nombre `IUnknown` de un puntero. Debe ser un miembro de la clase que contiene el mapa COM.

*clsid*<br/>
[en] Identificador del agregado que se creará si *punk* es NULL.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Igual que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), excepto que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*y, si *punk* es NULL, crear automáticamente el agregado descrito por el *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] El nombre `IUnknown` de un puntero. Debe ser un miembro de la clase que contiene el mapa COM.

*clsid*<br/>
[en] Identificador del agregado que se creará si *punk* es NULL.

### <a name="remarks"></a>Observaciones

Si se produce un error en la consulta de interfaz, el procesamiento de la asignación COM continúa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Hace que el programa llame a [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) cuando se consulta la interfaz especificada.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] Texto utilizado para construir el identificador de interfaz.

### <a name="remarks"></a>Observaciones

El IID de la interfaz *x* se `IID_`construirá añadiendo x a . Por ejemplo, *x* si `IPersistStorage`x es , `IID_IPersistStorage`el IID será .

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Guarda los datos específicos de la interfaz para cada instancia.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] El GUID de la interfaz de desmontaje.

*X*<br/>
[en] El nombre de la clase que implementa la interfaz.

*Punk*<br/>
[en] El nombre `IUnknown` de un puntero. Debe ser un miembro de la clase que contiene el mapa COM. Debe inicializarse en NULL en el constructor del objeto de clase.

### <a name="remarks"></a>Observaciones

Si no se utiliza la interfaz, esto reduce el tamaño general de la instancia del objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Expone sus interfaces de desmontaje.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] El GUID de la interfaz de desmontaje.

*X*<br/>
[en] El nombre de la clase que implementa la interfaz.

### <a name="remarks"></a>Observaciones

Una interfaz de desmontaje se implementa como un objeto independiente que se crea una instancia cada vez que se consulta la interfaz que representa. Normalmente, la interfaz se crea como un desmontaje si la interfaz se utiliza raramente, ya que esto guarda un puntero vtable en cada instancia del objeto principal. El desmontaje se elimina cuando su recuento de referencias se convierte en cero. La clase que implementa el desmontaje debe derivarse `CComTearOffObjectBase` de y tener su propio mapa COM.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Procesa el mapa COM de la clase base cuando el procesamiento alcanza esta entrada en el mapa COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parámetros

*Classname*<br/>
[en] Una clase base del objeto actual.

### <a name="remarks"></a>Observaciones

Por ejemplo, en el código siguiente:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Tenga en cuenta que la primera entrada en el mapa COM debe ser una interfaz en el objeto que contiene el mapa COM. Por lo tanto, no puede iniciar las entradas de mapa COM con COM_INTERFACE_ENTRY_CHAIN, lo que hace que el mapa COM de un objeto diferente se busque en el punto donde **COM_INTERFACE_ENTRY_CHAIN(**`COtherObject`**)** aparece en el mapa COM del objeto. Si desea buscar primero en el mapa COM de `IUnknown` otro objeto, agregue una entrada de interfaz para el mapa COM y, a continuación, encadene el mapa COM del otro objeto. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Un mecanismo general para enlazar a `QueryInterface` la lógica de ATL.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] Guid de la interfaz expuesta.

*dw*<br/>
[en] Un parámetro pasado a través de la *func*.

*Func*<br/>
[en] El puntero de función que devolverá *iid*.

### <a name="remarks"></a>Observaciones

Si *iid* coincide con el IID de la interfaz consultada, se llama a la función especificada por *func.* La declaración de la función debe ser:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Cuando se llama `pv` a la función, apunta al objeto de clase. El parámetro *riid* hace referencia a `ppv` la interfaz que se está consultando, es el puntero a la ubicación donde la función debe almacenar el puntero a la interfaz y *dw* es el parámetro especificado en la entrada. La función \* `ppv` debe establecerse en NULL y devolver E_NOINTERFACE o S_FALSE si decide no devolver una interfaz. Con E_NOINTERFACE, finaliza el procesamiento de mapas COM. Con S_FALSE, el procesamiento de mapas COM continúa, aunque no se devolvió ningún puntero de interfaz. Si la función devuelve un puntero de interfaz, debe devolver S_OK.

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Igual que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), excepto que la consulta de cualquier IID da como resultado una llamada a *func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parámetros

*dw*<br/>
[en] Un parámetro pasado a través de la *func*.

*Func*<br/>
[en] Función a la que se llama cuando se procesa esta entrada en el mapa COM.

### <a name="remarks"></a>Observaciones

Cualquier error hará que el procesamiento continúe en el mapa COM. Si la función devuelve un puntero de interfaz, debe devolver S_OK.

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Devuelve E_NOINTERFACE y finaliza el procesamiento de mapas COM cuando se consulta la interfaz especificada.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] Texto utilizado para construir el identificador de interfaz.

### <a name="remarks"></a>Observaciones

Puede utilizar esta macro para evitar que se utilice una interfaz en un caso determinado. Por ejemplo, puede insertar esta macro en el mapa COM justo antes de COM_INTERFACE_ENTRY_AGGREGATE_BLIND para evitar que una consulta para la interfaz se reenvíe a la incógnita interna del agregado.

El IID de la interfaz *x* se `IID_`construirá añadiendo x a . Por ejemplo, *x* si `IPersistStorage`x es , `IID_IPersistStorage`el IID será .
