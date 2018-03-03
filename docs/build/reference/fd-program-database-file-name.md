---
title: -Fd (nombre de archivo de base de datos de programa) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9cda26f310ec110c452394e960d3fb81d1f3e8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fd-program-database-file-name"></a>/Fd (Nombre del archivo de base de datos del programa)
Especifica un nombre de archivo para el archivo de base de datos (PDB) programa creado por [/Z7, / Zi, /ZI (formato de información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Fdpathname  
```  
  
## <a name="remarks"></a>Comentarios  
 Sin **/Fd**, el nombre del archivo PDB tiene como valor predeterminado VC*x*0.pdb, donde *x* es la versión principal de Visual C++ en uso.  
  
 Si especifica un nombre de ruta de acceso que no incluye un nombre de archivo (la ruta de acceso finaliza con una barra diagonal inversa), el compilador crea un archivo .pdb denominado VC*x*0 pdb en el directorio especificado.  
  
 Si especifica un nombre de archivo que no incluye una extensión, el compilador utiliza .pdb como la extensión.  
  
 Esta opción también asigna el archivo de estado (.idb) utilizado para la recompilación mínima y la compilación incremental.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Archivos de salida** .  
  
4.  Modificar el **nombre de archivo de base de datos de programa** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.  
  
## <a name="example"></a>Ejemplo  
 Esta línea de comandos crea un archivo .pdb denominado PROG.pdb y un archivo .idb denominado PROG.idb:  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)