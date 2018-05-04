---
title: Entra en conflicto con el x86 compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cd72de4922c297b4a230e0dc0fb606b56a2a473
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="conflicts-with-the-x86-compiler"></a>Conflictos con el compilador de x86
Tipos de datos que son mayores de 4 bytes no se alinean automáticamente en la pila cuando se usa el x86 compilador para compilar una aplicación. Dado que la arquitectura de la x86 compilador es una pila alineada de 4 bytes, cualquier valor mayor de 4 bytes, por ejemplo, un entero de 64 bits, no se alineará automáticamente con una dirección de 8 bytes.  
  
 Trabajar con datos no alineados tiene dos implicaciones.  
  
-   Puede tardar más tiempo en obtener acceso a ubicaciones desalineadas necesario para tener acceso a ubicaciones alineadas.  
  
-   Ubicaciones desalineadas no se puede usar en las operaciones de interbloqueos.  
  
 Si necesita una alineación más estricta, utilice `__declspec(align(N)) on your variable declarations`. Esto hace que el compilador alinear dinámicamente la pila para cumplir sus especificaciones. Sin embargo, al ajustar la pila dinámicamente en tiempo de ejecución, puede producir una ejecución más lenta de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)