---
title: Prevención de contención del montón | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4f01bdbbc14e09fe8f9823eed738556ee876376
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762256"
---
# <a name="avoidance-of-heap-contention"></a>Prevención de contención del montón

Los administradores de cadena predeterminada proporcionados por MFC y ATL son contenedores sencillos sobre un montón global. Este montón global es completamente segura para subprocesos, lo que significa que varios subprocesos pueden asignar y liberar memoria de ella al mismo tiempo sin dañar el montón. Para ayudar a proporcionar seguridad para subprocesos, el montón debe serializar el acceso a sí mismo. Normalmente, esto se consigue con una sección crítica o un mecanismo de bloqueo similar. Siempre que dos subprocesos intentan obtener acceso al montón simultáneamente, un subproceso se bloquea hasta que finalice la solicitud del otro subproceso. Para muchas aplicaciones, esta situación se produce con poca frecuencia y el impacto de rendimiento de mecanismo de bloqueo del montón es insignificante. Sin embargo, las aplicaciones que tienen acceso con frecuencia el montón desde varios subprocesos contención de bloqueo del montón puede causar que la aplicación se ejecute más despacio que si se tratara de un único subproceso (incluso en equipos con varias CPU).

Las aplicaciones que usan [CStringT](../atl-mfc-shared/reference/cstringt-class.md) son especialmente susceptibles a la contención del montón porque las operaciones en `CStringT` objetos requieren con frecuencia la reasignación del búfer de cadena.

Una manera de reducir la contención del montón entre subprocesos es que cada subproceso asigne las cadenas de un montón privado y local de subproceso. Siempre que las cadenas asignadas con asignador de un subproceso determinado solo se usan en ese subproceso, el asignador no necesita ser seguro para subprocesos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un procedimiento de subproceso que asigna su propio montón privado del que no es segura para subprocesos que se usará para las cadenas en ese subproceso:

[!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]

## <a name="comments"></a>Comentarios

Se pueden ejecutar varios subprocesos con este mismo procedimiento de subproceso, pero dado que cada subproceso tiene su propio montón existe contención entre subprocesos. Además, el hecho de que cada montón no es segura para subprocesos ofrece un aumento del rendimiento cuantificable incluso si se está ejecutando una sola copia del subproceso. Esto es el resultado del montón no usa operaciones costosas de bloqueo para proteger contra el acceso simultáneo.

Para obtener un procedimiento de subproceso más complicado, puede ser conveniente almacenar un puntero al administrador de cadenas del subproceso en una ranura de almacenamiento local (TLS) del subproceso. Esto permite que otras funciones llamadas por el procedimiento de subproceso para tener acceso al administrador de cadena del subproceso.

## <a name="see-also"></a>Vea también

[Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

