---
title: Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7da71e6391d2d3223b47ba528686d2fec003ab3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321355"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación
Si el resultado de un paso de compilación personalizada o un evento de compilación tiene el formato correcto, los usuarios obtendrán las ventajas siguientes:  
  
-   Los errores y las advertencias se enumeran en la ventana **Salida**.  
  
-   La salida aparece en la ventana **Lista de tareas**.  
  
-   Al hacer clic en la salida en la ventana **Salida** se muestra el tema correspondiente.  
  
-   Las operaciones con F1 están habilitadas en las ventanas **Lista de tareas** o **Salida**.  
  
 El formato de la salida debe ser el siguiente:  
  
 {*nombreDeArchivo* (*nº_línea* [, *nº_columna*]) &#124; *nombreDeHerramienta*} **:**  
  
 [*cualquier texto*] {**error** &#124; **advertencia**} *código####***:*** cadena localizable*  
  
 [ *cualquier texto* ]  
  
 Dónde:  
  
-   {*a* &#124; *b*} es la elección de *a* o *b*.  
  
-   [`ccc`] es un parámetro o una cadena opcional.  
  
 Por ejemplo:  
  
 C:\\*archivo_de_origen.cpp*(134) : error C2143: error de sintaxis : falta ";" delante de "}"  
  
 LINK: error irrecuperable LNK1104: no se puede abrir el archivo "*una_biblioteca.lib*"  
  
## <a name="see-also"></a>Vea también  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)