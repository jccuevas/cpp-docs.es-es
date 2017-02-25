---
title: "Tipos de archivos DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], MFC"
  - "DLL [C++], tipos"
  - "DLL de MFC [C++], tipos"
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Tipos de archivos DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se proporciona información que le ayudará a determinar el tipo de archivo DLL que debe compilar.  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Los distintos tipos de archivo DLL disponibles  
 Mediante Visual C\+\+, puede compilar archivos DLL para Win32 \(en C o C\+\+\) que no utilicen la biblioteca MFC \(Microsoft Foundation Class\).  Puede crear un proyecto de archivo DLL no basado en MFC con el Asistente para aplicaciones Win32.  
  
 La misma biblioteca MFC está disponible, tanto en bibliotecas de vínculos estáticos como en varios archivos DLL, con el Asistente para archivos DLL de MFC.  Si el archivo DLL utiliza MFC, Visual C\+\+ proporciona tres niveles distintos de desarrollo del archivo DLL:  
  
-   Compilar un archivo DLL estándar que se vincule a MFC de forma estática  
  
-   Compilar un archivo DLL estándar que se vincule a MFC de forma dinámica  
  
-   Compilar un archivo DLL de extensión de MFC que siempre se vincule a MFC de forma dinámica  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Archivos DLL que no están basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión: información general](../build/extension-dlls-overview.md)  
  
-   [Determinar el tipo de archivo DLL que se debe utilizar](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a> Determinar el tipo de archivo DLL que se debe utilizar  
 Si el archivo DLL no utiliza la biblioteca MFC, utilice Visual C\+\+ para generar un archivo DLL para Win32 que no esté basado en MFC.  La vinculación del archivo DLL a MFC \(ya sea estática o dinámica\) ocupa mucha memoria y mucho espacio en disco.  No debe vincular el archivo DLL a MFC a menos que realmente vaya a utilizar las funciones de MFC.  
  
 Si el archivo DLL va a utilizar las funciones de MFC y dicho archivo se va a utilizar en aplicaciones MFC y en aplicaciones que no están basadas en MFC, deberá generar un archivo DLL estándar que se vincule dinámicamente a MFC o un archivo DLL estándar que se vincule estáticamente a MFC.  En la mayoría de los casos, probablemente le interese utilizar un archivo DLL estándar que se vincule dinámicamente a MFC, puesto que su tamaño de archivo será mucho menor y el ahorro de memoria derivado de utilizar la versión compartida de MFC puede ser importante.  Si vincula estáticamente el archivo DLL a MFC, su tamaño de archivo será mayor y posiblemente ocupará memoria adicional, ya que cargará su propia copia privada del código de la biblioteca MFC.  
  
 Es más rápido compilar un archivo DLL que se vincule dinámicamente a MFC que compilar un archivo DLL que lo haga estáticamente, ya que en el primer caso no es necesario vincular MFC.  Esto se cumple, sobre todo, en las versiones de depuración en las que el vinculador debe compactar la información de depuración.  Al vincular a un archivo DLL que ya contiene la información de depuración, habrá que compactar menos información de depuración en el archivo DLL.  
  
 Una desventaja de la vinculación dinámica a MFC es que supone distribuir con el archivo DLL los archivos DLL compartidos Mfcx0.dll y Msvcrxx.dll \(o archivos similares\).  Los archivos DLL de MFC se pueden redistribuir libremente, pero tendrá que instalarlos mediante el programa de instalación.  Además, deberá distribuir el archivo Msvcrxx.dll, que contiene la biblioteca en tiempo de ejecución de C que el programa y los archivos DLL de MFC utilizan.  
  
 Si el archivo DLL sólo se utiliza en ejecutables MFC, podrá elegir entre compilar un archivo DLL estándar o un archivo DLL de extensión.  Si el archivo DLL implementa clases reutilizables derivadas de clases MFC existentes o si tiene que transferir objetos derivados de MFC entre la aplicación y el archivo DLL, deberá compilar un archivo DLL de extensión.  
  
 Si el archivo se vincula dinámicamente a MFC, podrá redistribuir los archivos DLL de MFC con su archivo DLL.  Esta arquitectura resulta especialmente útil para compartir la biblioteca de clases entre varios archivos ejecutables a fin de ahorrar espacio en disco y minimizar el uso de la memoria.  
  
 Antes de la versión 4.0, Visual C\+\+ sólo admitía dos tipos de archivos DLL que utilizaban MFC: USRDLL y AFXDLL.  Los archivos DLL estándar vinculados estáticamente a MFC tienen las mismas características que el archivo USRDLL anterior.  Los archivos DLL de extensión de MFC tienen las mismas características que los archivos AFXDLL antiguos.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Archivos DLL que no están basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión: información general](../build/extension-dlls-overview.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)