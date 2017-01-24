---
title: "Utilizar la versi&#243;n de depuraci&#243;n para comprobar si se ha sobrescrito la memoria | Microsoft Docs"
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
  - "memoria, sobrescrituras"
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Utilizar la versi&#243;n de depuraci&#243;n para comprobar si se ha sobrescrito la memoria
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si desea utilizar la versión de depuración para comprobar si se ha sobrescrito la memoria, primero debe recompilar el proyecto para depuración.  A continuación, vaya al principio de la función `InitInstance` de la aplicación y agregue la siguiente línea:  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 El asignador de memoria de depuración coloca bytes de protección para todas las asignaciones de memoria.  No obstante, estos bytes de protección no proporcionan ningún beneficio, a menos que se compruebe si han cambiado \(lo cual indicaría una sobrescritura en memoria\).  De lo contrario, sólo se dispondría de un búfer que podría, de hecho, permitirle seguir adelante con una sobrescritura en memoria.  
  
 Si activa `checkAlwaysMemDF`, forzará a MFC a hacer una llamada a la función `AfxCheckMemory` cada vez que se realice una llamada a **new** o **delete**.  Si se detectara una sobrescritura en memoria, se generaría un mensaje TRACE con un aspecto similar al siguiente:  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 Si recibe alguno de estos mensajes, deberá examinar el código para determinar dónde se produjo el daño.  Para determinar con mayor precisión dónde se produjo la sobrescritura en memoria, puede realizar llamadas explícitas a `AfxCheckMemory`.  Por ejemplo:  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 Si el primer ASSERT se realiza correctamente y el segundo no, significa que la sobrescritura en memoria debe haber ocurrido en la función entre las dos llamadas.  
  
 Según la naturaleza de la aplicación, puede encontrarse con que `afxMemDF` hace que el programa se ejecute muy lentamente, incluso para pruebas.  La variable `afxMemDF` hace que se llame a `AfxCheckMemory` para cada llamada a **new** y **delete**.  En ese caso, debería separar las llamadas a `AfxCheckMemory`\( \) como se indicó anteriormente y tratar de aislar la sobrescritura en memoria de ese modo.  
  
## Vea también  
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)