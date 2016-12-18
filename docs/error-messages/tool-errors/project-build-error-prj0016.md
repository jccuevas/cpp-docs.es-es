---
title: "Error PRJ0016 al compilar el proyecto | Microsoft Docs"
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
  - "PRJ0016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0016"
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error PRJ0016 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La configuración de seguridad del usuario impide crear el proceso.Esta configuración es necesaria para la compilación.  
  
 Está registrado como un usuario que no tiene permisos para crear procesos mediante un proceso.  Debe cambiar los niveles de permiso para esta cuenta de usuario, o ponerse en contacto con el administrador de su cuenta.  
  
 Este error también se puede producir si se establece la clave del Registro siguiente:  
  
 \\\\HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Policies\\Explorer\\RestrictRun  
  
 Para corregir este error, elimine la clave RestrictRun.  Si la clave del Registro es necesaria, anexe **vcspawn.exe** a la lista de entradas de la clave.  
  
 Otra causa de este error es que la Configuración de directivas no incluye VCSpawn.exe en la clave del Registro HKEY\_CURRENT\_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\Policies\\RestrictRun como programa de Windows permitido para esta cuenta de usuario.  
  
 Para obtener información adicional, vea:  
  
-   Artículo 324153 de Knowledge Base, que está disponible en [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153).  
  
-   [Cumplir con la Configuración de directrices del sistema](http://msdn.microsoft.com/library/aa372139), la sección en "Ejecución sólo permitida en aplicaciones para Windows".