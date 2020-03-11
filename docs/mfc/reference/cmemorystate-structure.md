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
ms.openlocfilehash: a110e1345cb970c117de125bd8105e1bc86eaf94
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855350"
---
# <a name="cmemorystate-structure"></a>CMemoryState (estructura)

Proporciona una manera cómoda de detectar pérdidas de memoria en el programa.

## <a name="syntax"></a>Sintaxis

```
struct CMemoryState
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMemoryState:: CMemoryState](#cmemorystate)|Construye una estructura similar a una clase que controla los puntos de control de memoria.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMemoryState:: Checkpoint](#checkpoint)|Obtiene una instantánea (punto de comprobación) del estado actual de la memoria.|
|[CMemoryState::D ifference](#difference)|Calcula la diferencia entre dos objetos de tipo `CMemoryState`.|
|[CMemoryState::D umpAllObjectsSince](#dumpallobjectssince)|Vuelca un resumen de todos los objetos asignados actualmente desde un punto de control anterior.|
|[CMemoryState::D umpStatistics](#dumpstatistics)|Imprime estadísticas de asignación de memoria para un objeto `CMemoryState`.|

## <a name="remarks"></a>Observaciones

`CMemoryState` es una estructura y no tiene una clase base.

Una "pérdida de memoria" se produce cuando se asigna memoria para un objeto en el montón pero no se cancela la asignación cuando ya no es necesario. Estas fugas de memoria pueden dar lugar a errores de memoria insuficiente. Hay varias maneras de asignar y desasignar memoria en el programa:

- Con el `malloc`/ `free` familia de funciones de la biblioteca en tiempo de ejecución.

- Con las funciones de administración de memoria de la API de Windows, `LocalAlloc`/ `LocalFree` y `GlobalAlloc`/ `GlobalFree`.

- Usar los C++ operadores **New** y **Delete** .

Los diagnósticos de `CMemoryState` solo ayudan a detectar pérdidas de memoria producidas cuando la memoria asignada con el operador **New** no se cancela mediante la **eliminación**. Los otros dos grupos de funciones de administración de memoria son para losC++ programas que no son de y no se recomienda combinarlos con **New** y **Delete** en el mismo programa. Se proporciona una macro adicional, DEBUG_NEW, para reemplazar el operador **New** cuando se necesita seguimiento de archivos y números de línea de las asignaciones de memoria. DEBUG_NEW se utiliza siempre que normalmente se usaría el operador **New** .

Como con otros diagnósticos, el diagnóstico de `CMemoryState` solo está disponible en las versiones de depuración del programa. Una versión de depuración debe tener definida la constante _DEBUG.

Si sospecha que el programa tiene una pérdida de memoria, puede usar las funciones `Checkpoint`, `Difference`y `DumpStatistics` para detectar la diferencia entre el estado de la memoria (objetos asignados) en dos puntos diferentes en la ejecución del programa. Esta información puede ser útil para determinar si una función está limpiando todos los objetos que asigna.

Si simplemente sabe dónde se produce el desequilibrio en la asignación y desasignación, no proporciona suficiente información, puede usar la función `DumpAllObjectsSince` para volcar todos los objetos asignados desde la llamada anterior a `Checkpoint`. Este volcado de memoria muestra el orden de asignación, el archivo de código fuente y la línea donde se asignó el objeto (si usa DEBUG_NEW para la asignación) y la derivación del objeto, su dirección y su tamaño. `DumpAllObjectsSince` también llama a la función `Dump` de cada objeto para proporcionar información sobre su estado actual.

Para obtener más información sobre cómo usar `CMemoryState` y otros diagnósticos, vea [depurar aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Las declaraciones de objetos de tipo `CMemoryState` y las llamadas a funciones miembro deben ir entre corchetes mediante directivas de `#if defined(_DEBUG)/#endif`. Esto hace que los diagnósticos de memoria se incluyan solo en las compilaciones de depuración del programa.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CMemoryState`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="checkpoint"></a>CMemoryState:: Checkpoint

Toma una instantánea de un resumen de la memoria y la almacena en este `CMemoryState` objeto.

```
void Checkpoint();
```

### <a name="remarks"></a>Observaciones

Las funciones miembro de `CMemoryState` [Difference](#difference) y [DumpAllObjectsSince](#dumpallobjectssince) usan estos datos de instantánea.

### <a name="example"></a>Ejemplo

  Vea el ejemplo del constructor [CMemoryState](#cmemorystate) .

##  <a name="cmemorystate"></a>CMemoryState:: CMemoryState

Construye un objeto de `CMemoryState` vacío que debe ser rellenado por la función miembro [Checkpoint](#checkpoint) o [Difference](#difference) .

```
CMemoryState();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>CMemoryState::D ifference

Compara dos objetos `CMemoryState` y, a continuación, almacena la diferencia en este objeto `CMemoryState`.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parámetros

*oldState*<br/>
Estado de memoria inicial tal y como lo define un punto de comprobación de `CMemoryState`.

*newState*<br/>
Nuevo estado de memoria tal y como lo define un punto de comprobación de `CMemoryState`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los dos Estados de memoria son diferentes; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Se debe haber llamado a [Checkpoint](#checkpoint) para cada uno de los dos parámetros de estado de memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo del constructor [CMemoryState](#cmemorystate) .

##  <a name="dumpallobjectssince"></a>CMemoryState::D umpAllObjectsSince

Llama a la función `Dump` para todos los objetos de un tipo derivado de la clase `CObject` que se asignaron (y se siguen asignando) desde la última llamada de [punto de comprobación](#checkpoint) para este objeto `CMemoryState`.

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Observaciones

La llamada a `DumpAllObjectsSince` con un objeto de `CMemoryState` no inicializado volcará todos los objetos que se encuentran actualmente en la memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo del constructor [CMemoryState](#cmemorystate) .

##  <a name="dumpstatistics"></a>CMemoryState::D umpStatistics

Imprime un informe conciso de estadísticas de memoria a partir de un objeto `CMemoryState` que está rellenado por la función miembro [Difference](#difference) .

```
void DumpStatistics() const;
```

### <a name="remarks"></a>Observaciones

El informe, que se imprime en el dispositivo [afxDump](diagnostic-services.md#afxdump) , muestra lo siguiente:

Un informe de ejemplo proporciona información sobre el número (o la cantidad) de:

- bloques libres

- bloques normales

- Bloques de CRT

- omitir bloques

- bloques cliente

- memoria máxima utilizada por el programa en cualquier momento (en bytes)

- memoria total usada actualmente por el programa (en bytes)

Los bloques libres son el número de bloques cuya desasignación se retrasó si `afxMemDF` se estableció en `delayFreeMemDF`. Para obtener más información, vea [afxMemDF](diagnostic-services.md#afxmemdf)en la sección "macros y variables globales de MFC".

### <a name="example"></a>Ejemplo

  El código siguiente debe colocarse en *Nombre_proyecto*app. cpp. Defina las variables globales siguientes:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

En la función `InitInstance`, agregue la línea:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Agregue un controlador para la función `ExitInstance` y use el código siguiente:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Ahora puede ejecutar el programa en modo de depuración para ver el resultado de la función `DumpStatistics`.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
