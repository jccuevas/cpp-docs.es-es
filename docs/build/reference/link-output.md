---
title: "Resultados de LINK | Microsoft Docs"
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
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ilk (archivos)"
  - "DLL [C++], como resultado del vinculador"
  - "archivos ejecutables [C++], como resultado del vinculador"
  - "archivos [C++], LINK"
  - "ILK (archivos)"
  - "bibliotecas de importación [C++], crear"
  - "LINK (herramienta) [C++], archivo de asignaciones"
  - "LINK (herramienta) [C++], resultado"
  - "vinculador [C++], archivos de salida"
  - "archivos de asignaciones [C++]"
  - "archivos de asignaciones [C++], resultados de LINK"
  - "archivos de resultados [C++], vinculador"
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Resultados de LINK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Link puede dar como resultado archivos .exe, DLL, archivos de asignaciones y mensajes.  
  
##  <a name="_core_output_files"></a> Archivos de resultados  
 El archivo de salida predeterminado de LINK es un archivo .exe.  Si se especifica la opción [\/DLL](../../build/reference/dll-build-a-dll.md), LINK compilará un archivo .dll.  Se puede elegir el nombre del archivo de salida mediante la opción [\/OUT \(Nombre del archivo de salida\)](../../build/reference/out-output-file-name.md).  
  
 En modo incremental, LINK crea un archivo .ilk que contiene información de estado para posteriores compilaciones incrementales del programa.  Para obtener información detallada acerca de los archivos .ilk, vea [Archivos .ilk](../../build/reference/dot-ilk-files-as-linker-input.md).  Para obtener más información acerca de la vinculación incremental, vea la opción [\/INCREMENTAL \(Vincular de forma incremental\)](../../build/reference/incremental-link-incrementally.md).  
  
 Cuando LINK crea un programa con exportaciones \(normalmente una DLL\), compila además un archivo .lib \(siempre que no se haya utilizado un archivo .exp en la compilación\).  Se puede elegir el nombre de archivo de la biblioteca de importación mediante la opción [\/IMPLIB](../../build/reference/implib-name-import-library.md).  
  
 Si se especifica la opción [\/MAP \(Generar archivo de asignaciones\)](../../build/reference/map-generate-mapfile.md), LINK creará un archivo de asignaciones.  
  
 Si se especifica la opción [\/DEBUG \(Generar información de depuración\)](../../build/reference/debug-generate-debug-info.md), LINK creará una PDB para contener la información de depuración del programa.  
  
##  <a name="_core_other_output"></a> Otros resultados  
 Si en la línea de comandos sólo se escribe la entrada `link`, LINK muestra una instrucción de uso en la que se resumen sus distintas opciones.  
  
 A no ser que se use la opción [\/NOLOGO \(Suprimir la pancarta de inicio\)](../../build/reference/nologo-suppress-startup-banner-linker.md), LINK mostrará un mensaje con información de copyright y de versión, y repetirá la entrada de la línea de comandos.  
  
 Se puede usar la opción [\/VERBOSE \(Imprimir mensajes de progreso\)](../../build/reference/verbose-print-progress-messages.md) para mostrar información más detallada acerca de la compilación.  
  
 LINK emite los mensajes de error y de advertencia en el formato LNK*nnnn*.  LIB, DUMPBIN y EDITBIN también utilizan ese prefijo de error y rango de números.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)