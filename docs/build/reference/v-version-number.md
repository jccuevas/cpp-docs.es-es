---
title: -V (número de versión) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3daf62c818b454a5477de04a27c4b4f308c271d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="v-version-number"></a>/V (Número de versión)
Desusado. Inserta una cadena de texto en el archivo .obj.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Vstring  
```  
  
## <a name="arguments"></a>Argumentos  
 `string`  
 Cadena que especifica el número de versión o el aviso de copyright para incrustar en un archivo .obj.  
  
## <a name="remarks"></a>Comentarios  
 La etiqueta de stringcan un archivo .obj con un número de versión o un aviso de copyright. Los caracteres de espacio o tabulación deben incluirse entre comillas dobles (") si son una parte de la cadena. Una barra diagonal inversa (\\) debe preceder a las comillas dobles si son una parte de la cadena. Un espacio entre **/V** y `string` es opcional.  
  
 También puede usar [comentario) (C/C ++)](../../preprocessor/comment-c-cpp.md) con el argumento de tipo de comentario del compilador para colocar el nombre y número de versión del compilador en el archivo .obj.  
  
 El **/V** opción está en desuso a partir de Visual Studio 2005; **/V** era principalmente usa para admitir la creación de controladores de dispositivos virtuales (VxD) y compilar VXD ya no es compatible con el conjunto de herramientas de Visual C++. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y quitar opciones de compilador** en [opciones de compilador enumerados por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)