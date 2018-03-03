---
title: "system (Función) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3e2c41ec95b0e26276df4f9f42d2ac46de54975
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="system-function"></a>system (Función)
**ANSI 4.10.4.5** Contenido y modo de ejecución de la cadena por la función **system**  
  
 La función **system** ejecuta un comando interno del sistema operativo, o un archivo .EXE, .COM (.CMD en Windows NT) o .BAT dentro de un programa de C, en lugar de la línea de comandos.  
  
 La función system encuentra el intérprete de comandos, que es normalmente CMD.EXE en el sistema operativo Windows NT o COMMAND.COM en Windows. Después, la función system pasa la cadena del argumento al intérprete de comandos.  
  
 Para más información, vea [system, _wsystem](../c-runtime-library/reference/system-wsystem.md).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)