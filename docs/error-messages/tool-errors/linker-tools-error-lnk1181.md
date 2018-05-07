---
title: Las herramientas del vinculador LNK1181 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 617678e5453acdafaf72875857b0e0f9b84a110a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1181"></a>Error de las herramientas del vinculador LNK1181
no se puede abrir el archivo de entrada 'filename'  
  
 No se encontró el vinculador `filename` porque no existe o no se encontró la ruta de acceso.  
  
 Algunas causas comunes de error LNK1181 incluyen:  
  
-   `filename` se hace referencia como una dependencia adicional en la línea del vinculador, pero el archivo no existe.  
  
-   A **/libpath** instrucción que especifica el directorio que contiene `filename` falta.  
  
 Para resolver los problemas mencionados anteriormente, asegúrese de que los archivos que se hace referencia en la línea del vinculador están presentes en el sistema.  Compruebe también existe una **/libpath** instrucción para cada directorio que contiene un archivo dependiente del vinculador.  
  
 Otra causa posible de LNK1181 es que un nombre de archivo largo con espacios incrustados no se incluye entre comillas.  En ese caso, el vinculador sólo reconoce un nombre de archivo hasta el primer espacio y, a continuación, se supone una extensión de archivo. obj.  La solución a esta situación es incluir el nombre de archivo largos (nombre de archivo además de la ruta de acceso) entre comillas.  
  
 Para obtener más información, consulte [archivos .lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Vea también  
 [/LIBPATH (Directorios de bibliotecas adicionales)](../../build/reference/libpath-additional-libpath.md)