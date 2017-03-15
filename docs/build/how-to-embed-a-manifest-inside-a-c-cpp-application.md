---
title: "C&#243;mo: Incrustar un manifiesto en una aplicaci&#243;n de C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "incrustar manifiestos"
  - "Make (archivos), actualizar para incrustar manifiestos"
  - "manifiestos [C++]"
ms.assetid: ec0bac69-2fdc-466c-ab0d-710a22974e5d
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Incrustar un manifiesto en una aplicaci&#243;n de C/C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se recomienda que una aplicación de C\/C\+\+ \(o biblioteca\) tenga su manifiesto incrustado dentro del archivo binario final, ya que así se garantiza un comportamiento correcto en tiempo de ejecución en la mayoría de los escenarios.  De forma predeterminada, [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] intenta incrustar el manifiesto cuando compila un proyecto a partir de archivos de código fuente; vea [Generación de manifiestos en Visual Studio](../build/manifest-generation-in-visual-studio.md) para obtener más información.  Sin embargo, si una aplicación se compila utilizando nmake, será necesario realizar algunos cambios en el archivo make existente.  En esta sección se muestra cómo cambiar los archivos make existentes para incrustar automáticamente el manifiesto dentro del archivo binario final.  
  
## Dos enfoques  
 Existen dos formas de incrustar el manifiesto dentro de una aplicación o biblioteca.  
  
-   Si no está realizando una compilación incremental, puede incrustar directamente el manifiesto utilizando una línea de comandos similar a la siguiente como paso posterior a la compilación:  
  
     **mt.exe –manifest MyApp.exe.manifest \-outputresource:MyApp.exe;1**  
  
     \-O bien\-  
  
     **mt.exe –manifest MyLibrary.dll.manifest \-outputresource:MyLibrary.dll;2**  
  
     \(1 para un archivo EXE, 2 para un archivo DLL.\)  
  
-   Si está realizando una compilación incremental, al editar el recurso directamente tal como se muestra aquí, se deshabilitará la compilación incremental y se recompilará completamente; por lo tanto, es necesario adoptar un enfoque diferente:  
  
    -   Vincule el archivo binario para generar el archivo MyApp.exe.manifest.  
  
    -   Convierta el manifiesto en un archivo de recursos.  
  
    -   Vuelva a realizar una vinculación \(incremental\) para incrustar el recurso del manifiesto en el archivo binario.  
  
 En los siguientes ejemplos se muestra cómo modificar los archivos MAKE para incorporar ambas técnicas.  
  
## Archivos MAKE \(antes\)  
 Considere el script nmake para MyApp.exe, una aplicación simple compilada a partir de un archivo:  
  
```  
# build MyApp.exe  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
```  
  
 Si este script se ejecuta tal como está mediante Visual C\+\+, creará correctamente MyApp.exe.  También crea el archivo de manifiesto externo MyApp.exe.manifest, que será utilizado por el sistema operativo durante la ejecución para cargar los ensamblados dependientes.  
  
 El script nmake para MyLibrary.dll presenta un aspecto muy similar:  
  
```  
# build MyLibrary.dll  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
```  
  
## Archivos MAKE \(después\)  
 Para poder compilar con manifiestos incrustados, es necesario realizar cuatro pequeños cambios en los archivos MAKE originales.  Para el archivo MAKE de MyApp.exe:  
  
```  
# build MyApp.exe  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_EXE)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 Para el archivo MAKE de MyLibrary.dll:  
  
```  
# build MyLibrary.dll  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_DLL)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2.  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3.  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 Los archivos MAKE incluyen ahora dos archivos \(makefile.inc y makefile.targ.inc\) que se encargan de realizar el trabajo real.  
  
 Cree el archivo makefile.inc y copie en el mismo lo siguiente:  
  
```  
# makefile.inc -- Include this file into existing makefile at the very top.  
  
# _VC_MANIFEST_INC specifies whether build is incremental (1 - incremental).  
# _VC_MANIFEST_BASENAME specifies name of a temporary resource file.  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
_VC_MANIFEST_INC=1  
_VC_MANIFEST_BASENAME=__VC90.Debug  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
_VC_MANIFEST_INC=0  
_VC_MANIFEST_BASENAME=__VC90  
  
!endif  
  
####################################################  
# Specifying name of temporary resource file used only in incremental builds:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
_VC_MANIFEST_AUTO_RES=$(_VC_MANIFEST_BASENAME).auto.res  
!else  
_VC_MANIFEST_AUTO_RES=  
!endif  
  
####################################################  
# _VC_MANIFEST_EMBED_EXE - command to embed manifest in EXE:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
#MT_SPECIAL_RETURN=1090650113  
#MT_SPECIAL_SWITCH=-notify_resource_update  
MT_SPECIAL_RETURN=0  
MT_SPECIAL_SWITCH=  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -out:$(_VC_MANIFEST_BASENAME).auto.manifest $(MT_SPECIAL_SWITCH) & \  
if "%ERRORLEVEL%" == "$(MT_SPECIAL_RETURN)" \  
rc /r $(_VC_MANIFEST_BASENAME).auto.rc & \  
link $** /out:$@ $(LFLAGS)  
  
!else  
  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -outputresource:$@;1  
  
!endif  
  
####################################################  
# _VC_MANIFEST_CLEAN - command to clean resources files generated temporarily:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
_VC_MANIFEST_CLEAN=-del $(_VC_MANIFEST_BASENAME).auto.res \  
    $(_VC_MANIFEST_BASENAME).auto.rc \  
    $(_VC_MANIFEST_BASENAME).auto.manifest  
  
!else  
  
_VC_MANIFEST_CLEAN=  
  
!endif  
  
# End of makefile.inc   
####################################################  
```  
  
 A continuación, cree el archivo makefile.targ.inc y copie en el mismo lo siguiente:  
  
```  
# makefile.targ.inc - include this at the very bottom of the existing makefile  
  
####################################################  
# Commands to generate initial empty manifest file and the RC file  
# that references it, and for generating the .res file:  
  
$(_VC_MANIFEST_BASENAME).auto.res : $(_VC_MANIFEST_BASENAME).auto.rc  
  
$(_VC_MANIFEST_BASENAME).auto.rc : $(_VC_MANIFEST_BASENAME).auto.manifest  
    type <<$@  
#include <winuser.h>  
1RT_MANIFEST"$(_VC_MANIFEST_BASENAME).auto.manifest"  
<< KEEP  
  
$(_VC_MANIFEST_BASENAME).auto.manifest :  
    type <<$@  
<?xml version='1.0' encoding='UTF-8' standalone='yes'?>  
<assembly xmlns='urn:schemas-microsoft-com:asm.v1' manifestVersion='1.0'>  
</assembly>  
<< KEEP  
  
# end of makefile.targ.inc  
```  
  
## Vea también  
 [Introducción a la generación de manifiestos para los programas de C\/C\+\+](../build/understanding-manifest-generation-for-c-cpp-programs.md)