---
title: Error del compilador C3610 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0cacac87535864c6268d0f078566b9ab224e9151
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3610"></a>Error del compilador C3610
'valuetype': tipo de valor debe ser 'a una conversión boxing' antes de que puede llamar al método 'método'  
  
 De forma predeterminada, un tipo de valor no está en el montón administrado. Antes de que se puede llamar a métodos de las clases de .NET en tiempo de ejecución, como `Object`, debe mover el tipo de valor al montón administrado.  
  
 Solo es accesible mediante la opción del compilador obsoleta C3610 **/CLR: oldSyntax**.  

