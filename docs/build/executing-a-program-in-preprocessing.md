---
title: "Ejecutar un programa en el preprocesamiento | Microsoft Docs"
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
  - "ejecución de programas [C++]"
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Ejecutar un programa en el preprocesamiento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para usar el código de salida de un comando durante el preprocesamiento, se ha de especificar el comando, con los argumentos, entre corchetes \(\[ \]\).  Las macros se amplían antes de que el comando se ejecute.  NMAKE reemplaza la especificación de comando por el código de salida del comando, que se puede usar en una expresión para controlar el preprocesamiento.  
  
## Vea también  
 [Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)