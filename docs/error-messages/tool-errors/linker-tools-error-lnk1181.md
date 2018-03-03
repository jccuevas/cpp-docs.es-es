---
title: Las herramientas del vinculador LNK1181 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5092d4f3ce7b4f96ca4dc5c1554483a7fc3a0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1181"></a>Error de las herramientas del vinculador LNK1181
no se puede abrir el archivo de entrada 'filename'  
  
 No se encontró el vinculador `filename` porque no existe o no se encontró la ruta de acceso.  
  
 Algunas causas comunes de error LNK1181 incluyen:  
  
-   `filename`se hace referencia como una dependencia adicional en la línea del vinculador, pero el archivo no existe.  
  
-   A **/libpath** instrucción que especifica el directorio que contiene `filename` falta.  
  
 Para resolver los problemas mencionados anteriormente, asegúrese de que los archivos que se hace referencia en la línea del vinculador están presentes en el sistema.  Compruebe también existe una **/libpath** instrucción para cada directorio que contiene un archivo dependiente del vinculador.  
  
 Otra causa posible de LNK1181 es que un nombre de archivo largo con espacios incrustados no se incluye entre comillas.  En ese caso, el vinculador sólo reconoce un nombre de archivo hasta el primer espacio y, a continuación, se supone una extensión de archivo. obj.  La solución a esta situación es incluir el nombre de archivo largos (nombre de archivo además de la ruta de acceso) entre comillas.  
  
 Para obtener más información, consulte [archivos .lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Vea también  
 [/LIBPATH (directorios de bibliotecas adicionales)](../../build/reference/libpath-additional-libpath.md)