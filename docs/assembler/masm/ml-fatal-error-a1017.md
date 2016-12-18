---
title: "ML Fatal Error A1017 | Microsoft Docs"
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
  - "A1017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1017"
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Fatal Error A1017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**nombre del archivo origen que faltan**  
  
 El ml no pudo encontrar un archivo para ensamblar o para pasar al vinculador.  
  
 Este error se genera cuando proporciona opciones de la línea de comandos de ML. sin especificar un nombre de archivo que actúe sobre.  Para ensamblar los archivos que no tienen una extensión .asm, utilice la opción de línea de comandos **\/Ta** .  
  
 Este error también se puede generar invocando el ml sin parámetros si la variable de entorno de ML. contiene opciones de la línea de comandos.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)