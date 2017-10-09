---
title: Error del compilador C2220 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: dc31519b2153c66ea9bab42f536ba7c6be5b2a10
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2220"></a>Error del compilador C2220
advertencia tratada como error - no se ha generado ningún archivo objeto  
  
 [/WX](../../build/reference/compiler-option-warning-level.md) indica al compilador que trate todas las advertencias como errores. Debido a que se ha producido un error, no se ha generado ningún archivo objeto o ejecutable.  
  
 Este error solo aparece cuando la **/WX** marca se establece y se produce una advertencia durante la compilación. Para corregir este error, debe eliminar cada advertencia en el proyecto.  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>Para corregirlo, use una de las técnicas siguientes  
  
-   Corregir los problemas que producen advertencias en el proyecto.  
  
-   Compilar en un nivel de advertencia inferior, por ejemplo, utilice **/W3** en lugar de **/W4**.  
  
-   Use un [advertencia](../../preprocessor/warning.md) pragma para deshabilitar o suprimir una advertencia concreta.  
  
-   No utilice **/WX** para compilar.
