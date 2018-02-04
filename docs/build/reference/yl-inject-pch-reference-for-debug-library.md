---
title: "-Yl (Insertar referencia PCH para biblioteca de depuración) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /yl
dev_langs:
- C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43e960906c504e5378a77d047c8eb1ab4d4594fe
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Insertar referencia PCH para biblioteca de depuración)

El **/Yl** opción genera un único símbolo en un archivo de encabezado precompilado y una referencia a este símbolo se aplica en todos los archivos de objeto que utilizan el encabezado precompilado.

## <a name="syntax"></a>Sintaxis

>**/Yl**  
>**/Yl**_nombre_  
>**/Yl-**  

### <a name="arguments"></a>Argumentos

*name*  
Un nombre opcional que se utiliza como parte del símbolo único.

*\-*  
Un guión (-) se deshabilita de forma explícita el **/Yl** opción del compilador.

## <a name="remarks"></a>Comentarios

El **/Yl** opción del compilador crea una definición de símbolo único en un archivo de encabezado precompilado creado mediante el [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opción. Las referencias a este símbolo se insertan automáticamente en todos los archivos que incluyen el encabezado precompilado utilizando la [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opción del compilador. El **/Yl** opción está habilitada de forma predeterminada cuando **/Yc** se utiliza para crear un archivo de encabezado precompilado.

El **/Yl**_nombre_ opción se utiliza para crear un símbolo de identificación en el archivo de encabezado precompilado. El compilador utiliza el *nombre* argumento como parte de su nombre representativo crea, similar a \_ \_ @@ \_PchSym\_@00@... @ *nombre*, donde la cadena de caracteres representa puntos suspensivos (...) un nombre único generado por el compilador. Si el *nombre* argumento se omite, el compilador genera un nombre de símbolo automáticamente. Normalmente, no es necesario conocer el nombre del símbolo. Sin embargo, cuando el proyecto usa más de un archivo de encabezado precompilado, la **/Yl**_nombre_ opción puede ser útil para determinar qué objeto archivos de uso que encabezado precompilado. Puede usar *nombre* como una cadena de búsqueda para buscar la referencia de símbolos en un archivo de volcado.

**/Yl-** deshabilita el comportamiento predeterminado y no se coloca un símbolo de identificación en el archivo de encabezado precompilado. Archivos compilados que incluyen este encabezado precompilado no obtienen una referencia al símbolo comunes.

Cuando **/Yc** no se especifica, cualquier **/Yl** opción no tiene ningún efecto, pero si especificado debe coincidir con cualquier **/Yl** opción pasa cuando **/Yc** es especificado.

Si usa **/Yl-**, **/Yc** y [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) opciones para generar un archivo de encabezado precompilado, la información de depuración se almacena en el archivo de objeto para el archivo de origen utilizado para crear el encabezado precompilado, en lugar de un archivo .pdb independiente. Si este archivo de objeto, a continuación, se convierte en parte de una biblioteca, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) errores o [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) las advertencias pueden ocurrir en las compilaciones que usan esta biblioteca y el archivo de encabezado precompilado, si el archivo de origen utilizado para crear el archivo de encabezado precompilado no define ningún símbolo propio. El vinculador puede excluir el archivo objeto desde el vínculo, junto con la información de depuración asociada, cuando no hay nada en el archivo de objeto se hace referencia en el cliente de la biblioteca. Para solucionar este problema, especifique **/Yl** (o quitar el **/Yl-** opción) cuando se usa **/Yc** para crear el archivo de encabezado precompilado. Esto garantiza que el archivo de objeto de la biblioteca que contiene la información de depuración obtiene vinculado en la compilación.

Para obtener más información sobre encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](../../build/reference/y-precompiled-headers.md)

- [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Agregar el **/Yl**_nombre_ opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
