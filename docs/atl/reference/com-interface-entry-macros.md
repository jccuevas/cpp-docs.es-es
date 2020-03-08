---
title: Macros de entrada de la interfaz COM
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
ms.openlocfilehash: 1e1674bad1164e640939d430a860beac7a6e4208
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855671"
---
# <a name="com_interface_entry-macros"></a>Macros COM_INTERFACE_ENTRY

Estas macros escriben las interfaces de un objeto en su asignación COM para que `QueryInterface`puedan tener acceso a ellas. El orden de las entradas en el mapa COM es el orden en el que se comprobarán las interfaces de un IID coincidente durante la `QueryInterface`.

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Escribe interfaces en el mapa de interfaz COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Utilice esta macro para eliminar la ambigüedad de dos bifurcaciones de herencia.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Utilice esta macro para especificar la interfaz en el mapa COM y especificar su IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Igual que [COM_INTERFACE_ENTRY2](#com_interface_entry2), salvo que se puede especificar un IID diferente.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Cuando se consulta la interfaz identificada por *IID* , `COM_INTERFACE_ENTRY_AGGREGATE` reenvía a `punk`.|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), salvo que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto si *punk* es null, crea automáticamente el agregado descrito por el *CLSID*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Igual que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), salvo que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*, y si *punk* es null, se crea automáticamente el agregado descrito por el *CLSID*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Hace que el programa llame a [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) cuando se consulta la interfaz especificada.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Guarda los datos específicos de la interfaz para cada instancia.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Expone las interfaces de recorte.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Procesa el mapa COM de la clase base cuando el procesamiento alcanza esta entrada en el mapa COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Mecanismo general para enlazar con la lógica de `QueryInterface` de ATL.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Igual que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), salvo que la consulta de cualquier IID da como resultado una llamada a *FUNC*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Devuelve E_NOINTERFACE y finaliza el procesamiento del mapa COM cuando se consulta la interfaz especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

## <a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

Escribe interfaces en el mapa de interfaz COM.

### <a name="syntax"></a>Sintaxis

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre de una interfaz de la que se deriva directamente el objeto de clase.

### <a name="remarks"></a>Observaciones

Normalmente, este es el tipo de entrada que se usa con más frecuencia.

### <a name="example"></a>Ejemplo

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

Utilice esta macro para eliminar la ambigüedad de dos bifurcaciones de herencia.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre de una interfaz que se desea exponer del objeto.

*RCA*<br/>
de Nombre de la bifurcación de herencia desde la que se expone *x* .

### <a name="remarks"></a>Observaciones

Por ejemplo, si se deriva el objeto de clase de dos interfaces duales, se expone `IDispatch` mediante COM_INTERFACE_ENTRY2 dado que `IDispatch` puede obtenerse a partir de cualquiera de las interfaces.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

Utilice esta macro para especificar la interfaz en el mapa COM y especificar su IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID de la interfaz expuesta.

*x*<br/>
de El nombre de la clase cuya tabla vtable se expondrá como la interfaz identificada por *IID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Igual que [COM_INTERFACE_ENTRY2](#com_interface_entry2), salvo que se puede especificar un IID diferente.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID que se especifica para la interfaz.

*x*<br/>
de Nombre de una interfaz de la que se deriva directamente el objeto de clase.

*RCA*<br/>
de Nombre de una segunda interfaz de la que se deriva directamente el objeto de clase.

##  <a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Cuando se consulta la interfaz identificada por *IID* , COM_INTERFACE_ENTRY_AGGREGATE reenvía a *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID de la interfaz consultada para.

*punk*<br/>
de Nombre de un puntero `IUnknown`.

### <a name="remarks"></a>Observaciones

Se supone que el parámetro *punk* apunta al desconocido interno de un agregado o a NULL, en cuyo caso se omite la entrada. Normalmente, se `CoCreate` el agregado en `FinalConstruct`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), salvo que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parámetros

*punk*<br/>
de Nombre de un puntero `IUnknown`.

### <a name="remarks"></a>Observaciones

Si se produce un error en la consulta de la interfaz, el procesamiento del mapa COM continúa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Igual que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), excepto si *punk* es null, crea automáticamente el agregado descrito por el *CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID de la interfaz consultada para.

*punk*<br/>
de Nombre de un puntero `IUnknown`. Debe ser un miembro de la clase que contiene el mapa COM.

*CLSID*<br/>
de Identificador del agregado que se creará si *punk* es NULL.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Igual que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), salvo que la consulta de cualquier IID da como resultado el reenvío de la consulta a *punk*, y si *punk* es null, se crea automáticamente el agregado descrito por el *CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parámetros

*punk*<br/>
de Nombre de un puntero `IUnknown`. Debe ser un miembro de la clase que contiene el mapa COM.

*CLSID*<br/>
de Identificador del agregado que se creará si *punk* es NULL.

### <a name="remarks"></a>Observaciones

Si se produce un error en la consulta de la interfaz, el procesamiento del mapa COM continúa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Hace que el programa llame a [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) cuando se consulta la interfaz especificada.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Texto que se usa para construir el identificador de interfaz.

### <a name="remarks"></a>Observaciones

El IID de la interfaz se construirá anexando *x* a `IID_`. Por ejemplo, si *x* es `IPersistStorage`, el IID se `IID_IPersistStorage`.

##  <a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Guarda los datos específicos de la interfaz para cada instancia.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID de la interfaz de recorte.

*x*<br/>
de Nombre de la clase que implementa la interfaz.

*punk*<br/>
de Nombre de un puntero `IUnknown`. Debe ser un miembro de la clase que contiene el mapa COM. Se debe inicializar en NULL en el constructor del objeto de clase.

### <a name="remarks"></a>Observaciones

Si no se utiliza la interfaz, se reduce el tamaño total de la instancia del objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Expone las interfaces de recorte.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID de la interfaz de recorte.

*x*<br/>
de Nombre de la clase que implementa la interfaz.

### <a name="remarks"></a>Observaciones

Una interfaz de recorte se implementa como un objeto independiente al que se crean instancias cada vez que se consulta la interfaz que representa. Normalmente, la interfaz se compila como un recorte si la interfaz se usa con poca frecuencia, ya que esto guarda un puntero vtable en cada instancia del objeto principal. El recorte se elimina cuando su recuento de referencias se convierte en cero. La clase que implementa el recorte debe derivarse de `CComTearOffObjectBase` y tener su propio mapa COM.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Procesa el mapa COM de la clase base cuando el procesamiento alcanza esta entrada en el mapa COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parámetros

*classname*<br/>
de Clase base del objeto actual.

### <a name="remarks"></a>Observaciones

Por ejemplo, en el código siguiente:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Tenga en cuenta que la primera entrada del mapa COM debe ser una interfaz del objeto que contiene el mapa COM. Por lo tanto, no se pueden iniciar las entradas de asignación COM con COM_INTERFACE_ENTRY_CHAIN, lo que hace que se busque en el mapa COM de un objeto diferente en el punto en el que aparece **COM_INTERFACE_ENTRY_CHAIN (** `COtherObject` **)** en el mapa com del objeto. Si desea buscar primero en el mapa COM de otro objeto, agregue una entrada de interfaz para `IUnknown` al mapa COM y, a continuación, Encadene el mapa COM del otro objeto. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Mecanismo general para enlazar con la lógica de `QueryInterface` de ATL.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID de la interfaz expuesta.

*dw*<br/>
de Un parámetro pasado a la función *FUNC*.

*func*<br/>
de Puntero de función que devolverá *IID*.

### <a name="remarks"></a>Observaciones

Si *IID* coincide con el IID de la interfaz consultada para, se llama a la función especificada por *FUNC* . La declaración de la función debe ser:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Cuando se llama a la función, `pv` apunta a su objeto de clase. El parámetro *riid* hace referencia a la interfaz que se consulta, `ppv` es el puntero a la ubicación donde la función debe almacenar el puntero en la interfaz y *DW* es el parámetro especificado en la entrada. La función debe establecer \* `ppv` en NULL y devolver E_NOINTERFACE o S_FALSE si decide no devolver una interfaz. Con E_NOINTERFACE, finaliza el procesamiento del mapa COM. Con S_FALSE, el procesamiento de mapas COM continúa, aunque no se devolviera ningún puntero de interfaz. Si la función devuelve un puntero de interfaz, debe devolver S_OK.

##  <a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Igual que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), salvo que la consulta de cualquier IID da como resultado una llamada a *FUNC*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parámetros

*dw*<br/>
de Un parámetro pasado a la función *FUNC*.

*func*<br/>
de Función a la que se llama cuando se procesa esta entrada en el mapa COM.

### <a name="remarks"></a>Observaciones

Cualquier error hará que el procesamiento continúe en el mapa COM. Si la función devuelve un puntero de interfaz, debe devolver S_OK.

##  <a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Devuelve E_NOINTERFACE y finaliza el procesamiento del mapa COM cuando se consulta la interfaz especificada.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Texto que se usa para construir el identificador de interfaz.

### <a name="remarks"></a>Observaciones

Puede usar esta macro para evitar que una interfaz se utilice en un caso determinado. Por ejemplo, puede insertar esta macro en el mapa COM justo antes de COM_INTERFACE_ENTRY_AGGREGATE_BLIND para evitar que una consulta de la interfaz se reenvíe al desconocido interno del agregado.

El IID de la interfaz se construirá anexando *x* a `IID_`. Por ejemplo, si *x* es `IPersistStorage`, el IID se `IID_IPersistStorage`.
