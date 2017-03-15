---
title: "Entrada y salida | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "E/S [CRT]"
  - "E/S [CRT], rutinas"
  - "E/S (rutinas)"
  - "rutinas de entrada"
  - "rutinas de salida"
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Entrada y salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

E\/S funciona leer y escribir datos a y desde los archivos y los dispositivos.  Operaciones de E\/S de archivos tienen lugar en modo de texto o modo binario.  La biblioteca en tiempo de ejecución de Microsoft tiene tres tipos de funciones de E\/S:  
  
-   datos de una llamada de las funciones de[E\/S de la secuencia](../c-runtime-library/stream-i-o.md) como una secuencia de caracteres individuales.  
  
-   las funciones de[E\/S de bajo nivel](../c-runtime-library/low-level-i-o.md) invocan el sistema operativo directamente para la operación de nivel inferior que lo proporcionada por E\/S de secuencia.  
  
-   [E\/S de la consola y de puerto](../c-runtime-library/console-and-port-i-o.md) funciona leer o escribir directamente en una consola \(teclado y mostrar\) o a un puerto de E\/S \(como un puerto de impresora\).  
  
    > [!NOTE]
    >  Dado que se almacenan en búfer funciones de secuencia y no son funciones de bajo nivel, estos dos tipos de funciones normalmente son incompatibles.  Para procesar un archivo concreto, utilice exclusivamente transmitirs o de bajo nivel funciones.  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)