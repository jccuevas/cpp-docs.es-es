---
title: "Vinculaci&#243;n impl&#237;cita | Microsoft Docs"
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
  - "vinculación implícita [C++]"
  - "vinculación dinámica en tiempo de carga [C++]"
  - "vinculación de carga estática [C++]"
ms.assetid: 3ea4c316-4e70-4111-9944-c1b4ad00c605
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Vinculaci&#243;n impl&#237;cita
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para una vinculación implícita a un archivo DLL, los archivos ejecutables deberán obtener lo siguiente del proveedor del archivo DLL:  
  
-   Un archivo de encabezado \(archivo .h\) que contenga las declaraciones de las funciones exportadas o clases de C\+\+.  Todas las clases, todas las funciones y todos los datos deberían tener `__declspec(dllimport)`; para obtener más información, vea [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
-   Una biblioteca de importación \([archivos .LIB](../build/reference/dot-lib-files-as-linker-input.md)\) a la que vincularse. El vinculador crea la biblioteca de importación cuando se compila el archivo DLL.  
  
-   El propio archivo DLL \(archivo con la extensión .dll\).  
  
 Los archivos ejecutables que utilizan el archivo DLL deben incluir el archivo de encabezado que contiene las funciones exportadas \(o las clases de C\+\+\) en cada archivo de código fuente que contenga llamadas a las funciones exportadas.  Desde una perspectiva de programación, las llamadas a las funciones exportadas son como cualquier otra llamada a función.  
  
 Para compilar el archivo ejecutable de llamada deberá vincularlo a la biblioteca de importación.  Si utiliza un archivo MAKE externo, deberá especificar el nombre de archivo de la biblioteca de importación donde se indican otros archivos objeto \(.obj\) o bibliotecas con los que se están estableciendo vínculos.  
  
 El sistema operativo deberá ser capaz de encontrar el archivo DLL cuando cargue el archivo ejecutable de llamada.  
  
## ¿Qué desea hacer?  
  
-   [Vincular de forma explícita](../build/linking-explicitly.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Trabajar con bibliotecas de importación y archivos de exportación](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [La ruta de acceso de búsqueda que Windows utiliza para buscar una DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## Vea también  
 [Vincular un ejecutable a un archivo DLL](../build/linking-an-executable-to-a-dll.md)