---
title: Error irrecuperable C1311 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b3759a5fec4b072f9a9b300670d61cb0d101c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1311"></a>Error irrecuperable C1311
El formato COFF no puede inicializar estáticamente 'var' con número bytes de una dirección  
  
 Una dirección cuyo valor no se conoce en tiempo de compilación no se puede asignar estáticamente a una variable cuyo tipo tiene un almacenamiento de menos de cuatro bytes.  
  
 Este error puede producirse en el código que lo contrario, está C++ válido.  
  
 En el ejemplo siguiente se muestra una condición que podría producir el error C1311.  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```