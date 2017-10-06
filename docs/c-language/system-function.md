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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: b504aedc5ad11edf40d7b797529065757dfb58e6
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="system-function"></a>system (Función)
**ANSI 4.10.4.5** Contenido y modo de ejecución de la cadena por la función **system**  
  
 La función **system** ejecuta un comando interno del sistema operativo, o un archivo .EXE, .COM (.CMD en Windows NT) o .BAT dentro de un programa de C, en lugar de la línea de comandos.  
  
 La función system encuentra el intérprete de comandos, que es normalmente CMD.EXE en el sistema operativo Windows NT o COMMAND.COM en Windows. Después, la función system pasa la cadena del argumento al intérprete de comandos.  
  
 Para más información, vea [system, _wsystem](../c-runtime-library/reference/system-wsystem.md).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)
