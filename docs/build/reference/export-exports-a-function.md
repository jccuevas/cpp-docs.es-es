---
title: "-EXPORT (exporta una función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2183a67679fc216396d03ac31a5a11db8d011454
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="export-exports-a-function"></a>/EXPORT (Exporta una función)
```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## <a name="remarks"></a>Comentarios  
 Con esta opción, puede exportar una función desde el programa para que otros programas pueden llamar a la función. También puede exportar los datos. Exportaciones generalmente se definen en un archivo DLL.  
  
 El *entrada* es el nombre de la función o elemento de datos que va a ser utilizada por el programa que realiza la llamada. `ordinal`Especifica un índice en la tabla de exportaciones en el intervalo 1 a 65535; Si no se especifica `ordinal`, LINK asigna uno. El **NONAME** palabra clave exporta la función solo como un valor ordinal, sin un *entrada*.  
  
 El **datos** palabra clave especifica que el elemento exportado es un elemento de datos. El elemento de datos en el programa cliente debe declararse mediante **extern __declspec (dllimport)**.  
  
 Hay tres métodos para exportar una definición, aparecen en el orden recomendado de uso:  
  
1.  [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) en el código fuente  
  
2.  Un [exportaciones](../../build/reference/exports.md) instrucción en un archivo .def  
  
3.  Una especificación / Export en un comando de LINK  
  
 Los tres métodos se pueden utilizar en el mismo programa. Cuando LINK compila un programa que contiene exportaciones, también crea una biblioteca de importación, a menos que se usa un archivo .exp en la compilación.  
  
 LINK usa formatos de identificadores representativos. El compilador decora un identificador cuando crea el archivo .obj. Si *entrada* se especifica para el vinculador en su no representativo formar (tal y como aparece en el código fuente), LINK intentará encontrar el nombre. Si no se encuentra a una coincidencia única, LINK emite un mensaje de error. Use la [DUMPBIN](../../build/reference/dumpbin-reference.md) herramienta para establecer el [nombres representativos](../../build/reference/decorated-names.md) formada por un identificador cuando se debe especificar al vinculador.  
  
> [!NOTE]
>  No se especifica el formato representativo de identificadores de C se declaran `__cdecl` o `__stdcall`.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción en la **opciones adicionales** cuadro.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)