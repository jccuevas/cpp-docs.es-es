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
ms.openlocfilehash: a1a6912cd736643313306f6453ce19b1f6b97adc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502978"
---
# <a name="cmemorystate-structure"></a>CMemoryState (estructura)

Proporciona una manera cómoda para detectar pérdidas de memoria en el programa.

## <a name="syntax"></a>Sintaxis

```
struct CMemoryState
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Crea una estructura de clase que controla los puntos de comprobación de memoria.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMemoryState:: Checkpoint](#checkpoint)|Obtiene una instantánea (punto de comprobación) del estado actual de memoria.|
|[CMemoryState:: Difference](#difference)|Calcula la diferencia entre dos objetos de tipo `CMemoryState`.|
|[CMemoryState:: DumpAllObjectsSince](#dumpallobjectssince)|Vuelca un resumen de todos los objetos asignados actualmente desde un punto de comprobación anterior.|
|[CMemoryState:: DumpStatistics](#dumpstatistics)|Imprime las estadísticas de la asignación de memoria para un `CMemoryState` objeto.|

## <a name="remarks"></a>Comentarios

`CMemoryState` es una estructura y no tiene una clase base.

Una "pérdida de memoria" se produce cuando la memoria de un objeto está asignada en el montón pero no desasigna cuando ya no es necesario. Tales pérdidas de memoria finalmente pueden provocar errores de memoria insuficiente. Hay varias maneras de asignar y desasignar memoria en el programa:

- Mediante el `malloc` /  `free` familia de funciones de la biblioteca de tiempo de ejecución.

- Uso de las funciones de administración de memoria de API de Windows, `LocalAlloc` /  `LocalFree` y `GlobalAlloc` /  `GlobalFree`.

- En C++ **nueva** y **eliminar** operadores.

El `CMemoryState` diagnóstico sólo ayuda a detectar memoria pérdidas producidas cuando asigna memoria mediante la **nueva** operador no se desasigna mediante **eliminar**. Son los dos grupos de funciones de administración de memoria para programas que no son de C++ y mezclarlos con **nueva** y **eliminar** no se recomienda en el mismo programa. Se proporciona una macro adicional, DEBUG_NEW, para reemplazar el **nuevo** operador cuando necesite un archivo y número de línea de seguimiento de asignaciones de memoria. DEBUG_NEW se usa siempre que normalmente usaría el **nuevo** operador.

Al igual que con otros diagnósticos, el `CMemoryState` diagnóstico solo está disponible en versiones de depuración del programa. Una versión de depuración debe definir la constante _DEBUG.

Si sospecha que el programa tiene una pérdida de memoria, puede usar el `Checkpoint`, `Difference`, y `DumpStatistics` funciones para detectar la diferencia entre el estado de memoria (objetos asignados) en dos puntos distintos en la ejecución del programa. Esta información puede ser útil para determinar si una función es limpiar todos los objetos que asigna.

Si simplemente saber dónde se produce el desequilibrio en la asignación y desasignación no proporciona suficiente información, puede usar el `DumpAllObjectsSince` función para volcar todos los objetos asignados desde la llamada anterior a `Checkpoint`. Este volcado de memoria muestra el orden de asignación, el archivo de código fuente y la línea donde fue asignado el objeto (si está usando para la asignación DEBUG_NEW), y la derivación del objeto, su dirección y su tamaño. `DumpAllObjectsSince` También llama a cada objeto `Dump` función para proporcionar información sobre su estado actual.

Para obtener más información sobre cómo usar `CMemoryState` y otros diagnósticos, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Las declaraciones de objetos de tipo `CMemoryState` y llamadas a funciones miembro deben ir entre corchetes por `#if defined(_DEBUG)/#endif` directivas. Esto hace que el diagnóstico de memoria que se incluirán solo en versiones de depuración del programa.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CMemoryState`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="checkpoint"></a>  CMemoryState:: Checkpoint

Toma una instantánea resumen de memoria y lo almacena en esta `CMemoryState` objeto.

```
void Checkpoint();
```

### <a name="remarks"></a>Comentarios

El `CMemoryState` funciones miembro [diferencia](#difference) y [DumpAllObjectsSince](#dumpallobjectssince) usar estos datos de instantánea.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.

##  <a name="cmemorystate"></a>  CMemoryState::CMemoryState

Construye un valor vacío `CMemoryState` objetos que deben rellenarse por la [Checkpoint](#checkpoint) o [diferencia](#difference) función miembro.

```
CMemoryState();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>  CMemoryState:: Difference

Compara dos `CMemoryState` objetos, a continuación, almacena la diferencia en esta `CMemoryState` objeto.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parámetros

*oldState*<br/>
El estado de memoria inicial tal como se define por un `CMemoryState` punto de control.

*newState*<br/>
El nuevo estado de memoria como se define en un `CMemoryState` punto de control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los dos Estados de memoria son diferentes; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

[Punto de comprobación](#checkpoint) debe llamar para cada uno de los dos parámetros de estado de memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.

##  <a name="dumpallobjectssince"></a>  CMemoryState:: DumpAllObjectsSince

Llama a la `Dump` función para todos los objetos de un tipo derivado de clase `CObject` que se asignaron (y todavía se asignan) desde la última [punto de comprobación](#checkpoint) llamar para este `CMemoryState` objeto.

```
void DumpAllObjectsSince() const;

```

### <a name="remarks"></a>Comentarios

Una llamada a `DumpAllObjectsSince` con sin inicializar `CMemoryState` objeto volcará todos los objetos actualmente en memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.

##  <a name="dumpstatistics"></a>  CMemoryState:: DumpStatistics

Imprime un informe de estadísticas de memoria concisa desde un `CMemoryState` objeto que se rellena con el [diferencia](#difference) función miembro.

```
void DumpStatistics() const;

```

### <a name="remarks"></a>Comentarios

El informe, que se imprime en la [afxDump](diagnostic-services.md#afxdump) dispositivo, se muestra lo siguiente:

Un informe de ejemplo proporciona información sobre el número o cantidad de:

- bloques libres

- bloques de tipo normal

- Bloques CRT

- Omitir bloques

- bloques cliente

- memoria máxima utilizada por el programa en cualquier momento (en bytes)

- memoria total usada actualmente por el programa (en bytes)

Los bloques libres son el número de bloques cuya desasignación se retrasa si `afxMemDF` se estableció en `delayFreeMemDF`. Para obtener más información, consulte [afxMemDF](diagnostic-services.md#afxmemdf), en la sección "MFC Macros y variables globales".

### <a name="example"></a>Ejemplo

  El siguiente código debe colocarse en *Nombre_proyecto*App.cpp. Defina las variables globales siguientes:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

En el `InitInstance` de función, agregue la línea:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Agregar un controlador para el `ExitInstance` funcionando y use el código siguiente:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Ahora puede ejecutar el programa en modo de depuración para ver la salida de la `DumpStatistics` función.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

