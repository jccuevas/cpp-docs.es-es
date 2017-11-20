---
title: Solidez | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.runtime
dev_langs: C++
helpviewer_keywords: robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 27412403fe6ce0f1884a2ea99790376acb1c5236
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="robustness"></a>Solidez
Use las siguientes funciones de la biblioteca en tiempo de ejecución de C para mejorar la solidez del programa.  
  
### <a name="run-time-robustness-functions"></a>Funciones de solidez en tiempo de ejecución  
  
|Función|Uso|  
|--------------|---------|  
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Transfiere el control al mecanismo de control de errores si el operador `new` no puede asignar memoria.|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Controla las excepciones Win32 (excepciones estructuradas de C) como con excepciones con tipo de C++.|  
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instala su propia función de finalización a la que debe llamar [terminate](../c-runtime-library/reference/terminate-crt.md).|  
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instala su propia función de finalización a la que debe llamar [unexpected](../c-runtime-library/reference/unexpected-crt.md).|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)