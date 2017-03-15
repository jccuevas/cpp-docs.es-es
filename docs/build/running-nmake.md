---
title: "Ejecutar NMAKE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de comandos"
  - "archivos de comandos, NMAKE"
  - "NMAKE (programa), ejecutar"
  - "NMAKE (programa), destinos"
  - "archivos de respuesta, NMAKE"
  - "destinos"
  - "destinos, compilar"
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Ejecutar NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## Comentarios  
 NMAKE solo compila destinos *targets* especificados o, si no se especifican, el primer destino en el archivo MAKE.  El primer destino en el archivo MAKE puede ser un [pseudodestino](../build/pseudotargets.md) que compila otros destinos.  NMAKE utiliza los archivos MAKE especificados con \/F; si no se especifica \/F, utiliza el archivo MAKE del directorio actual.  Si no se especifica ningún archivo MAKE, utiliza reglas de inferencia para compilar destinos \(*target\)* de la línea de comandos.  
  
 El archivo de texto `commandfile` \(o archivo de respuesta\) contiene entradas de la línea de comandos.  Otras entradas pueden preceder o ir a continuación de @`commandfile`.  Se permite una ruta de acceso.  En `commandfile`, los saltos de línea se consideran espacios.  Las definiciones de macro se han de encerrar entre comillas si contienen espacios.  
  
## ¿Sobre qué desea obtener más información?  
 [Opciones de NMAKE](../build/nmake-options.md)  
  
 [Tools.ini y NMAKE](../build/tools-ini-and-nmake.md)  
  
 [Códigos de salida de NMAKE](../build/exit-codes-from-nmake.md)  
  
## Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)