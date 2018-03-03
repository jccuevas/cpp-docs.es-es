---
title: "Advertencia de línea de comandos D9026 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9127ad1887d476e5460798f806c2db1ff3144de3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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