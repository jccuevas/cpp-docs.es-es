---
title: Error del compilador C2220 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d23476de35e0af45b46a775683ba8673b4959346
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171498"
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