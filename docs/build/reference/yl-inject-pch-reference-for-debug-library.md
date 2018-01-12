---
title: "-Yl (Insertar referencia PCH para biblioteca de depuración) | Documentos de Microsoft"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yl
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e777977f6d869d2bbc28d980f6445851e54396b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Insertar referencia PCH para biblioteca de depuración)

El **/Yl** opción crea un símbolo comunes para un archivo de encabezado precompilado e inserta referencias a este símbolo en todos los archivos que utilizan el encabezado precompilado. Esto hace que la información de tipo completa para los símbolos de encabezado precompilado estén disponibles para el depurador en todos los archivos que utilizan el encabezado precompilado. Esta opción está habilitada de forma predeterminada. Uso de esta opción puede evitar que los errores del vinculador porque falta información de depuración en las bibliotecas vinculadas que usar encabezados precompilados.

## <a name="syntax"></a>Sintaxis

>**/Yl**  
>**/Yl**_nombre_  
>**/Yl-**  

### <a name="arguments"></a>Argumentos

*name*  
Un nombre opcional que se utiliza para definir un símbolo para ser archivos almacenados y que se hace referencia en el objeto que definen o utilizan encabezado precompilado.

*\-*  
Un guión (-) se deshabilita de forma explícita el **/Yl** opción del compilador.

## <a name="remarks"></a>Comentarios

El **/Yl** opción permite al depurador obtener información completa acerca de los tipos en un encabezado precompilado en cada archivo que incluya el encabezado precompilado. Esta opción crea un nombre de símbolo interno, inserta la definición del símbolo en el archivo de objeto que se utiliza para crear el encabezado precompilado por la [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opción e inserta una referencia al símbolo en todos los archivos que incluyen compilada previamente encabezado mediante el uso de la [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opción del compilador. Como todos los archivos de origen que utilizan el encabezado precompilado hacen referencia al símbolo con nombre, el vinculador vincule siempre el archivo de objeto que define el símbolo y el encabezado precompilado asociado información de depuración. Esta opción está habilitada de forma predeterminada.

El **/Yl**_nombre_ opción se utiliza para crear de forma explícita el símbolo de identificación para el archivo de encabezado precompilado. El compilador utiliza el *nombre* argumento para crear un símbolo similar a \_ \_ @@ \_PchSym\_@00@... @*nombre* , donde la cadena de caracteres representa un generados por el enlazador de puntos suspensivos (...). Si se omite el argumento, el compilador genera automáticamente un nombre de símbolo.

**/Yl-** deshabilita el comportamiento predeterminado y no se pone una referencia al símbolo identificación en los archivos de objeto que incluyan el encabezado precompilado. Esta opción puede resultar necesaria para los archivos compilados sin presente en el archivo de encabezado precompilado.

Si usa **/Yl-**, **/Yc** y [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) opciones para crear una biblioteca, el compilador crea un archivo de encabezado precompilado que contiene información de depuración que se almacena en un archivo de objeto en lugar de un archivo .pdb. [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) errores o [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) las advertencias pueden ocurrir en las compilaciones que emplean esta biblioteca y el encabezado precompilado si el archivo de origen utilizado para crear el encabezado precompilado no define ningún símbolo. El vinculador puede excluir este archivo de objeto de biblioteca desde el vínculo, junto con la información de depuración del encabezado precompilado asociado, cuando no hay nada en el archivo de objeto se hace referencia en el cliente de la biblioteca. Para solucionar el problema, especifique **/Yl** cuando usa **/Yc** para crear un archivo de encabezado precompilado y **/Yu** usarlo. Esto garantiza que el archivo de objeto que contiene la información de depuración se incluye en la compilación.

Para obtener más información sobre encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](../../build/reference/y-precompiled-headers.md)

- [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Elija la **línea de comandos** página de propiedades de la **C/C++** carpeta.

1. Agregar el **/Yl**_nombre_ opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
