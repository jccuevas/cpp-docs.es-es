---
title: "Llamadas de funci&#243;n naked | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "código de epílogo"
  - "naked (funciones)"
  - "naked (palabra clave) [C++]"
  - "naked (palabra clave) [C++], atributo de clase de almacenamiento"
  - "código de prólogo"
  - "controladores de dispositivo virtual"
  - "controladores de dispositivo virtual, llamadas a función naked"
  - "controladores de dispositivo virtual VXD"
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Llamadas de funci&#243;n naked
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Las funciones declaradas con el atributo `naked` se emiten sin código de prólogo o epílogo, lo cual permite escribir secuencias personalizadas de prólogo\/epílogo mediante el [ensamblador alineado](../assembler/inline/inline-assembler.md).  Las funciones naked se proporcionan como una característica avanzada.  Permiten declarar una función que se está llamando desde un contexto que no es C\/C\+\+, y crear así diferentes suposiciones sobre dónde están los parámetros o qué registros se conservan.  Entre los posibles ejemplos, se encuentran rutinas tales como los controladores de interrupción.  Esta característica es especialmente útil para quienes escriben controladores de dispositivos virtuales \(VxD\).  
  
## ¿Qué más desea saber?  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Reglas y limitaciones de las funciones naked](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [Consideraciones para escribir código de prólogo\/epílogo](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
### FIN de Específicos de Microsoft  
  
## Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)