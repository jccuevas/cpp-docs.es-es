---
title: "Inicializar un archivo DLL | Microsoft Docs"
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
  - "DLL [C++], inicializar"
  - "inicializar DLL"
  - "código de terminación [C++]"
ms.assetid: f655c5ff-ab5b-493a-a1da-4d1074e60c5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Inicializar un archivo DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Generalmente, el archivo DLL incluye código de inicialización \(de asignación de memoria, por ejemplo\) que deberá ejecutarse cuando se cargue el archivo DLL.  Cuando se utiliza Visual C\+\+, el punto en el que debe agregar código de inicialización para el archivo DLL dependerá del tipo de DLL que vaya a compilar.  Si no necesita agregar código de inicialización o de finalización, no tiene que hacer nada específico al compilar el archivo DLL.  En la tabla siguiente se indica dónde debe agregar código para inicializar el archivo DLL.  
  
|Tipo de archivo DLL|Dónde debe agregarse el código de inicialización y de finalización|  
|-------------------------|------------------------------------------------------------------------|  
|Archivo DLL estándar|En las funciones `InitInstance` y `ExitInstance` del objeto `CWinApp` del archivo DLL.|  
|Archivo DLL de extensión|En la función `DllMain` generada por el Asistente para archivos DLL de MFC.|  
|Archivo DLL que no está basado en MFC|En una función denominada `DllMain` proporcionada por el usuario.|  
  
 En Win32, todos los archivos DLL pueden contener una función de punto de entrada opcional \(normalmente denominada `DllMain`\) que se invoca para la inicialización y la finalización.  Esto le ofrece la oportunidad de asignar o liberar recursos adicionales cuando sea necesario.  Windows llamará a la función de punto de entrada en cuatro situaciones: asociación de proceso, desasociación de proceso, asociación de subproceso y desasociación de subproceso.  
  
 La biblioteca en tiempo de ejecución de C proporciona una función de punto de entrada denominada **\_DllMainCRTStartup**, que llama a `DllMain`.  En función del tipo de archivo DLL, deberá incluir una función denominada `DllMain` en el código fuente o utilizar la función `DllMain` proporcionada por la biblioteca MFC.  
  
## ¿Qué desea hacer?  
  
-   [Inicializar archivos DLL estándar](../build/initializing-regular-dlls.md)  
  
-   [Inicializar archivos DLL de extensión](../build/initializing-extension-dlls.md)  
  
-   [Inicializar archivos DLL que no están basados en MFC](../build/initializing-non-mfc-dlls.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Comportamiento de la biblioteca en tiempo de ejecución de C y \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [\<caps:sentence id\="tgt24" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>Especificación de funciones para DllMain \(SDK de Windows\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt25" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>Función de punto de entrada de biblioteca de vínculos dinámicos \(SDK de Windows\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)