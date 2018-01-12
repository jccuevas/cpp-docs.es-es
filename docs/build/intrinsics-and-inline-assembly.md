---
title: "Ensamblado intrínseco y en línea | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80eb16eb7fde49c499227bb3d60000e2ac6e5143
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="intrinsics-and-inline-assembly"></a>Ensamblado intrínseco y en línea
Una de las restricciones para la [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] compilador es que no se admite la ensamblador en línea. Esto significa que las funciones que no se puede escribir en C o C++ tendrán que escribirse como subrutinas o como funciones intrínsecas compatibles con el compilador. Algunas funciones les afecta el rendimiento mientras que otros no lo están. Funciones sensibles al rendimiento deben implementarse como funciones intrínsecas.  
  
 Las funciones intrínsecas compatibles con el compilador se describen en [funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)