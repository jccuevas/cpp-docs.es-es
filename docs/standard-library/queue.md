---
title: '&lt;queue&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: 506ab5fccd44ad37a08a9f741f44f24d3a85b87d
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2019
ms.locfileid: "68956995"
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

Define las clases de plantilla priority_queue y queue, así como varias plantillas auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<queue>

**Espacio de nombres:** std

> [!NOTE]
> La \<biblioteca de > de colas también `#include <initializer_list>` utiliza la instrucción.

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|Comprueba si el objeto queue en el lado izquierdo del operador no es igual al objeto queue del lado derecho.|
|[operator<](../standard-library/queue-operators.md#op_lt)|Comprueba si el objeto queue en el lado izquierdo del operador es inferior al objeto queue del lado derecho.|
|[operator\<=](../standard-library/queue-operators.md#op_gt_eq)|Comprueba si el objeto queue en el lado izquierdo del operador es inferior a o igual que el objeto queue del lado derecho.|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|Comprueba si el objeto queue en el lado izquierdo del operador es igual al objeto queue del lado derecho.|
|[operator>](../standard-library/queue-operators.md#op_gt)|Comprueba si el objeto queue en el lado izquierdo del operador es mayor que el objeto queue del lado derecho.|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|Comprueba si el objeto queue en el lado izquierdo del operador es mayor que o igual al objeto queue del lado derecho.|

### <a name="classes"></a>Clases

|||
|-|-|
|[queue (Clase)](../standard-library/queue-class.md)|Clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad que limita el acceso a los elementos frontal y trasero de algún tipo de contenedor subyacente.|
|[priority_queue (Clase)](../standard-library/priority-queue-class.md)|Clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad que limita el acceso al elemento superior de algún tipo de contenedor subyacente, que siempre es el más grande.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
