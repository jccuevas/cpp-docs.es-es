---
title: -IDLOUT (dar nombre a los archivos de salida MIDL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
dev_langs: C++
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f9f798c31fc4b492565c3406f0cb26251a208d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Dar nombre a los archivos de resultados de MIDL)
```  
/IDLOUT:[path\]filename  
```  
  
## <a name="parameters"></a>Parámetros  
 *path*  
 Una especificación de ruta de acceso absoluta o relativa. Al especificar una ruta de acceso, afectan a solo la ubicación de un archivo .idl; todos los demás archivos se colocan en el directorio del proyecto.  
  
 *filename*  
 Especifica el nombre del archivo .idl creado por el compilador MIDL. No se supone que ninguna extensión de archivo; Especifique *filename*.idl si desea una extensión .idl.  
  
## <a name="remarks"></a>Comentarios  
 La opción/IDLOUT especifica el nombre y la extensión del archivo .idl.  
  
 El vinculador de Visual C++ llama al compilador MIDL al vincular proyectos que tienen el [módulo](../../windows/module-cpp.md) atributo.  
  
 /IDLOUT también especifica los nombres de archivo de los demás archivos de salida asociados con el compilador MIDL:  
  
-   *nombre de archivo*.tlb  
  
-   *nombre de archivo*_p.c  
  
-   *nombre de archivo*_i.c  
  
-   *nombre de archivo*. h  
  
 *nombre de archivo* es el parámetro que pasa a/IDLOUT. Si [TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md) se especifica, el archivo .tlb obtendrá su nombre de TLBOUT *filename*.  
  
 Si se especifica ni /IDLOUT ni/TLBOUT, el vinculador creará vc70.tlb, vc70.idl, vc70_p.c, vc70_i.c y vc70.h.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **IDL incrustado** página de propiedades.  
  
4.  Modificar el **combinar nombre de archivo de Base IDL** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [/IGNOREIDL (no procesar atributos en MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL (especificar las opciones de línea de comandos MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Compilación de programas con atributos](../../windows/building-an-attributed-program.md)