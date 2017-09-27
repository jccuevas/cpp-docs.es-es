---
title: "Exit (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 240636bf7b6f10421c5d4ebd202a5fb3473a819d
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="exit-function"></a>exit (Función)
El **salir** función, declarada en el archivo de inclusión estándar STDLIB. H, se finaliza un programa de C++.  
  
 El valor proporcionado como argumento pasado a **salir** se devuelve al sistema operativo como código de salida o de código de retorno del programa. Por convención, un código de retorno de cero significa que el programa se completó correctamente.  
  
> [!NOTE]
>  Puede utilizar las constantes `EXIT_FAILURE` y `EXIT_SUCCESS`, definidas en STDLIB.H, para indicar si el programa se ha completado correctamente o ha generado errores.  
  
 Emitir un `return` instrucción desde la **principal** función es equivalente a llamar a la **salir** función con el valor devuelto como argumento.  
  
 Para obtener más información, consulte [salir](../c-runtime-library/reference/exit-exit-exit.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="see-also"></a>Vea también  
 [Finalización del programa](../cpp/program-termination.md)
