---
title: C2097 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d6955a610e3109c3b16edf96913be4503ee4c647
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2097"></a>C2097 de Error del compilador
inicialización no válida  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Inicialización de una variable con un valor no constante.  
  
2.  Inicialización de una dirección corta con una dirección larga.  
  
3.  Inicialización de un local estructura, unión o matriz con una expresión no constante cuando se compila con **/Za**.  
  
4.  Inicialización con una expresión que contiene un operador de coma.  
  
5.  Inicialización con una expresión que no sea constante ni simbólica.
