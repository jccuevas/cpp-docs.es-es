---
title: Ensamblado intrínseco y en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b8651bea0b1ee9f54ec0af704d92feef0722368
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367984"
---
# <a name="intrinsics-and-inline-assembly"></a>Ensamblado intrínseco y en línea
Una de las restricciones para la [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] compilador es que no se admite la ensamblador en línea. Esto significa que las funciones que no se puede escribir en C o C++ tendrán que escribirse como subrutinas o como funciones intrínsecas compatibles con el compilador. Algunas funciones les afecta el rendimiento mientras que otros no lo están. Funciones sensibles al rendimiento deben implementarse como funciones intrínsecas.  
  
 Las funciones intrínsecas compatibles con el compilador se describen en [funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)