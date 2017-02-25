---
title: "R6025 de Error de tiempo de ejecuci&#243;n de C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6025"
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error en tiempo de ejecuci&#243;n de C R6025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

llamada de función virtual pura  
  
 No se ha creado una instancia de ningún objeto para controlar la llamada de función virtual pura.  
  
 Si una aplicación muestra este error, póngase en contacto con el servicio de soporte técnico de su aplicación.  
  
 Este error se genera al llamar a una función virtual en una clase base abstracta a través de un puntero creado mediante una conversión al tipo de la clase derivada; sin embargo, se trata realmente de un puntero a la clase base.  Esto puede ocurrir cuando se convierte desde un puntero **void\*** a un puntero a una clase cuando el puntero **void\* se ha creado durante la construcción de la clase base.**  
  
 Para obtener más información, vea [Soporte técnico de Microsoft](http://go.microsoft.com/fwlink/?LinkId=75220) el sitio Web.