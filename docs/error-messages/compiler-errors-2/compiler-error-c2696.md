---
title: C2696 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65ccdd6d2c8c34c360811b80d5a93abe76f5ef8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235044"
---
# <a name="compiler-error-c2696"></a>C2696 de Error del compilador
No se puede crear un objeto temporal de un tipo administrado 'type'  
  
Las referencias a `const` en un programa no administrado hacen que el compilador llame al constructor y crear un objeto temporal en la pila. Sin embargo, una clase administrada nunca puede crearse en la pila.  
  
Solo es accesible mediante la opción del compilador obsoleta C2696 **/CLR: oldSyntax**.  
