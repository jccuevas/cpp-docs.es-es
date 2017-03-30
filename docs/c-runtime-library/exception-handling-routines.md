---
title: Rutinas para el control de excepciones | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
caps.latest.revision: 8
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
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 3dd5d8dd77f2b62a6b0ea52e7d056b3d779cd2f4
ms.lasthandoff: 03/29/2017

---
# <a name="exception-handling-routines"></a>Rutinas para el control de excepciones
Utilice las funciones de control de excepciones de C++ para recuperarse de eventos inesperados durante la ejecución del programa.  
  
### <a name="exception-handling-functions"></a>Funciones de control de excepciones  
  
|Función|Uso|  
|--------------|---------|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Controla las excepciones Win32 (excepciones estructuradas de C), como excepciones con tipo de C++.|  
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instala su propia rutina de finalización a la que debe llamar `terminate`.|  
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instala su propia función de finalización a la que debe llamar `unexpected`.|  
|[terminate](../c-runtime-library/reference/terminate-crt.md)|Se llama automáticamente en determinadas circunstancias una vez generada la excepción. La función `terminate` llama a `abort` o a una función que se especifique mediante `set_terminate`.|  
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|Llama a `terminate` o a una función que se especifique mediante `set_unexpected`. La función `unexpected` no se usa en la implementación actual del control de excepciones de Microsoft C++.|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)
