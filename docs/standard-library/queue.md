---
title: '&lt;queue&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <queue>
dev_langs:
- C++
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3bccad1ff20a314c562b580d4d5102f283bcef56
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

Define las clases de plantilla priority_queue y queue, así como varias plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <queue>

```

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|Comprueba si el objeto queue en el lado izquierdo del operador no es igual al objeto queue del lado derecho.|
|[operator<](../standard-library/queue-operators.md#op_lt)|Comprueba si el objeto queue en el lado izquierdo del operador es inferior al objeto queue del lado derecho.|
|[operator\<=](../standard-library/queue-operators.md#op_gt_eq)|Comprueba si el objeto queue en el lado izquierdo del operador es inferior a o igual que el objeto queue del lado derecho.|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|Comprueba si el objeto queue en el lado izquierdo del operador es igual al objeto queue del lado derecho.|
|[operator>](../standard-library/queue-operators.md#op_gt)|Comprueba si el objeto queue en el lado izquierdo del operador es mayor que el objeto queue del lado derecho.|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|Comprueba si el objeto queue en el lado izquierdo del operador es mayor que o igual al objeto queue del lado derecho.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[queue (Clase)](../standard-library/queue-class.md)|Clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad que limita el acceso a los elementos frontal y trasero de algún tipo de contenedor subyacente.|
|[priority_queue (Clase)](../standard-library/priority-queue-class.md)|Clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad que limita el acceso al elemento superior de algún tipo de contenedor subyacente, que siempre es el más grande.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
