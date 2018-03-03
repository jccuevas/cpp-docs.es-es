---
title: Punto directivas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9958b13a6f06b0024ec2d4dd304abfe93b16741e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dot-directives"></a>Directivas dot
Especificar directivas dot fuera de un bloque de descripción, al principio de una línea. Directivas dot comienzan con un punto (. ) y van seguidas por dos puntos (:). Se permiten espacios y tabulaciones. Punto directivas nombres distinguen mayúsculas de minúsculas y mayúsculas.  
  
|Directiva|Propósito|  
|---------------|-------------|  
|**. PASAR POR ALTO:**|Omite los códigos de salida distinto de cero devueltos por comandos, desde el lugar que donde se especifica hasta el final del archivo MAKE. De forma predeterminada, NMAKE se detiene si un comando devuelve un código de salida distinto de cero. Para restaurar la comprobación de errores, utilice **! CMDSWITCHES**. Para pasar por alto el código de salida para un único comando, use el modificador de guión (-). Para omitir códigos de salida para un archivo completo se utiliza / I.|  
|**. PRECIOSOS:** *destinos*|Conserva *destinos* en disco si los comandos se actualizan se interrumpen; no tiene ningún efecto si un comando controla una interrupción eliminando el archivo. Separe los nombres de destino con uno o más espacios o tabulaciones. De forma predeterminada, NMAKE elimina un destino si una generación se interrumpe mediante CTRL+C o CTRL+INTER. Cada vez que **. Muy VALIOSO** se aplica a la totalidad del archivo MAKE; varias especificaciones son acumulativas.|  
|**. MODO SILENCIOSO:**|Suprime la presentación de los comandos ejecutados desde el lugar que donde se especifica hasta el final del archivo MAKE. De forma predeterminada, NMAKE muestra los comandos que se invoca. Para restaurar la repetición, use **! CMDSWITCHES**. Para suprimir la repetición de un único comando, use la  **@**  modificador. Para suprimir la repetición de un archivo completo, se utiliza/S.|  
|**. SUFIJOS:**`list`|Enumera las extensiones para la coincidencia de regla de inferencia; predefine para incluir las siguientes extensiones: .exe .obj .asm .c .cpp .cxx BAS Step .for .pas .res .rc .f. f90.|  
  
 Para cambiar la **. SUFIJOS** lista orden o para especificar una nueva lista, borrar la lista y especificar una nueva configuración. Para borrar la lista, no especifique ninguna extensión después de los dos puntos:  
  
```  
.SUFFIXES :  
```  
  
 Para agregar sufijos adicionales al final de la lista, especifique  
  
```  
.SUFFIXES : suffixlist  
```  
  
 donde *suffixlist* es una lista de los sufijos adicionales, separados por uno o más espacios o tabulaciones. Para ver la configuración actual de **. SUFIJOS**, ejecutar NMAKE con/p.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)