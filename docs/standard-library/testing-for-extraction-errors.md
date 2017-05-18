---
title: "Comprobar errores de extracción | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 05e2c94cc23a7ad75edcd92721de538ac008d65b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="testing-for-extraction-errors"></a>Comprobar errores de extracción
Las funciones de procesamiento de errores de salida, que se describen en [Funciones de procesamiento de errores](../standard-library/output-file-stream-member-functions.md), se aplican a los flujos de entrada. Es importante probar si hay errores durante la extracción. Considere esta instrucción:  
  
```  
cin>> n;  
```  
  
 Si `n` es un entero con signo, un valor mayor que 32.767 (el valor máximo permitido o MAX_INT) establece el bit `fail` de la secuencia y el objeto `cin` se vuelve inutilizable. Todas las extracciones posteriores generan una devolución inmediata sin ningún valor almacenado.  
  
## <a name="see-also"></a>Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)


