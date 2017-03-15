---
title: "Ejemplo de archivo MAKE para PCH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
ms.assetid: daf68983-77dc-45db-8701-aa89ad18910d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Ejemplo de archivo MAKE para PCH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El siguiente archivo MAKE utiliza macros y una estructura de comandos de control de flujo \!IF, \!ELSE, \!ENDIF para simplificar su adaptación al proyecto.  
  
```  
# Makefile : Illustrates the effective use of precompiled  
#            headers in a project  
# Usage:     NMAKE option  
# option:    DEBUG=[0|1]  
#            (DEBUG not defined is equivalent to DEBUG=0)  
#  
OBJS = myapp.obj applib.obj  
# List all stable header files in the STABLEHDRS macro.  
STABLEHDRS = stable.h another.h  
# List the final header file to be precompiled here:  
BOUNDRY = stable.h  
# List header files under development here:  
UNSTABLEHDRS = unstable.h  
# List all compiler options common to both debug and final  
# versions of your code here:  
CLFLAGS = /c /W3  
# List all linker options common to both debug and final  
# versions of your code here:  
LINKFLAGS = /NOD /ONERROR:NOEXE  
!IF "$(DEBUG)" == "1"  
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f  
LINKFLAGS = $(LINKFLAGS) /COD  
LIBS      = slibce  
!ELSE  
CLFLAGS   = $(CLFLAGS) /Oselg /Gs  
LINKFLAGS = $(LINKFLAGS)  
LIBS      = slibce  
!ENDIF  
myapp.exe: $(OBJS)  
    link $(LINKFLAGS) @<<  
$(OBJS), myapp, NUL, $(LIBS), NUL;  
<<  
# Compile myapp  
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp  
# Compile applib  
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp  
# Compile headers  
stable.pch : $(STABLEHDRS)  
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp  
```  
  
 Aparte de las macros STABLEHDRS, BOUNDRY y UNSTABLEHDRS mostradas en la ilustración "Estructura de un archivo MAKE que utiliza un encabezado precompilado" en [Archivos PCH en el proceso de compilación](../../build/reference/pch-files-in-the-build-process.md), este archivo MAKE incluye una macro CLFLAGS y una macro LINKFLAGS.  Estas macros se deben utilizar para indicar opciones del compilador y del vinculador que se aplican tanto para generar una versión de depuración como una versión final del archivo ejecutable de la aplicación.  También existe una macro LIBS en la que se indican las bibliotecas necesarias para el proyecto.  
  
 El archivo MAKE también utiliza \!IF, \!ELSE, \!ENDIF para detectar si se define un símbolo DEBUG en la línea de comandos de NMAKE:  
  
```  
NMAKE DEBUG=[1|0]  
```  
  
 Esta característica hace posible utilizar el mismo archivo MAKE durante el desarrollo y para las versiones finales del programa \(use DEBUG\=0 para las versiones finales\).  Las siguientes líneas de comandos son equivalentes:  
  
```  
NMAKE   
NMAKE DEBUG=0  
```  
  
 Para obtener más información acerca de los archivos MAKE, vea [Referencia de NMAKE](../../build/nmake-reference.md).  Vea también [Opciones del compilador](../../build/reference/compiler-options.md) y [Opciones del vinculador](../../build/reference/linker-options.md).  
  
## Vea también  
 [Utilizar encabezados precompilados en un proyecto](../../build/reference/using-precompiled-headers-in-a-project.md)