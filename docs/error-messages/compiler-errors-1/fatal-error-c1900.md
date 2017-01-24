---
title: "Error irrecuperable C1900 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1900"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1900"
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1900
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Il 'tool1', versión 'number1', no coincide con 'tool2', versión 'number2'  
  
 Las herramientas ejecutadas en varias transferencias del compilador no coinciden.  ***number1*** y ***number2*** hacen referencia a las fechas de los archivos.  Por ejemplo, en la transferencia 1, el front\-end del compilador ejecuta \(c1.dll\) y, en la transferencia 2, el back\-end del compilador ejecuta \(c2.dll\).  Las fechas de los archivos deben coincidir.  
  
 Para corregir este problema, asegúrese de que se han aplicado todas las actualizaciones a Visual Studio.  Si el problema persiste, utilice **Programas y características** del Panel de control de Windows para reparar o reinstalar Visual Studio.