---
title: "/errorReport (Informar de los errores del compilador) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.ErrorReporting"
  - "/errorreport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/errorReport (opción del compilador) [C++]"
  - "-errorReport (opción del compilador) [C++]"
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /errorReport (Informar de los errores del compilador)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite proporcionar directamente a Microsoft la información sobre el error interno del compilador.  
  
## Sintaxis  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## Argumentos  
 **none**  
 No se recopilarán informes sobre errores internos del compilador ni se enviarán a Microsoft.  
  
 **prompt**  
 Pregunta si desea enviar un informe cuando recibe un error interno del compilador.  **prompt** es el valor predeterminado cuando una aplicación está compilada en un entorno de desarrollo.  
  
 **queue**  
 Pone en cola el informe de errores.  Cuando inicia una sesión con privilegios de administrador, aparece una ventana para que pueda informar de todos los errores desde la última vez que inició una sesión \(se le pedirá que envíe informes de errores como máximo una vez cada tres días\).  **queue** es el valor predeterminado cuando una aplicación está compilada en un símbolo del sistema.  
  
 **send**  
 Envía automáticamente los informes de errores internos del compilador a Microsoft.  Para habilitar esta opción, primero debe aceptar la directiva de recolección de datos de Microsoft.  La primera vez que especifique **\/errorReport:send** en un equipo, un mensaje del compilador le remitirá a un sitio web que contiene la directiva de recolección de datos de Microsoft.  
  
 Esta opción depende de la configuración del Registro.  Para obtener información sobre cómo establecer los valores adecuados en el registro, vea [Cómo activar el informe de errores automático en Visual Studio 2008 herramientas de línea de comandos](http://go.microsoft.com/fwlink/?LinkID=184695) en el sitio web de MSDN.  
  
## Comentarios  
 Un error interno del compilador \(ICE\) se produce cuando el compilador no puede procesar un archivo de código fuente.  Cuando aparece un ICE, el compilador no genera un archivo de salida ni otro tipo de diagnóstico útil que pueda utilizar para corregir el código.  
  
 En versiones anteriores, cuando el usuario recibía un error ICE, se le solicitaba que llamara a los servicios de soporte técnico de Microsoft para notificar el problema.  Con **\/errorReport**, puede proporcionar información de los ICE directamente a Microsoft.  Sus informes de errores pueden ayudar a mejorar las futuras versiones del compilador.  
  
 La capacidad de un usuario para enviar informes depende del equipo y de los permisos de la directiva del usuario.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Informes de errores**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)