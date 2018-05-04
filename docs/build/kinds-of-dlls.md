---
title: Tipos de archivos DLL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 605d60535df8d0a94d58e120df89f975402b8a22
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="kinds-of-dlls"></a>Tipos de archivos DLL
Este tema proporciona información para ayudarle a determinar el tipo de archivo DLL para compilar.  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Diferentes tipos de archivos DLL disponibles  
 Mediante Visual C++, puede generar archivos DLL para Win32 de C o C++ que no utilizan la biblioteca (Microsoft Foundation Classes). Puede crear un proyecto DLL que no son de MFC con el Asistente para aplicaciones de Win32.  
  
 La propia biblioteca MFC está disponible, en cualquier bibliotecas de vínculos estáticos o en un número de archivos DLL, con el Asistente para archivos DLL de MFC. Si el archivo DLL utiliza MFC, Visual C++ admite tres escenarios diferentes de desarrollo de DLL:  
  
-   Generar a una DLL de MFC normal estáticamente vincule a MFC  
  
-   Generar a una DLL de MFC normal dinámicamente vincule a MFC  
  
-   Creación de un archivo DLL de extensión MFC, que siempre vincular dinámicamente MFC  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Archivos DLL no basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL de MFC estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL de MFC estándar vinculado dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión MFC: información general](../build/extension-dlls-overview.md)  
  
-   [Qué tipo de archivo DLL para usar](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a> Decidir qué tipo de DLL que se utilizan  
 Si el archivo DLL no usa MFC, utilice Visual C++ para generar un archivo DLL para Win32 que no basado en MFC. Vincular al archivo DLL a MFC (estática o dinámicamente) ocupa mucha memoria y mucho espacio en disco. No debe vincularse a MFC a menos que el archivo DLL realmente utiliza MFC.  
  
 Si el archivo DLL va a utilizar MFC y se usará en las aplicaciones MFC o no están basados en MFC, deberá generar una DLL de MFC normal que se vincula dinámicamente a MFC o una DLL de MFC normal que se vincula estáticamente a MFC. En la mayoría de los casos, probablemente desee usar una DLL de MFC normal que se vincula dinámicamente a MFC, porque el tamaño de archivo del archivo DLL será mucho menor y el ahorro de memoria derivado de utilizar la versión compartida de MFC puede ser importante. Si se vinculan estáticamente a MFC, el tamaño de archivo del archivo DLL se ser mayor y posiblemente ocupará memoria adicional, ya que cargará su propia copia privada del código de biblioteca MFC.  
  
 Generar un archivo DLL que se vincule dinámicamente a MFC es más rápido que generar un archivo DLL que se vincula estáticamente a MFC ya no es necesario vincular MFC. Esto es especialmente cierto en las compilaciones de depuración que el vinculador debe compactar la información de depuración. Al vincular con un archivo DLL que ya contiene la información de depuración, hay menos información de depuración para compactar dentro de su archivo DLL.  
  
 Una desventaja de que se vincula dinámicamente a MFC es que debe distribuir los archivos DLL compartidos Mfcx0.dll y el archivo Msvcrxx.dll (o archivos similares) con el archivo DLL. Los archivos DLL de MFC son puede redistribuir libremente, pero todavía debe instalar los archivos DLL en el programa de instalación. Además, debe distribuir el archivo de Msvcrxx.dll, que contiene la biblioteca de tiempo de ejecución de C que se está usando el programa y los mismos archivos DLL de MFC.  
  
 Si solo se usará el archivo DLL mediante archivos ejecutables MFC, tendrá que elegir entre crear una DLL de MFC normal o un archivo DLL de extensión MFC. Si el archivo DLL implementa clases reutilizables derivadas de las clases MFC existentes o si necesita pasar objetos derivados de MFC entre la aplicación y el archivo DLL, deberá generar un archivo DLL de extensión MFC.  
  
 Si el archivo DLL se vincula dinámicamente a MFC, puede redistribuir los archivos DLL de MFC con su archivo DLL. Esta arquitectura es especialmente útil para compartir la biblioteca de clases entre varios archivos ejecutables para ahorrar espacio en disco y minimizar el uso de memoria.  
  
 Antes de la versión 4.0, tipos de Visual C++ sólo admitía dos de los archivos DLL que utilizaban MFC: USRDLL y AFXDLL. Archivos DLL de MFC estándar vinculados estáticamente a MFC tienen las mismas características que el antiguo archivo USRDLL. Archivos DLL de extensión MFC tienen las mismas características que los archivos AFXDLL antiguos.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Archivos DLL no basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL de MFC estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL de MFC estándar vinculado dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión MFC: información general](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)