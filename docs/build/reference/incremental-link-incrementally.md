---
title: -INCREMENTAL (vincular de forma incremental) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
dev_langs:
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7495b3dda7b79f45045176fc949016f89c92506a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (Vincular de forma incremental)
```  
/INCREMENTAL[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 Controla el modo en que el vinculador administra la vinculación incremental.  
  
 De manera predeterminada, el vinculador se ejecuta en modo incremental. Para reemplazar un vínculo incremental predeterminado, especifique /INCREMENTAL:NO.  
  
 Un programa vinculado de forma incremental es funcionalmente equivalente a un programa que está vinculado de forma no incremental. Sin embargo, al estar preparados para posteriores vínculos incrementales, una biblioteca estática de ejecutable vinculado incrementalmente o el archivo de biblioteca de vínculos dinámicos:  
  
-   Es mayor que un programa vinculado de forma no incremental a causa del relleno del código y los datos. El relleno permite al vinculador aumentar el tamaño de las funciones y los datos sin volver a crear el archivo.  
  
-   Pueden contener códigos thunk de salto para controlar la reubicación de las funciones en direcciones nuevas.  
  
    > [!NOTE]
    >  Para asegurarse de que la versión final de lanzamiento no contiene relleno ni códigos thunk, vincule el programa de forma no incremental.  
  
 Para vincular de forma incremental con independencia del valor predeterminado, especifique /INCREMENTAL. Cuando se selecciona esta opción, el vinculador emite una advertencia si no se puede vincular de forma incremental y, a continuación, vincula el programa de forma no incremental. Hay ciertas opciones y situaciones que invalidan la opción /INCREMENTAL.  
  
 La mayoría de los programas pueden vincularse de manera incremental. Sin embargo, algunos cambios son demasiado grandes y algunas opciones no son compatibles con la vinculación incremental. LINK realizará un vínculo completo si se especifica cualquiera de las opciones siguientes:  
  
-   No se selecciona la vinculación incremental (/INCREMENTAL:NO).  
  
-   Se selecciona /OPT:REF.  
  
-   Se selecciona /OPT:ICF.  
  
-   Se selecciona /OPT:LBR.  
  
-   Se selecciona /ORDER.  
  
 /INCREMENTAL está implícita cuando [/DEBUG](../../build/reference/debug-generate-debug-info.md) se especifica.  
  
 Asimismo, LINK realizará un vínculo completo si se da alguna de las situaciones siguientes:  
  
-   Falta el archivo de estado incremental (.ilk). (LINK crea un archivo .ilk nuevo en previsión de una vinculación incremental posterior).  
  
-   No se cuenta con permiso de escritura para el archivo .ilk. (LINK omite el archivo .ilk y vínculos de forma no incremental.)  
  
-   Falta el archivo de salida .exe o .dll.  
  
-   Se ha modificado la marca de tiempo del archivo .ilk, .exe o .dll.  
  
-   Se ha modificado una opción de LINK. La mayoría de las opciones de LINK, si se cambian entre compilaciones, producen un vínculo completo.  
  
-   Se ha agregado u omitido un archivo objeto (.obj).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione la página de propiedades **General** .  
  
4.  Modificar el **habilitar vinculación Incremental** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)