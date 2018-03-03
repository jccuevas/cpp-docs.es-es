---
title: "Control de errores y notificación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 738721eb3fc37ba076157129cb88a22f2c90e464
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="error-handling-and-notification"></a>Notificación y control de errores
Para obtener más información sobre la notificación y control de errores, vea [descripción de la función auxiliar](understanding-the-helper-function.md).  
  
 Para obtener más información sobre las funciones de enlace, vea [definiciones de estructura y constante](../../build/reference/structure-and-constant-definitions.md).  
  
 Si el programa utiliza archivos DLL de carga retrasada, deberá controlar los errores Fortalezca de forma Puesto que dará como resultado errores que se producen mientras se ejecuta el programa en las excepciones no controladas. El control de errores está formado por dos partes:  
  
 Recuperación mediante un enlace.  
 Si se necesita el código recuperar o proporcionar una biblioteca y/o rutina alternativas en caso de error, puede proporcionar un enlace a la función auxiliar que puede proporcionar o solucionar el problema. La rutina del enlace tiene que devolver un valor apropiado, de modo que el proceso puede continuar (HINSTANCE o FARPROC) o 0 para indicar que se debe producir una excepción. También podría producir su propia excepción o **longjmp** desde el enlace. Existen enlaces de notificación y enlaces de error.  
  
 Informes a través de una excepción.  
 Si todo lo que es necesario para controlar el error es anular el procedimiento, ningún enlace es necesario siempre que el código de usuario puede controlar la excepción.  
  
 Los temas siguientes describen la notificación y control de errores:  
  
-   [Enlaces de notificación](../../build/reference/notification-hooks.md)  
  
-   [Enlaces de error](../../build/reference/failure-hooks.md)  
  
-   [Excepciones](../../build/reference/exceptions-c-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)