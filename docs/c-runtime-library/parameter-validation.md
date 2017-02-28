---
title: "Validación de parámetros | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 749e734bc4657efff3f0dfaeb735a0ea69375d02
ms.lasthandoff: 02/24/2017

---
# <a name="parameter-validation"></a>Validación de parámetros
La mayoría de las funciones de CRT con seguridad mejorada y muchas de las funciones existentes validan sus parámetros. Esto puede incluir la comprobación de punteros NULL, la comprobación de que los enteros están comprendidos en un intervalo válido o la comprobación de que los valores de enumeración son válidos. Cuando se encuentre un parámetro no válido, se ejecutará el controlador de parámetros no válidos.  
  
## <a name="invalid-parameter-handler-routine"></a>Rutina de controlador de parámetros no válidos  
 Cuando una función de biblioteca en tiempo de ejecución de C detecta un parámetro no válido, captura información sobre el error y llama a una macro que encapsula una función de distribución del controlador de parámetros no válidos, una de las funciones [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md) o [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md). La función de distribución que se llame depende de que el código sea, respectivamente, una compilación de depuración o una compilación comercial, o que el error no se considere recuperable. 
 
 En compilaciones de depuración, la macro de parámetros no válidos normalmente genera un error de aserción y un punto de interrupción del depurador antes de que se llame a la función de distribución. Cuando se ejecuta el código, puede que la aserción se notifique al usuario en un cuadro de diálogo con las opciones "Anular", "Reintentar" y "Continuar" u otras similares, en función de la versión de la biblioteca en tiempo de ejecución y del sistema operativo. Estas opciones permiten al usuario finalizar inmediatamente el programa, asociar un depurador o permitir que el código existente siga ejecutándose, lo que llama a la función de distribución. 
 
 La función de distribución del controlador de parámetros no válidos llama a su vez al controlador de parámetros no válidos actualmente asignado. De manera predeterminada, el parámetro no válido llama a `_invoke_watson`, que hace que la aplicación se "bloquee", es decir, termine y genere un minivolcado. Si se habilita mediante el sistema operativo, un cuadro de diálogo pregunta al usuario si quiere cargar el volcado de memoria en Microsoft para su análisis.   
  
 Este comportamiento puede modificarse mediante las funciones [_set_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) o [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) para establecer el controlador de parámetros no válidos en la función del usuario. Si la función que especifique no finaliza la aplicación, el control vuelve a la función que recibe los parámetros no válidos. En el CRT, estas funciones normalmente interrumpen la ejecución de la función, establecen `errno` en un código de error y devuelven un código de error. En muchos casos, el valor `errno` y el valor devuelto son `EINVAL`, lo que indica un parámetro no válido. En algunos casos, se devuelve un código de error más específico, como, por ejemplo, `EBADF` para un puntero de archivo incorrecto que se pasa como parámetro. Para obtener más información sobre `errno`, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="see-also"></a>Vea también  
 [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
