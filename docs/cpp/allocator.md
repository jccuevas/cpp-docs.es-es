---
title: asignador
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: f9c8de7c8686b89a2ab9570a2558e3f649e545b5
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58419093"
---
# <a name="allocator"></a>asignador

**Específicos de Microsoft**

El **asignador** especificador de declaración se puede aplicar a las funciones de asignación de memoria personalizado para que las asignaciones de visible a través de seguimiento de eventos para Windows (ETW).

## <a name="syntax"></a>Sintaxis

```
   __declspec(allocator) 
```

## <a name="remarks"></a>Comentarios

El generador de perfiles de memoria nativa en Visual Studio funciona mediante la recopilación de datos de eventos ETW emitidos durante el tiempo de ejecución de la asignación. Los asignadores de CRT y Windows SDK se han anotado en el nivel de origen para que se pueden capturar los datos de asignación. Si va a escribir sus propios asignadores, las funciones que devuelven un puntero a la memoria de montón recientemente asignada se pueden decorar con `__declspec(allocator)`, tal como se muestra en este ejemplo para myMalloc:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Para obtener más información, consulte [medir el uso de memoria en Visual Studio](/visualstudio/profiling/memory-usage) y [eventos de montón ETW nativos personalizados](/visualstudio/profiling/custom-native-etw-heap-events).