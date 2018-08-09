---
title: Trasladar de UNIX a Win32 | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], porting to Win32
- Windows API [C++], migrating from UNIX
- migration [C++]
- UNIX [C++], porting to Win32
- porting to Win32 [C++], from UNIX
- porting to Win32 [C++]
- Win32 applications [C++], migrating from UNIX
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08958de9f756ac005f966245e22a44afd7125bc0
ms.sourcegitcommit: 66f4f12d3851c897ca69cf62da1697e95b2b97c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39496680"
---
# <a name="porting-from-unix-to-win32"></a>Trasladar de UNIX a Win32
Al migrar aplicaciones de UNIX a Windows, dispone de varias opciones:  
  
-   Utilizar bibliotecas UNIX para migrar aplicaciones de UNIX a Win32  
  
-   Migrar aplicaciones de UNIX a Win32 de forma nativa  
  
-   Ejecutar aplicaciones UNIX en Windows mediante el subsistema POSIX  
  
## <a name="unix-libraries"></a>Bibliotecas de UNIX  
 Una opción que consideran normalmente los programadores de UNIX es usar bibliotecas de terceros similares a UNIX para que su código UNIX se pueda compilar como un ejecutable de Win32. Varias bibliotecas comerciales (y al menos un dominio público) permiten hacerlo. Esta opción es válida para algunas aplicaciones. La ventaja de estas bibliotecas de migración es que reducen al mínimo el trabajo de migración inicial. Su principal inconveniente, para un producto de software competitivo, es que una migración nativa a Win32 de una aplicación será, por lo general, más rápida e inevitablemente tendrá una mayor funcionalidad. Puede ser difícil para la aplicación salirse de su shell UNIX si necesita realizar llamadas de Win32 para obtener una mayor capacidad de Windows.  
  
 En la lista siguiente se proporciona recursos de Microsoft y de terceros para migrar y facilitar la migración de UNIX a Visual C++:  
  
### <a name="unix-migration-guides"></a>Guías de migración de UNIX  
 La [Guía de migración de aplicaciones UNIX personalizadas](https://technet.microsoft.com/library/bb656290.aspx) proporciona ayuda técnica sobre la migración de código del entorno de UNIX al de Win32.  
  
 La [Guía de migración de proyectos de UNIX](https://technet.microsoft.com/library/bb656287.aspx) complementa a la Guía de migración de aplicaciones UNIX personalizadas ofreciendo una ayuda de alto nivel sobre la migración de proyectos importantes de UNIX a Win32. La guía proporciona consejos sobre cuestiones a tener en cuenta en cada fase de la migración del proyecto.
  
### <a name="microsoft-windows-services-for-unix-sfu"></a>Microsoft Windows Services for UNIX (SFU)  
 Microsoft Windows Services for UNIX (SFU) proporciona una gama completa de servicios entre plataformas para integrar Windows en entornos existentes basados en UNIX. Services for UNIX proporciona uso compartido de archivos, acceso y administración remotos, sincronización de contraseña, administración de directorios comunes, un conjunto común de utilidades y un shell.  
  
 [Windows Services for UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)  
  
### <a name="interopsystemscom"></a>InteropSystems.com  
 [http://www.interopsystems.com/](http://www.interopsystems.com/)  
  
 Un sitio de terceros de una compañía que proporciona software para realizar migraciones de UNIX a Win32.  
  
### <a name="c-boost-web-site"></a>Sitio web de C++ Boost  
 [http://boost.sourceforge.net/regression-logs/](http://boost.sourceforge.net/regression-logs/)  
  
 [http://boost.sourceforge.net/boost-build2/](http://boost.sourceforge.net/boost-build2/)  
  
## <a name="porting-unix-applications-directly-to-win32"></a>Migración de aplicaciones UNIX directamente a Win32  
 Otra opción es migrar las aplicaciones UNIX directamente a Win32. Si se utilizan bibliotecas ANSI C/C ++ y bibliotecas comerciales de compiladores de C, muchas de las llamadas tradicionales al sistema utilizadas por las aplicaciones UNIX estarán disponibles en las aplicaciones de Win32.  
  
 El modelo de salida de aplicaciones basado en **stdio** no necesita modificarse, puesto que las API de consola de Win32 imitan el modelo de **stdio** y existen versiones de *curses* que usan las API de consola de Win32. Para más información, vea [SetConsoleCursorPosition](http://msdn.microsoft.com/library/windows/desktop/ms686025).  
  
 Las aplicaciones basadas en sockets de Berkeley apenas necesitan modificaciones para funcionar como aplicaciones Win32. La interfaz de Windows Sockets se diseñó para ofrecer portabilidad con sockets BSD, con un número mínimo de cambios que se indican en las secciones de introducción de la especificación WinSock.  
  
 Windows es compatible con RPC conforme con DCE, por lo que las aplicaciones basadas en RPC se pueden utilizar fácilmente. Vea [RPC Functions](http://msdn.microsoft.com/library/windows/desktop/aa378623) (Funciones RPC).  
  
 Las diferencias más importantes se encuentran en el modelo de proceso. UNIX tiene **fork** y Win32 no. Según el uso de **fork** y la base de código, Win32 cuenta con dos API que pueden usarse: **CreateProcess** y `CreateThread`. Una aplicación UNIX que bifurque varias copias de sí misma puede modificarse en Win32 de modo que tenga varios procesos o un solo proceso con varios subprocesos. Si se usan varios procesos, existen varios métodos de IPC que pueden emplearse para la comunicación entre procesos (y quizás para actualizar el código y los datos del nuevo proceso para que sean como el elemento primario, si es necesaria la funcionalidad que proporciona **fork**). Para más información sobre IPC, vea [Interprocess Communications](http://msdn.microsoft.com/library/windows/desktop/aa365574) (Comunicaciones entre procesos).  
  
 Los modelos gráficos de Windows y UNIX son muy diferentes. UNIX utiliza la GUI X Window System, mientras que Windows usa GDI. Aunque son similares en concepto, no hay ninguna asignación simple de la API de X a la API de GDI. Sin embargo, la compatibilidad con OpenGL está disponible para migrar aplicaciones basadas en OpenGL de UNIX. Y hay clientes X y servidores X para Windows. Vea [Contextos de dispositivo](http://msdn.microsoft.com/library/windows/desktop/dd183553) para más información sobre GDI.  
  
 Las aplicaciones UNIX básicas, incluidas numerosas aplicaciones CGI, deben migrarse fácilmente a Visual C++ que se ejecutan en Windows. Funciones como **open**, `fopen`, **read**, **write**, etc. están disponibles en la biblioteca en tiempo de ejecución de Visual C++. Además, hay una asignación unívoca entre las API de C UNIX y las API de Win32: **open** para **CreateFile**, **read** para **ReadFile**, **write** para **WriteFile**, `ioctl` para **DeviceIOControl**, **close** para **CloseFile**, etc.  
  
## <a name="windows-posix-subsystem"></a>Subsistema POSIX de Windows  
 Otra opción que contemplan los programadores de UNIX es el subsistema POSIX de Windows. Sin embargo, solo es compatible con POSIX 1003.1, que era la única versión POSIX estandarizada cuando se creó Windows NT. Desde entonces, ha habido poca demanda para extender este subsistema, porque la mayoría de las aplicaciones se han convertido a Win32. El sistema 1003.1 es de un interés limitado para las aplicaciones completas, ya que no incluye muchas funciones (como las de la versión 1003.2, con compatibilidad con redes, etc.). Las aplicaciones completas que se ejecutan bajo el subsistema POSIX de Windows no tienen acceso a las características de Windows disponibles para las aplicaciones de Win32, como archivos asignados a memoria, redes y gráficos. Las aplicaciones como VI, LS y GREP son los objetivos principales del subsistema POSIX de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Guía de migración y actualización de Visual C++](visual-cpp-change-history-2003-2015.md)   
 [UNIX](../c-runtime-library/unix.md)   
 [Reglas de inferencia](../build/inference-rules.md)