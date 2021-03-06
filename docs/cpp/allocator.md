---
title: asignador
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 39708e8cfff7f61c3a3f763f87e1a3da36f0d4b1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077256"
---
# <a name="allocator"></a>asignador

**Específicos de Microsoft**

El especificador de declaración de **asignador** se puede aplicar a funciones de asignación de memoria personalizadas para que las asignaciones estén visibles a través del seguimiento de eventos para Windows (ETW).

## <a name="syntax"></a>Sintaxis

```
   __declspec(allocator)
```

## <a name="remarks"></a>Observaciones

El generador de perfiles de memoria nativa en Visual Studio funciona mediante la recopilación de datos de eventos ETW de asignación emitidos por durante el tiempo de ejecución. Los asignadores de CRT y Windows SDK se han anotado en el nivel de origen para que se pueden capturar los datos de asignación. Si escribe sus propios asignadores, las funciones que devuelven un puntero a la memoria de montón recién asignada se pueden decorar con `__declspec(allocator)`, tal como se puede observar en este ejemplo para myMalloc:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Para obtener más información, vea [medir el uso de memoria en Visual Studio](/visualstudio/profiling/memory-usage) y [eventos de montón ETW nativos personalizados](/visualstudio/profiling/custom-native-etw-heap-events).

**FIN de Específicos de Microsoft**
