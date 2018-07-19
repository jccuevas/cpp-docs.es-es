---
title: Expansión de caracteres comodín | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4de54cbbe978534a42dcb9cbfa677eb1597aa5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939141"
---
# <a name="wildcard-expansion"></a>Expansión de caracteres comodín
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Puede utilizar caracteres comodín (signo de interrogación (?) y asterisco (*)) para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.  
  
 Argumentos de línea de comandos se controlan mediante una rutina denominada `_setargv` (o `_wsetargv` en el entorno de caracteres anchos), que de forma predeterminada no expande los caracteres comodín en cadenas independientes en el `argv` matriz de cadenas. Para obtener más información acerca de cómo habilitar la expansión de caracteres comodín, consulte [expansión de argumentos comodín](../c-language/expanding-wildcard-arguments.md).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [main: Inicio de programa](../cpp/main-program-startup.md)