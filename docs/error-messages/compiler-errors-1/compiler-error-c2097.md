---
title: C2097 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b867c7f043d796f208fdc7100509893147daf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2097"></a>C2097 de Error del compilador
inicialización no válida  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Inicialización de una variable con un valor no constante.  
  
2.  Inicialización de una dirección corta con una dirección larga.  
  
3.  Inicialización de un local estructura, unión o matriz con una expresión no constante cuando se compila con **/Za**.  
  
4.  Inicialización con una expresión que contiene un operador de coma.  
  
5.  Inicialización con una expresión que no sea constante ni simbólica.