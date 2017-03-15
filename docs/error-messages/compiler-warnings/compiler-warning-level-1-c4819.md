---
title: "Advertencia del compilador (nivel 1) C4819 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4819"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4819"
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4819
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El archivo contiene un carácter que no se puede representar en la página de códigos actual \(número\).Guarde el archivo en formato Unicode para evitar la pérdida de datos.  
  
 C4819 se produce cuando un archivo de código fuente ANSI se compila en un sistema con una página de códigos que no puede representar todos los caracteres del archivo.  
  
 Para resolver C4819, guarde el archivo en formato Unicode.  En Visual Studio, elija **Archivo**, **Opciones avanzadas para guardar**.  En el cuadro de diálogo **Opciones avanzadas para guardar** seleccione una codificación que pueda representar todos los caracteres del archivo \(por ejemplo, UTF\-8\) y, a continuación, elija **Aceptar**.