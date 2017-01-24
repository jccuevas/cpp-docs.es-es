---
title: "raise | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "raise"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "Raise"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "programas [C++], enviar señales a programas en ejecución"
  - "raise (función)"
  - "señales"
  - "señales, enviar a programas en ejecución"
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raise
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Envía una señal al programa en ejecución.  
  
> [!NOTE]
>  No use este método para cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], salvo en escenarios de prueba o depuración.  Las formas de cerrar mediante programación o con la interfaz de usuario una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] no se permiten según la Sección 3.6 de los [Requisitos de certificación para una aplicación de Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889).  Para obtener más información, vea [Ciclo de vida de la aplicación \(aplicaciones de la Tienda Windows\)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## Sintaxis  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### Parámetros  
 *sig*  
 Señal que se va a producir.  
  
## Valor devuelto  
 Si se ejecuta correctamente, **raise** devuelve 0.  De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 La función **raise** envía *sig* al programa en ejecución.  Si una llamada anterior a **signal** ha instalado una función de control de señales para *sig*, **raise** ejecuta esa función.  Si no se ha instalado ninguna función de controlador, se realiza la acción predeterminada asociada al valor de señal *sig*, como se indica a continuación.  
  
|Señal|Significado|Valor|  
|-----------|-----------------|-----------|  
|`SIGABRT`|Terminación anómala|Finaliza el programa de llamada con el código de salida 3|  
|`SIGFPE`|Error de punto flotante|Finaliza el programa de llamada|  
|`SIGILL`|Instrucción no válida|Finaliza el programa de llamada|  
|`SIGINT`|Interrupción de CTRL\+C|Finaliza el programa de llamada|  
|`SIGSEGV`|Acceso no válido a almacenamiento|Finaliza el programa de llamada|  
|`SIGTERM`|Solicitud de finalización enviada al programa|Omite la señal|  
  
 Si el argumento no es una señal válida según lo especificado anteriormente, se invoca el controlador de parámetros no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si no es controlada, la función establece `errno` en `EINVAL` y devuelve un valor distinto de cero.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**raise**|\<signal.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [signal](../../c-runtime-library/reference/signal.md)