---
title: Error del compilador C3610 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f58d66e9d3dacfa2c0b38eb84fe51e0813a892d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3610"></a>Error del compilador C3610
'valuetype': tipo de valor debe ser 'a una conversión boxing' antes de que puede llamar al método 'método'  
  
 De forma predeterminada, un tipo de valor no está en el montón administrado. Antes de que se puede llamar a métodos de las clases de .NET en tiempo de ejecución, como `Object`, debe mover el tipo de valor al montón administrado.  
  
 Solo es accesible mediante la opción del compilador obsoleta C3610 **/CLR: oldSyntax**.  
