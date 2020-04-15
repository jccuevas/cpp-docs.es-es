---
title: CMemoryState (estructura)
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 8f49a9faf70673c62167deeaa1bef33e4882378f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369996"
---
# <a name="cmemorystate-structure"></a>CMemoryState (estructura)

Proporciona una manera cómoda de detectar fugas de memoria en el programa.

## <a name="syntax"></a>Sintaxis

```
struct CMemoryState
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Construye una estructura similar a una clase que controla los puntos de comprobación de memoria.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMemoryState::Checkpoint](#checkpoint)|Obtiene una instantánea (punto de control) del estado de memoria actual.|
|[CMemoryState::Difference](#difference)|Calcula la diferencia entre dos `CMemoryState`objetos de tipo .|
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Vuelca un resumen de todos los objetos asignados actualmente desde un punto de comprobación anterior.|
|[CMemoryState::DumpStatistics](#dumpstatistics)|Imprime estadísticas de asignación de memoria para un `CMemoryState` objeto.|

## <a name="remarks"></a>Observaciones

`CMemoryState`es una estructura y no tiene una clase base.

Una "pérdida de memoria" se produce cuando la memoria de un objeto se asigna en el montón pero no se desasigna cuando ya no es necesaria. Estas pérdidas de memoria pueden eventualmente conducir a errores de memoria insuficiente. Hay varias maneras de asignar y desasignar memoria en el programa:

- Uso `malloc` /  `free` de la familia de funciones de la biblioteca en tiempo de ejecución.

- Mediante `LocalAlloc` /  `LocalFree` las funciones de `GlobalAlloc` /  `GlobalFree`administración de memoria de la API de Windows y .

- Mediante los operadores **new** y **delete** de C+++ .

Los `CMemoryState` diagnósticos solo ayudan a detectar las pérdidas de memoria causadas cuando la memoria asignada mediante el **operador new** no se desasigna mediante **delete**. Los otros dos grupos de funciones de administración de memoria son para programas que no son C++, y no se recomienda mezclarlos con **new** y **delete** en el mismo programa. Se proporciona una macro adicional, DEBUG_NEW, para reemplazar el **operador nuevo** cuando se necesita el seguimiento de archivos y números de línea de las asignaciones de memoria. DEBUG_NEW se utiliza siempre que se utiliza normalmente el **operador new.**

Al igual que con `CMemoryState` otros diagnósticos, los diagnósticos solo están disponibles en las versiones de depuración del programa. Una versión de depuración debe tener definida la _DEBUG constante.

Si sospecha que el programa tiene una `Checkpoint`pérdida `Difference`de `DumpStatistics` memoria, puede utilizar las funciones , , y para descubrir la diferencia entre el estado de memoria (objetos asignados) en dos puntos diferentes en la ejecución del programa. Esta información puede ser útil para determinar si una función está limpiando todos los objetos que asigna.

Si simplemente saber dónde se produce el desequilibrio en la asignación y desasignación no proporciona suficiente información, puede utilizar la `DumpAllObjectsSince` función para volcar todos los objetos asignados desde la llamada anterior a `Checkpoint`. Este volcado muestra el orden de asignación, el archivo de origen y la línea donde se asignó el objeto (si utiliza DEBUG_NEW para la asignación) y la derivación del objeto, su dirección y su tamaño. `DumpAllObjectsSince`también llama a `Dump` la función de cada objeto para proporcionar información sobre su estado actual.

Para obtener más información `CMemoryState` acerca de cómo usar y otros diagnósticos, vea [Depurar aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Las declaraciones de `CMemoryState` objetos de tipo y `#if defined(_DEBUG)/#endif` llamadas a funciones miembro deben estar entre corchetes por directivas. Esto hace que los diagnósticos de memoria se incluyan solo en las compilaciones de depuración del programa.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CMemoryState`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState::Checkpoint

Toma un resumen de instantánea de `CMemoryState` memoria y la almacena en este objeto.

```
void Checkpoint();
```

### <a name="remarks"></a>Observaciones

Las `CMemoryState` funciones miembro [Difference](#difference) y [DumpAllObjectsSince](#dumpallobjectssince) utilizan estos datos de instantánea.

### <a name="example"></a>Ejemplo

  Vea el ejemplo para el [CMemoryState](#cmemorystate) constructor.

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState

Construye un `CMemoryState` objeto vacío que debe rellenarse mediante la función miembro [Checkpoint](#checkpoint) o [Difference.](#difference)

```
CMemoryState();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::Difference

Compara dos `CMemoryState` objetos y, a `CMemoryState` continuación, almacena la diferencia en este objeto.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parámetros

*oldState*<br/>
El estado de memoria `CMemoryState` inicial definido por un punto de comprobación.

*newState*<br/>
El nuevo estado de `CMemoryState` memoria definido por un punto de comprobación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los dos estados de memoria son diferentes; de lo contrario 0.

### <a name="remarks"></a>Observaciones

[Se](#checkpoint) debe haber llamado a Checkpoint para cada uno de los dos parámetros de estado de memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo para el [CMemoryState](#cmemorystate) constructor.

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince

Llama `Dump` a la función para todos `CObject` los objetos de un tipo derivado de la `CMemoryState` clase que se asignaron (y todavía se asignan) desde la última llamada [Checkpoint](#checkpoint) para este objeto.

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Observaciones

Llamar `DumpAllObjectsSince` con un `CMemoryState` objeto no inicializado va a volcar todos los objetos actualmente en memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo para el [CMemoryState](#cmemorystate) constructor.

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::DumpStatistics

Imprime un informe de estadísticas de `CMemoryState` memoria conciso desde un objeto que se rellena con la función miembro [Difference.](#difference)

```
void DumpStatistics() const;
```

### <a name="remarks"></a>Observaciones

El informe, que se imprime en el dispositivo [afxDump,](diagnostic-services.md#afxdump) muestra lo siguiente:

Un informe de ejemplo proporciona información sobre el número (o la cantidad) de:

- bloques libres

- bloques normales

- Bloques CRT

- ignorar bloques

- bloques cliente

- memoria máxima utilizada por el programa en cualquier momento (en bytes)

- memoria total utilizada actualmente por el programa (en bytes)

Los bloques libres son el número `afxMemDF` de bloques cuya desasignación se retrasó si se estableció en `delayFreeMemDF`. Para obtener más información, vea [afxMemDF](diagnostic-services.md#afxmemdf), en la sección "Macros y globales de MFC".

### <a name="example"></a>Ejemplo

  El código siguiente debe colocarse en *projname*App.cpp. Defina las siguientes variables globales:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

En `InitInstance` la función, agregue la línea:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Agregue un controlador `ExitInstance` para la función y utilice el código siguiente:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Ahora puede ejecutar el programa en modo depurar `DumpStatistics` para ver la salida de la función.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
