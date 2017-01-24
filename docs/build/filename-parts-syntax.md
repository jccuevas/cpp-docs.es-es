---
title: "Sintaxis de las partes de un nombre de archivo | Microsoft Docs"
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
  - "sintaxis de partes de nombres de archivos en NMAKE"
  - "NMAKE (programa), sintaxis"
  - "sintaxis, partes de nombre de archivos"
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Sintaxis de las partes de un nombre de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sintaxis de las partes de un nombre de archivo en los comandos representa componentes del primer nombre de archivo dependiente \(que puede ser un dependiente implícito\).  Los componentes de un nombre de archivo son la unidad, la ruta de acceso, el nombre base y la extensión del archivo según se especifican, no como existen en el disco.  Se ha de utilizar **%s** para representar el nombre de archivo completo.  Se ha de utilizar **%&#124;**\[*parts*\]**F** \(el signo de porcentaje va seguido de una barra vertical\) para representar las partes del nombre de archivo, donde *parts* puede ser una de las siguientes letras, en cualquier orden, o ninguna.  
  
|Carta|Descripción|  
|-----------|-----------------|  
|Ninguna letra|Nombre completo \(igual que **%s**\)|  
|**d**|Unidad|  
|**i**|Ruta de acceso|  
|**f**|Nombre base del archivo|  
|**e**|Extensión de archivo|  
  
 Por ejemplo, si el nombre de archivo es c:\\prog.exe:  
  
-   %s será c:\\prog.exe  
  
-   %&#124;F será c:\\prog.exe  
  
-   %&#124;dF será c  
  
-   %&#124;pF será c:\\  
  
-   %&#124;fF será prog  
  
-   %&#124;eF será exe  
  
## Vea también  
 [Comandos en un archivo MAKE](../build/commands-in-a-makefile.md)