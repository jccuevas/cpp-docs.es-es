---
title: "archivos .Lib como entrada del vinculador | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.AdditionalDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".lib (archivos)"
  - "COFF (archivos), bibliotecas de importación"
  - "bibliotecas predeterminadas [C++]"
  - "bibliotecas predeterminadas [C++], resultados del vinculador"
  - "valores predeterminados [C++], bibliotecas"
  - "bibliotecas de importación, archivos del vinculador"
  - "bibliotecas [C++], archivos .obj como entrada del vinculador"
  - "vincular [C++], OMF (bibliotecas)"
  - "OMF (bibliotecas)"
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# archivos .Lib como entrada del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LINK acepta bibliotecas estándar y de importación en formato COFF; en ambos casos, la extensión normalmente será .lib.  Las bibliotecas estándar contienen objetos y son creadas por la herramienta LIB.  Las bibliotecas de importación contienen información sobre exportaciones a otros programas; las crea LINK, al compilar un programa con exportaciones, o la herramienta LIB.  Para obtener información acerca de la creación de bibliotecas estándar o de importación mediante LIB, vea [Referencia de LIB](../../build/reference/lib-reference.md).  Para obtener más detalles acerca de la utilización de LINK para crear bibliotecas de importación, vea la opción [\/DLL](../../build/reference/dll-build-a-dll.md).  
  
 Las bibliotecas se especifican en LINK o como argumentos de nombre de archivo o como bibliotecas predeterminadas.  LINK resuelve las referencias externas buscando, en primer lugar, en las bibliotecas especificadas en la línea de comandos, después, en las bibliotecas predeterminadas especificadas con la opción [\/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) y, por último, en las bibliotecas predeterminadas mencionadas en los archivos .obj.  Si con el nombre de la biblioteca se especifica también una ruta de acceso, LINK la buscará en ese directorio.  Si no se especifica una ruta de acceso, LINK buscará primero en el directorio desde el que se esté ejecutando y, después, en cualquier directorio especificado en la variable de entorno LIB.  
  
### Para agregar archivos .lib como entrada del vinculador en el entorno de desarrollo  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Entrada**.  
  
4.  Modifique la propiedad **Dependencias adicionales**.  
  
### Para agregar mediante programación archivos .lib como entrada del vinculador  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalDependencies%2A>.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo compilar y utilizar un archivo .lib:  
  
```  
// lib_link_input_1.cpp  
// compile with: /LD  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
## Ejemplo  
 Y, a continuación,  
  
```  
// lib_link_input_2.cpp  
// compile with: /EHsc lib_link_input_1.lib  
__declspec(dllimport) int Test();  
#include <iostream>  
int main() {  
   std::cout << Test() << std::endl;  
}  
```  
  
  **213**   
## Vea también  
 [Archivos de entrada de LINK](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)