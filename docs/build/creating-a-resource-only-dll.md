---
title: "Crear un archivo DLL de recursos | Microsoft Docs"
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
  - "DLL [C++], crear"
  - "DLL sólo de recursos [C++], crear"
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Crear un archivo DLL de recursos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un archivo DLL de recursos es un archivo DLL que sólo contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo.  El uso de este tipo de archivo es una buena manera de compartir el mismo conjunto de recursos entre varios programas.  También es bueno para proporcionar una aplicación con recursos localizados en varios idiomas \(vea [Recursos localizados en aplicaciones MFC: archivos DLL satélite](../build/localized-resources-in-mfc-applications-satellite-dlls.md)\).  
  
 Para crear un archivo DLL de recursos debe crear un nuevo proyecto de archivo DLL para Win32 \(que no esté basado en MFC\) y agregar los recursos al proyecto.  
  
-   Seleccione Proyecto Win32 en el cuadro de diálogo **Nuevo proyecto** y especifique un tipo de proyecto de DLL en el Asistente para proyectos Win32.  
  
-   Cree un nuevo script de recursos que contenga los recursos \(como una cadena o un menú\) para el archivo DLL y guarde el archivo .rc.  
  
-   En el menú **Proyecto**, haga clic en **Agregar elemento existente** e inserte el nuevo archivo .rc en el proyecto.  
  
-   Especifique la opción [\/NOENTRY](../build/reference/noentry-no-entry-point.md) del vinculador. \/NOENTRY evita que el vinculador vincule una referencia a \_main en el archivo DLL; esta opción es necesaria para crear un archivo DLL sólo de recursos.  
  
-   Compile el archivo DLL.  
  
 La aplicación que utiliza el archivo DLL de recursos debe llamar a **LoadLibrary** para [vincularse explícitamente al archivo DLL](../build/loadlibrary-and-afxloadlibrary.md).  Para tener acceso a los recursos, llame a las funciones genéricas **FindResource** y **LoadResource**, que funcionan en cualquier tipo de recurso, o llame a una de las siguientes funciones específicas para recursos:  
  
-   `FormatMessage`  
  
-   **LoadAccelerators**  
  
-   `LoadBitmap`  
  
-   `LoadCursor`  
  
-   `LoadIcon`  
  
-   `LoadMenu`  
  
-   `LoadString`  
  
 La aplicación debe llamar a **FreeLibrary** cuando deje de utilizar los recursos.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [DELETE\_PENDING\_Editing Resources](http://msdn.microsoft.com/es-es/c29d31c7-2d94-40ca-8aa0-c7262883529c)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)