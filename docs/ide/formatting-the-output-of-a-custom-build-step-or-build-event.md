---
title: "Aplicar formato a los resultados de un paso de compilación personalizada o un evento de compilación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53720e93c7d45f1eaeb0e62749194720373bee1c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación
Si el resultado de un paso de compilación personalizada o un evento de compilación tiene el formato correcto, los usuarios obtendrán las siguientes ventajas:  
  
-   Errores y advertencias se enumeran en la **salida** ventana.  
  
-   Los resultados aparecen en la **lista de tareas** ventana.  
  
-   Al hacer clic en la salida en el **salida** ventana muestra el tema correspondiente.  
  
-   Las operaciones con F1 están habilitadas en el **lista de tareas** ventana o **salida** ventana.  
  
 El formato de la salida debe ser:  
  
 {*filename* (*línea #* [, *column #*]) &#124; *toolname*} **:**  
  
 [*cualquier texto*] {**error** &#124; **advertencia**} *código ###***:***cadenas localizables*  
  
 [ *cualquier texto* ]  
  
 Dónde:  
  
-   {*un* &#124; *b*} es una opción de uno de ellos *una* o *b*.  
  
-   [`ccc`] es un parámetro o una cadena opcional.  
  
 Por ejemplo:  
  
 C:\\*sourcefile.cpp*(134): error C2143: error de sintaxis: falta ';' antes de '}'  
  
 LINK: error irrecuperable LNK1104: no se puede abrir el archivo '*somelib.lib*'  
  
## <a name="see-also"></a>Vea también  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)