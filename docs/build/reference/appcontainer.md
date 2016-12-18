---
title: "/APPCONTAINER | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/APPCONTAINER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/APPCONTAINER editbin (opción)"
  - "APPCONTAINER editbin (opción)"
  - "-APPCONTAINER editbin (opción)"
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /APPCONTAINER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marca un ejecutable que se debe ejecutar en un contenedor de la aplicación; por ejemplo, una [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] o una aplicación universal de Windows.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## Comentarios  
 Un ejecutable que tiene establecida la opción **\/APPCONTAINER** solo puede ejecutarse en un contenedor de la aplicación, que es el entorno de aislamiento del proceso que se introdujo en Windows 8. Para [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] y las aplicaciones universales de Windows, se debe establecer esta opción.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [¿Qué es una aplicación de universal Windows?](http://go.microsoft.com/fwlink/p/?LinkID=522074)