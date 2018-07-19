---
title: Exit (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d08ac1375fa383543eaafb5b3ce49cd2bbfbc4da
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941085"
---
# <a name="exit-function"></a>exit (Función)
El `exit` función, declarada en el archivo de inclusión estándar \<stdlib.h >, finaliza un programa de C++.  
  
 El valor proporcionado como argumento a `exit` se devuelve al sistema operativo como código de salida o de código de retorno del programa. Por convención, un código de retorno de cero significa que el programa se completó correctamente.  
  
> [!NOTE]
>  Puede usar las constantes EXIT_FAILURE y EXIT_SUCCESS, definido en \<stdlib.h >, para indicar éxito o error del programa.  
  
 Emitir un **devolver** instrucción desde el `main` función es equivalente a llamar a la `exit` función con el valor devuelto como argumento.  
  
 Para obtener más información, consulte [salir](../c-runtime-library/reference/exit-exit-exit.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="see-also"></a>Vea también  
 [Finalización del programa](../cpp/program-termination.md)