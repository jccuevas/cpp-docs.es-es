---
title: "Archivos de entrada de LIB | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de entrada, LIB"
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos de entrada de LIB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los archivos de entrada que espera LIB dependerán del modo en que se esté utilizando, como se indica en la tabla siguiente.  
  
|Modo|Entrada|  
|----------|-------------|  
|Predeterminado \(compilar o modificar una biblioteca\)|Archivos objeto en formato COFF \(.obj\), bibliotecas COFF \(.lib\), archivos objeto \(.obj\) en Formato de modelo de objetos de 32 bits \(OMF\)|  
|Extraer un miembro con la opción \/EXTRACT|Biblioteca COFF \(.lib\)|  
|Compilar un archivo de exportación y una biblioteca de importación con la opción \/DEF|Archivos de definición de módulo \(.def\), archivos objeto en formato COFF \(.obj\), bibliotecas COFF \(.lib\), archivos objeto \(.obj\) en formato OMF de 32 bits|  
  
> [!NOTE]
>  No se pueden utilizar bibliotecas OMF creadas con la versión de 16 bits de la herramienta LIB como entrada de la versión de 32 bits de LIB.  
  
## Vea también  
 [Información general sobre LIB](../../build/reference/overview-of-lib.md)