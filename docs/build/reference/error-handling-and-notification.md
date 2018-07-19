---
title: Control de errores y notificación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2edec23da89766a45545566b0a689001d3ca75f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373223"
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