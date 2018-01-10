---
title: "Expandir argumentos de caracteres comodín | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f710cc1695579bf1a6f873229c347966888bc745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expanding-wildcard-arguments"></a>Expandir argumentos de caracteres comodín
**Específicos de Microsoft**  
  
 Cuando se ejecuta un programa de C, se puede usar cualquiera de estos dos caracteres comodín —el signo de interrogación (?) y el asterisco (*)— para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.  
  
 De forma predeterminada, los caracteres comodín no se expanden en argumentos de línea de comandos. Puede reemplazar la rutina de carga `argv` del vector de argumento normal por una versión que expanda los caracteres comodín mediante la vinculación con el archivo setargv.obj o wsetargv.obj. Si el programa usa una función `main` , debe vincularse con setargv.obj. Si el programa usa una función `wmain` , debe vincularse con wsetargv.obj. Ambos tienen un comportamiento equivalente.  
  
 Para establecer la vinculación con setargv.obj o wsetargv.obj, use la opción **/link** . Por ejemplo:  
  
 **cl example.c /link setargv.obj**  
  
 Los caracteres comodín se expanden de la misma manera que los comandos del sistema operativo. (Vea la guía del usuario del sistema operativo si no está familiarizado con los caracteres comodín).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Opciones de vínculo](../c-runtime-library/link-options.md)   
 [Función main y ejecución del programa](../c-language/main-function-and-program-execution.md)