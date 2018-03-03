---
title: Error irrecuperable C1311 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a0d798ea53ebbbfe850b77b4b8176b35e2040ed8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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