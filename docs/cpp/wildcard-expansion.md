---
title: "Expansión de caracteres comodín | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c9bbb5dcc706e08b2b985769248969f9bd23201
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="wildcard-expansion"></a>Expansión de caracteres comodín
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Puede utilizar caracteres comodín (signo de interrogación (?) y asterisco (*)) para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.  
  
 Argumentos de línea de comandos se administran mediante una rutina denominada **_setargv** (o **_wsetargv** en el entorno de caracteres anchos), que de forma predeterminada no expande los caracteres comodín en cadenas independientes en el `argv`matriz de cadenas. Para obtener más información acerca de cómo habilitar la expansión de caracteres comodín, consulte [expansión de argumentos comodín](../c-language/expanding-wildcard-arguments.md).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [main: Inicio de programa](../cpp/main-program-startup.md)