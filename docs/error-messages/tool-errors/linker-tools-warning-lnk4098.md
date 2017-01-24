---
title: "Advertencia de las herramientas del vinculador LNK4098 | Microsoft Docs"
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
  - "LNK4098"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4098"
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4098
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la biblioteca predeterminada 'biblioteca' está en conflicto con otras bibliotecas; use la biblioteca \/NODEFAULTLIB:biblioteca  
  
 Intenta vincular con bibliotecas incompatibles entre sí.  
  
> [!NOTE]
>  Ahora, las bibliotecas en tiempo de ejecución contienen directivas para impedir que se mezclen tipos distintos.  Recibirá esta advertencia si intenta usar tipos diferentes o versiones de depuración y no de depuración de la biblioteca en tiempo de ejecución en un mismo programa.  Por ejemplo, si compila un archivo para que utilice un tipo de biblioteca en tiempo de ejecución y otro archivo para que utilice otra biblioteca diferente \(por ejemplo, único subproceso y multiproceso\) e intenta vincularlos, recibirá esta advertencia.  Se deben compilar todos los archivos de código fuente para que utilicen la misma biblioteca en tiempo de ejecución.  Para obtener más información, vea las opciones del compilador [Utilizar la biblioteca en tiempo de ejecución](../../build/reference/md-mt-ld-use-run-time-library.md) \(**\/MD**, **\/MT**, **\/LD**\).  
  
 Se puede usar el modificador [\/VERBOSE:LIB](../../build/reference/verbose-print-progress-messages.md) del vinculador para determinar en qué bibliotecas busca el vinculador.  Si recibe la advertencia LNK4098 y desea crear un archivo ejecutable que utilice, por ejemplo, bibliotecas en tiempo de ejecución de un único subproceso de no depuración, puede utilizar la opción **\/VERBOSE:LIB** para averiguar en qué bibliotecas busca el vinculador.  El vinculador debe mostrar LIBC.lib y no T.lib, MSVCRT.lib, LIBCD.lib, LIBCMTD.lib o MSVCRTD.lib como bibliotecas de su búsqueda.  Se puede indicar al vinculador que omita las bibliotecas en tiempo de ejecución incorrectas mediante la opción [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) para cada biblioteca que se desee omitir.  
  
 La tabla siguiente muestra qué bibliotecas deben omitirse según la biblioteca en tiempo de ejecución que se desee usar.  
  
|Para usar esta biblioteca en tiempo de ejecución|Omita estas bibliotecas|  
|------------------------------------------------------|-----------------------------|  
|De un único subproceso \(libc.lib\)|libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|De multiproceso \(libcmt.lib\)|libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|De multiproceso con DLL \(msvcrt.lib\)|libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|De un único subproceso de depuración \(libcd.lib\)|libc.lib, libcmt.lib, msvcrt.lib, libcmtd.lib, msvcrtd.lib|  
|De multiproceso de depuración \(libcmtd.lib\)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, msvcrtd.lib|  
|De multiproceso con DLL de depuración \(msvcrtd.lib\)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|  
  
 Por ejemplo, si recibe esta advertencia y desea crear un archivo ejecutable que utilice la versión no de depuración y de un único subproceso de las bibliotecas en tiempo de ejecución, puede utilizar las siguientes opciones con el vinculador:  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```