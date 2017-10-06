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
caps.latest.revision: 9
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
ms.openlocfilehash: 779a788cae6523a48a82694e55edf3c1da5519d7
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="wildcard-expansion"></a>Expansión de caracteres comodín
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Puede utilizar caracteres comodín (signo de interrogación (?) y asterisco (*)) para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.  
  
 Argumentos de línea de comandos se administran mediante una rutina denominada **_setargv** (o **_wsetargv** en el entorno de caracteres anchos), que de forma predeterminada no expande los caracteres comodín en cadenas independientes en el `argv`matriz de cadenas. Para obtener más información acerca de cómo habilitar la expansión de caracteres comodín, consulte [expansión de argumentos comodín](../c-language/expanding-wildcard-arguments.md).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [main: Inicio de programa](../cpp/main-program-startup.md)
