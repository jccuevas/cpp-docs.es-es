---
title: "Directivas dot | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "directivas dot en NMAKE"
  - "NMAKE (programa), dot (directivas)"
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Directivas dot
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las directivas dot se especifican fuera de un bloque de descripción, al principio de una línea.  Las directivas dot comienzan con un punto \(. \) y van seguidas por dos puntos \(:\).  Se permiten los espacios y las tabulaciones.  Los nombres de las directivas dot distinguen entre mayúsculas y minúsculas y van en mayúsculas.  
  
|Directiva|Objetivo|  
|---------------|--------------|  
|**.IGNORE :**|Omite los códigos de salida distintos de cero devueltos por comandos, desde el lugar donde se especifica hasta el final del archivo MAKE.  De forma predeterminada, NMAKE se detiene si un comando devuelve un código de salida distinto de cero.  Para restaurar la comprobación de errores se utiliza **\!CMDSWITCHES**.  Para omitir el código de salida de un comando único se utiliza el modificador guión \(–\).  Para omitir los códigos de salida para un archivo completo se utiliza \/I.|  
|**.PRECIOUS :** *targets*|Conserva *targets* en el disco si los comandos que los actualizan se interrumpen; no tiene efecto si un comando controla una interrupción eliminando el archivo.  Los nombres de los destinos se separan con uno o más espacios o tabulaciones.  De forma predeterminada, NMAKE elimina un destino si una compilación se interrumpe mediante CTRL\+C o CTRL\+INTER.  Cada uso de **.PRECIOUS** se aplica a la totalidad del archivo MAKE; las especificaciones múltiples son acumulativas.|  
|**.SILENT :**|Suprime la presentación de comandos ejecutados, desde el lugar donde se especifica hasta el final del archivo MAKE.  De forma predeterminada, NMAKE muestra los comandos a los que llama.  Para restaurar la repetición se utiliza **\!CMDSWITCHES**.  Para suprimir la repetición de un comando único se utiliza el modificador **@**.  Para suprimir la repetición de un archivo completo se utiliza \/S.|  
|**.SUFFIXES :** `list`|Muestra las extensiones para la coincidencia de reglas de inferencia; se predefine para incluir las siguientes extensiones: .exe .obj .asm .c .cpp .cxx .bas .cbl .for .pas .res .rc .f .f90.|  
  
 Para cambiar el orden de la lista **.SUFFIXES** o para especificar una lista nueva, se ha de borrar la lista y especificar una nueva configuración.  Para borrar la lista, no se han de especificar extensiones después del signo de dos puntos:  
  
```  
.SUFFIXES :  
```  
  
 Para agregar otros sufijos al final de la lista, se ha de especificar  
  
```  
.SUFFIXES : suffixlist  
```  
  
 donde *suffixlist* es una lista de los sufijos que se agregan, separados por uno o varios espacios o tabulaciones.  Para ver la configuración actual de **.SUFFIXES**, se ha de ejecutar NMAKE con \/P.  
  
## Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)