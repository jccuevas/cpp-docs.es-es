---
title: Palabras reservadas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
dev_langs:
- C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35f9a3e907b72b4b8cf8e673e771832ba3fc0527
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="reserved-words"></a>Palabras reservadas
Las siguientes palabras están reservadas por el vinculador. Estos nombres pueden utilizarse como argumentos en [las instrucciones de definición de módulo](../../build/reference/module-definition-dot-def-files.md) solo si el nombre se incluye entre comillas dobles ("").  
  
||||  
|-|-|-|  
|**OBJETO APPLOADER**1|**INITINSTANCE**2|**PRECARGA**|  
|**BASE**|**IOPL**|**PRIVADA**|  
|**CÓDIGO**|**BIBLIOTECA**1|**PROTMODE**2|  
|**CONFORME**|**LOADONCALL**1|**PURO**1|  
|**DATOS**|**LONGNAMES**2|**SOLO LECTURA**|  
|**DESCRIPCIÓN**|**PUEDE MOVER**1|**LECTURA Y ESCRITURA**|  
|**DEV386**|**MOVEABLE**1|**REALMODE**1|  
|**DESCARTABLE**|**VARIOS**|**RESIDENTE**|  
|**DINÁMICA**|**NOMBRE**|**RESIDENTNAME**1|  
|**SOLO PARA EJECUTAR**|**NEWFILES**2|**SECCIONES**|  
|**EXECUTEONLY**|**NODATA**1|**SEGMENTOS**|  
|**EJECUCIÓNLECTURA**|**NOIOPL**1|**COMPARTIDO**|  
|**EXETYPE**|**NONAME**|**ÚNICO**|  
|**EXPORTS**|**NO COMPATIBLE**1|**STACKSIZE**|  
|**FIJO**1|**NONDISCARDABLE**|**STUB**|  
|**FUNCIONES**2|**NINGUNO**|**VERSIÓN**|  
|**HEAPSIZE**|**NO COMPARTIDOS**|**WINDOWAPI**|  
|**IMPORTACIONES**|**NOTWINDOWCOMPAT**1|**WINDOWCOMPAT**|  
|**IMPURAS**1|**OBJETOS**|**WINDOWS**|  
|**INCLUIR**2|**ANTIGUO**1||  
  
 1 el vinculador emite una advertencia ("omitida") cuando encuentra este término. Sin embargo, la palabra se sigue reserva.  
  
 2 el vinculador omite esta palabra, pero no genera ninguna advertencia.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)