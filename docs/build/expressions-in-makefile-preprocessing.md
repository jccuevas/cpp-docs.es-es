---
title: "Expresiones de preprocesamiento de archivos MAKE | Microsoft Docs"
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
  - "expresiones [C++], preprocesamiento de archivos make"
  - "Make (archivos), preprocesamiento"
  - "preprocesar archivos make"
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Expresiones de preprocesamiento de archivos MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La expresión **\!IF** o **\!ELSE IF**`constantexpression` está formada por constantes de tipo entero \(en notación decimal o de lenguaje C\), constantes de cadena o comandos.  Se han de utilizar paréntesis para agrupar expresiones.  Las expresiones utilizan aritmética de enteros largos con signo de estilo C; los números tienen el formato de complemento de factores de 2 de 32 bits, en el intervalo de –2147483648 a 2147483647.  
  
 Las expresiones pueden usar operadores que actúan en valores constantes, códigos de salida de comandos, cadenas, macros y rutas de acceso del sistema de archivos.  
  
## ¿Sobre qué desea obtener más información?  
 [Operadores de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-operators.md)  
  
 [Ejecutar un programa en el preprocesamiento](../build/executing-a-program-in-preprocessing.md)  
  
## Vea también  
 [Preprocesamiento de archivos MAKE](../build/makefile-preprocessing.md)