---
title: Ejecutar NMAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6c39612cf4df47665f7ea3d529b77ee4e70ce8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="running-nmake"></a>Ejecutar NMAKE
## <a name="syntax"></a>Sintaxis  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## <a name="remarks"></a>Comentarios  
 Compilaciones NMAKE solo especificados *destinos* o, si no se especifica ninguno, el primer destino en el archivo MAKE. El primer destino de archivo MAKE puede ser un [pseudodestino](../build/pseudotargets.md) que genera otros destinos. NMAKE utiliza los archivos MAKE especificados con/f; Si no se especifica/f, utiliza el archivo MAKE en el directorio actual. Si no se especifica ningún archivo MAKE, utiliza reglas de inferencia para generar la línea de comandos *destinos*.  
  
 El `commandfile` archivo de texto (o un archivo de respuesta) contiene una entrada de línea de comandos. Otra entrada puede delante o detrás de`commandfile`. Se permite una ruta de acceso. En `commandfile`, saltos de línea se tratan como espacios. Escriba las definiciones de macro entre comillas si contienen espacios.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Opciones de NMAKE](../build/nmake-options.md)  
  
 [Tools.ini y NMAKE](../build/tools-ini-and-nmake.md)  
  
 [Códigos de salida de NMAKE](../build/exit-codes-from-nmake.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)