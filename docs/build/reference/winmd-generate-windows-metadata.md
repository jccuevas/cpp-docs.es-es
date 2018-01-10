---
title: -WINMD (generar metadatos de Windows) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs: C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 903ab6875457aa8c069c47a2be7f8ff1f5c884a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generar metadatos de Windows)
Habilita la generación de un archivo de metadatos en tiempo de ejecución de Windows (.winmd).  
  
```  
/WINMD[:{NO|ONLY}]  
```  
  
## <a name="remarks"></a>Comentarios  
 /WINMD  
 El valor predeterminado de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplicaciones. El enlazador genera el archivo ejecutable binario y el archivo de metadatos de winmd.  
  
 /WINMD:NO  
 El enlazador genera solo el archivo ejecutable binario, pero no es un archivo winmd.  
  
 / WINMD: SOLO  
 El enlazador genera solo el archivo .winmd, pero no el archivo ejecutable binario.  
  
 De forma predeterminada, el nombre de archivo de salida tiene la forma `binaryname`.winmd. Para especificar un nombre de archivo diferente, use la [/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) opción.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **metadatos de Windows** página de propiedades.  
  
4.  En el **generar metadatos de Windows** lista desplegable, seleccione la opción que desee.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)