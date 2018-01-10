---
title: "Prevención de contención del montón | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f17f73efc8fba19bb129e3b118f8a4357444aad0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="avoidance-of-heap-contention"></a>Prevención de contención del montón
Los administradores de cadena predeterminada proporcionados por MFC y ATL son contenedores sencillos sobre un montón global. Este montón global es totalmente seguro para subprocesos, lo que significa que varios subprocesos pueden asignar y liberar memoria en él simultáneamente sin dañar el montón. Con el fin de proporcionar seguridad para subprocesos, el montón tiene que serializar el acceso a sí mismo. Esto se realiza normalmente con una sección crítica o un mecanismo de bloqueo similar. Cuando dos subprocesos intentan obtener acceso al montón simultáneamente, un subproceso se bloquea hasta que finalice la solicitud del otro subproceso. Para muchas aplicaciones, esta situación se produce raramente y el impacto en el rendimiento del mecanismo de bloqueo del montón es insignificante. Sin embargo, para las aplicaciones que tienen acceso con frecuencia el montón desde varios subprocesos contención de bloqueo del montón puede hacer que la aplicación se ejecute más despacio que si se tratara de un único subproceso (incluso en equipos con varias CPU).  
  
 Las aplicaciones que utilizan [CStringT](../atl-mfc-shared/reference/cstringt-class.md) son especialmente susceptibles a la contención de montón porque las operaciones en `CStringT` objetos requieren con frecuencia la reasignación del búfer de cadena.  
  
 Una manera de reducir la contención del montón entre subprocesos es que cada subproceso asigne las cadenas de un montón privado y local de subprocesos. Siempre y cuando las cadenas se asignan con asignador de un subproceso determinado se usan solo en ese subproceso, el asignador no tienen que ser seguro para subprocesos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un procedimiento de subproceso que asigna su propio montón privado de no es segura para subprocesos que se usará para las cadenas en ese subproceso:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]  
  
## <a name="comments"></a>Comentarios  
 Varios subprocesos pueden ejecutarse con este mismo procedimiento de subproceso, pero debido a que cada subproceso tiene su propio montón existe contención entre subprocesos. Además, el hecho de que cada montón no es seguro para subprocesos proporciona un aumento apreciable del rendimiento incluso si se ejecuta solo una copia del subproceso. Esto es el resultado del montón no utiliza las operaciones de interbloqueos costosas para proteger contra el acceso simultáneo.  
  
 Para un procedimiento de subproceso más complicado, puede ser conveniente almacenar un puntero al administrador de cadenas del subproceso en un espacio de almacenamiento local (TLS) del subproceso. Esto permite que otras funciones llamadas por el procedimiento de subproceso para tener acceso al administrador de cadena del subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

