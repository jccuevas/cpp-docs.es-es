---
title: "Error PRJ0050 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0050"
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error PRJ0050 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Error al registrar el resultado.Compruebe que dispone de los permisos necesarios para modificar el Registro.  
  
 El sistema de compilación de Visual C\+\+ no pudo registrar el resultado de la compilación \(dll o .exe\).  Debe haber iniciado una sesión como administrador para modificar el Registro.  
  
 Si compila un archivo .dll, puede intentar registrarlo manualmente mediante regsvr32.exe. De este modo, debería aparecer información sobre el motivo del error de compilación.  
  
 Si no compila un archivo .dll, busque en el registro de compilación el comando que origine el error.