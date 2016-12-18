---
title: "Trasladar de UNIX a Win32 | Microsoft Docs"
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
  - "APIs [C++], porting to Win32"
  - "migration [C++]"
  - "porting to Win32 [C++]"
  - "porting to Win32 [C++], from UNIX"
  - "UNIX [C++], porting to Win32"
  - "Win32 applications [C++], migrating from UNIX"
  - "Windows API [C++], migrating from UNIX"
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Trasladar de UNIX a Win32
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al migrar aplicaciones de UNIX a Windows, dispone de varias opciones:  
  
-   Utilizar bibliotecas UNIX para migrar aplicaciones de UNIX a Win32  
  
-   Migrar aplicaciones de UNIX a Win32 de forma nativa  
  
-   Ejecutar aplicaciones UNIX en Windows mediante el subsistema POSIX  
  
## Bibliotecas de UNIX  
 Una opción que consideran normalmente los programadores de UNIX es usar bibliotecas de terceros similares a UNIX para que su código UNIX se pueda compilar como un ejecutable de Win32.  Varias bibliotecas comerciales \(y al menos un dominio público\) permiten hacerlo.  Esta opción es válida para algunas aplicaciones.  La ventaja de estas bibliotecas de migración es que reducen al mínimo el trabajo de migración inicial.  Su principal inconveniente, para un producto de software competitivo, es que una migración nativa a Win32 de una aplicación será, por lo general, más rápida e inevitablemente tendrá una mayor funcionalidad.  Puede ser difícil para la aplicación salirse de su shell UNIX si necesita realizar llamadas de Win32 para obtener una mayor capacidad de Windows.  
  
 En la lista siguiente se proporciona recursos de Microsoft y de terceros para migrar y facilitar la migración de UNIX a Visual C\+\+:  
  
### Guías de migración de UNIX  
 La Guía de migración de aplicaciones UNIX personalizadas proporciona ayuda técnica sobre la migración de código del entorno de UNIX al de Win32.  
  
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=95428](http://go.microsoft.com/fwlink/?LinkId=95428)  
  
 La Guía de migración de proyectos de UNIX complementa a la Guía de migración de aplicaciones UNIX personalizadas ofreciendo una ayuda de alto nivel sobre la migración de proyectos importantes de UNIX a Win32.  La guía proporciona consejos sobre cuestiones a tener en cuenta en cada fase de la migración del proyecto.  La guía se puede descargar desde:  
  
 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=20012](http://go.microsoft.com/fwlink/?linkid=20012)  
  
### Microsoft Windows Services for UNIX \(SFU\)  
 Microsoft Windows Services for UNIX \(SFU\) proporciona una gama completa de servicios entre plataformas para integrar Windows en entornos existentes basados en UNIX.  Services for UNIX proporciona uso compartido de archivos, acceso y administración remotos, sincronización de contraseña, administración de directorios comunes, un conjunto común de utilidades y un shell.  
  
 [Windows Services for UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)  
  
### InteropSystems.com  
 [http:\/\/www.interopsystems.com\/](http://www.interopsystems.com/)  
  
 Un sitio de terceros de una compañía que proporciona software para realizar migraciones de UNIX a Win32.  
  
### Sitio web de C\+\+ Boost  
 [http:\/\/boost.sourceforge.net\/regression\-logs\/](http://boost.sourceforge.net/regression-logs/)  
  
 [http:\/\/boost.sourceforge.net\/boost\-build2\/](http://boost.sourceforge.net/boost-build2/)  
  
## Migración de aplicaciones UNIX directamente a Win32  
 Otra opción es migrar las aplicaciones UNIX directamente a Win32.  Si se utilizan bibliotecas ANSI C\/C \+\+ y bibliotecas comerciales de compiladores de C, muchas de las llamadas tradicionales al sistema utilizadas por las aplicaciones UNIX estarán disponibles en las aplicaciones de Win32.  
  
 El modelo de salida de aplicaciones basadas en **stdio** no deben cambiarse, puesto que las API de consola de Win32 imitan el modelo de **stdio** y existen versiones de *curses* que usan las API de consola de Win32.  Para obtener más información, vea [SetConsoleCursorPosition](http://msdn.microsoft.com/library/windows/desktop/ms686025).  
  
 Las aplicaciones basadas en sockets de Berkeley apenas necesitan modificaciones para funcionar como aplicaciones Win32.  La interfaz de Windows Sockets se diseñó para ofrecer portabilidad con sockets BSD, con un número mínimo de cambios que se indican en las secciones de introducción de la especificación WinSock.  
  
 Windows es compatible con RPC conforme con DCE, por lo que las aplicaciones basadas en RPC se pueden utilizar fácilmente.  Vea [Funciones de RPC](http://msdn.microsoft.com/library/windows/desktop/aa378623).  
  
 Las diferencias más importantes se encuentran en el modelo de proceso.  UNIX tiene **fork** y Win32 no.  Dependiendo del uso de **fork** y la base de código, Win32 cuenta con dos API que pueden utilizarse: **CreateProcess** y `CreateThread`.  Una aplicación UNIX que bifurque varias copias de sí misma puede modificarse en Win32 de modo que tenga varios procesos o un solo proceso con varios subprocesos.  Si se usan varios procesos, existen varios métodos de IPC que pueden utilizarse para la comunicación entre procesos \(y quizás para actualizar el código y los datos del nuevo proceso para que sean como el elemento primario, si es necesaria la funcionalidad que proporciona **fork**\).  Para obtener más información sobre IPC, vea [Comunicaciones entre procesos](http://msdn.microsoft.com/library/windows/desktop/aa365574).  
  
 Los modelos gráficos de Windows y UNIX son muy diferentes.  UNIX utiliza la GUI X Window System, mientras que Windows usa GDI.  Aunque son similares en concepto, no hay ninguna asignación simple de la API de X a la API de GDI.  Sin embargo, la compatibilidad con OpenGL está disponible para migrar aplicaciones basadas en OpenGL de UNIX.  Y hay clientes X y servidores X para Windows.  Vea [Contextos de dispositivo](http://msdn.microsoft.com/library/windows/desktop/dd183553) para obtener información sobre GDI.  
  
 Las aplicaciones UNIX básicas, incluidas numerosas aplicaciones CGI, deben migrarse fácilmente a Visual C\+\+ que se ejecutan en Windows.  Funciones como **open**, `fopen`, **read**, **write** y otras están disponibles en la biblioteca de tiempo de ejecución de Visual C\+\+.  Además, hay una asignación unívoca entre las API de C UNIX y las API de Win32: **open** a **CreateFile**, **read** a **ReadFile**, **write** a **WriteFile**, `ioctl` a **DeviceIOControl**, **close** a **CloseFile**, y así sucesivamente.  
  
## Subsistema POSIX de Windows  
 Otra opción que contemplan los programadores de UNIX es el subsistema POSIX de Windows.  Sin embargo, solo es compatible con POSIX 1003.1, que era la única versión POSIX estandarizada cuando se creó Windows NT.  Desde entonces, ha habido poca demanda para extender este subsistema, porque la mayoría de las aplicaciones se han convertido a Win32.  El sistema 1003.1 es de un interés limitado para las aplicaciones completas, ya que no incluye muchas funciones \(como las de la versión 1003.2, con compatibilidad con redes, etc.\).  Las aplicaciones completas que se ejecutan bajo el subsistema POSIX de Windows no tienen acceso a las características de Windows disponibles para las aplicaciones de Win32, como archivos asignados a memoria, redes y gráficos.  Las aplicaciones como VI, LS y GREP son los objetivos principales del subsistema POSIX de Windows.  
  
## Vea también  
 [Migrar programas](http://msdn.microsoft.com/es-es/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)   
 [UNIX](../c-runtime-library/unix.md)   
 [Reglas de inferencia](../build/inference-rules.md)