---
title: Especificar un archivo insertado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef2183390b2aca2fb54e1468bd59e697374a355a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-an-inline-file"></a>Especificar un archivo insertado
Especificar dos corchetes angulares (<<) en el comando donde *filename* va a aparecer. Los corchetes angulares no puede ser una expansión de macro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<<[filename]  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando se ejecuta el comando, los corchetes angulares se reemplazan por *filename*, si se especifica, o por un nombre único generado por NMAKE. Si se especifica, *filename* debe seguir los corchetes angulares sin espacios ni tabulaciones. Se permite una ruta de acceso. Requiere o supone ninguna extensión. Si *filename* se especifica, se crea el archivo actual o el directorio especificado, reemplazando los archivos con ese nombre; en caso contrario, se crea en el directorio TMP (o el directorio actual, si la variable de entorno TMP no está definido). Si una anterior *filename* es volver a usar, NMAKE reemplaza el archivo anterior.  
  
## <a name="see-also"></a>Vea también  
 [Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)