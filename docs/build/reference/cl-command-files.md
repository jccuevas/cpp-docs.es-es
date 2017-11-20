---
title: Archivos de comandos de CL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8e42c349436bd0df4f1e26b35d238b6e1ee75c32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cl-command-files"></a>Archivos de comandos de CL
Un archivo de comandos es un archivo de texto que contiene opciones y nombres de archivo en caso contrario, escribiría en la [línea de comandos](../../build/reference/compiler-command-line-syntax.md) o especificar utilizando el [variable de entorno de CL](../../build/reference/cl-environment-variables.md). CL acepta un archivo de comandos del compilador como un argumento en la variable de entorno de CL o en la línea de comandos. A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.  
  
 Opciones y nombres de archivo en un archivo de comandos se procesan según la ubicación de un nombre de archivo de comandos en la variable de entorno de CL o en la línea de comandos. Sin embargo, si la opción aparece en el archivo de comandos, todas las opciones en el resto de la línea se pasan al vinculador. Opciones de las líneas siguientes en el archivo de comandos y opciones en la línea de comandos después de la invocación del archivo de comandos aún se aceptan como opciones del compilador. Para obtener más información sobre cómo afecta el orden de las opciones a su interpretación, vea [orden de las opciones de CL](../../build/reference/order-of-cl-options.md).  
  
 Un archivo de comandos no debe contener el comando de CL. Cada opción debe empezar y finalizar en la misma línea; no se puede usar la barra diagonal inversa (\\) para combinar una opción en dos líneas.  
  
 Un archivo de comandos especificado por un signo de arroba (@) seguido por un nombre de archivo; el nombre de archivo puede especificar una ruta de acceso absoluta o relativa.  
  
 Por ejemplo, si es el siguiente comando en un archivo denominado RESP:  
  
```  
/Og /link LIBC.LIB  
```  
  
 y especifique el siguiente comando de CL:  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 el comando de CL es como sigue:  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 Tenga en cuenta que la línea de comandos y el archivo de comandos se combina eficazmente.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)