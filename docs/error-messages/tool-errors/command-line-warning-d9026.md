---
title: Advertencia de línea de comandos D9026 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2d99573ee46c51178cc2fe995fa0f526b800f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9026"></a>Advertencia de la línea de comandos D9026
opciones se aplican a toda la línea de comandos  
  
 Se especificó una opción en un comando después de que se especificó un nombre de archivo. La opción se aplica al archivo que le preceden.  
  
 Por ejemplo, en el comando  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 el archivo VERDI.c se compilará con la opción/G5, el valor predeterminado de no/G4.  
  
 Este comportamiento es distinto de algunas versiones anteriores, que se aplican solo las opciones especificadas antes el nombre de archivo, lo que produce VERDI.c que se está compilando con/G4 y PUCCINI.c que se compiló con/G5.