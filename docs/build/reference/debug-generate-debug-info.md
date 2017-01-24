---
title: "/DEBUG (Generar informaci&#243;n de depuraci&#243;n) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.GenerateDebugInformation"
  - "/debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb (archivos), generar información de depuración"
  - "/DEBUG (opción del vinculador)"
  - "DEBUG (opción del vinculador)"
  - "-DEBUG (opción del vinculador)"
  - "depurar [C++], archivos de información de depuración"
  - "depurar [C++], opción del vinculador"
  - "generar información de depuración (opción del vinculador)"
  - "PDB (archivos)"
  - "pdb (archivos), generar información de depuración"
  - "bases de datos de programa [C++]"
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
caps.latest.revision: 11
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DEBUG (Generar informaci&#243;n de depuraci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEBUG  
```  
  
## Comentarios  
 La opción \/DEBUG crea información de depuración para el archivo .exe o DLL.  
  
 El vinculador incluye la información de depuración en una base de datos de programa \(PDB\)  y la actualiza durante posteriores compilaciones del programa.  
  
 Las DLL y los archivos .exe creados para depuración contienen el nombre y la ruta de acceso de la PDB correspondiente.  El depurador lee el nombre incrustado y usa la PDB durante la depuración del programa.  El vinculador le asigna a la base de datos de programa el nombre base del programa y la extensión .pdb y después incrusta la ruta de acceso en que fue creada.  Para reemplazar esta configuración predeterminada, es necesario establecer [\/PDB](../../build/reference/pdb-use-program-database.md) y especificar un nombre de archivo distinto.  
  
 Las opciones del compilador \/Zd \([Sólo números de línea](../../build/reference/z7-zi-zi-debug-information-format.md)\) y \/Z7 \([Compatible con C7](../../build/reference/z7-zi-zi-debug-information-format.md)\) hacen que el compilador deje la información de depuración en los archivos .obj.  También se puede usar la opción del compilador \/Zi \([Base de datos de programa](../../build/reference/z7-zi-zi-debug-information-format.md)\) para almacenar la información de depuración en una PDB del archivo .obj.  El vinculador busca la PDB del objeto primero en la ruta de acceso absoluta especificada en el archivo .obj y, después, en el directorio que contiene el archivo .obj.  No puede especificar el nombre o la ubicación del archivo PDB de un objeto en el vinculador.  
  
 [La opción \/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) está implícita cuando se especifica \/DEBUG.  
  
 \/DEBUG modifica los valores predeterminados de la opción [\/OPT](../../build/reference/opt-optimizations.md) de REF a NOREF y de ICF a NOICF \(de modo que no será necesario que especifique \/OPT:REF u \/OPT:ICF de forma explícita\).  
  
 Vea el artículo Q121366 de Knowledge Base \("INFO: PDB and DBG Files \- What They Are and How They Work"\), para obtener más información sobre los archivos .PDB y .DBG.  Encontrará artículos de Knowledge Base en MSDN Library, o en [http:\/\/support.microsoft.com](http://support.microsoft.com/).  
  
 No se puede crear un archivo .exe o .dll que contenga información de depuración.  La información de depuración se coloca siempre en un archivo .pdb.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades de **Depuración** .  
  
4.  Modifique la propiedad **Generar información de depuración**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)