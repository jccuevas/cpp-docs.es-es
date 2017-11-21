---
title: "Herramientas de compilación especificando personalizado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
dev_langs: C++
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.assetid: e5161946-8002-418d-991e-219e6a8586f5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c65664e6c09028f1f15ded917a59ad013868f841
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-custom-build-tools"></a>Especificar las herramientas de compilación personalizadas
A *herramienta de compilación personalizada* proporciona el sistema de compilación con la información que necesita para compilar archivos de entrada específicos. Una herramienta de compilación personalizada especifica un comando para ejecutar, una lista de archivos de entrada, una lista de archivos de salida generados por el comando y una descripción opcional de la herramienta.  
  
 Para obtener información general sobre las herramientas de compilación personalizada y pasos de compilación personalizada, vea [Introducción a los pasos de compilación personalizada y eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md).  
  
### <a name="to-specify-a-custom-build-tool"></a>Para especificar una herramienta de compilación personalizada  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../ide/working-with-project-properties.md).  
  
2.  Haga clic en **propiedades de configuración** para habilitar la **configuración** cuadro. En el **configuración** , seleccione la configuración para el que desea especificar una herramienta de compilación personalizada.  
  
3.  En **el Explorador de soluciones**, seleccione el archivo de entrada para la herramienta de compilación personalizada.  
  
     Si el **herramienta de compilación personalizada** carpeta no aparece, la extensión de archivo del archivo seleccionado está asociada con una herramienta de forma predeterminada. Por ejemplo, la herramienta predeterminada para los archivos .c y .cpp es el compilador. Para reemplazar una configuración de herramienta predeterminada, en la **propiedades de configuración** nodo, en la **General** carpeta, en la **tipo de elemento** propiedad, haga clic en **de compilación personalizada Herramienta**. Haga clic en **aplicar** y **herramienta de compilación personalizada** nodo se muestra.  
  
4.  En el **herramienta de compilación personalizada** nodo, en la **General** carpeta, especifique la herramienta de compilación de las propiedades asociadas con la opción de instalación:  
  
    -   En **dependencias adicionales**, especifique los archivos adicionales más allá de lo que se está definiendo la herramienta de compilación personalizada (el archivo asociado con la herramienta de compilación personalizada se considera implícitamente una entrada a la herramienta). Tener archivos de entrada adicionales no es un requisito para una herramienta de compilación personalizada. Si tiene más de una entrada adicional, sepárelas con punto y coma.  
  
         Si un **dependencias adicionales** fecha del archivo es posterior al archivo de entrada, a continuación, se ejecuta la herramienta de compilación personalizada. Si todos los de la **dependencias adicionales** archivos sean más antiguos que el archivo de entrada y el archivo de entrada es anterior a la **salidas** no se ejecuta el archivo de propiedades y, a continuación, la herramienta de compilación personalizada.  
  
         Por ejemplo, suponga que tiene una herramienta de compilación personalizada que toma MyInput.x como entrada y genera MyInput.cpp, y que incluye un archivo de encabezado, MyHeader.h. Puede especificar MyHeader.h como una dependencia de entrada para MyInput.x y el sistema de compilación compilará MyInput.cpp cuando esté anticuado con respecto a MyInput.x o MyHeader.h.  
  
         Las dependencias de entrada también pueden asegurarse de que las herramientas de compilación personalizada se ejecutan en el orden que necesite. En el ejemplo anterior, supongamos que MyHeader.h es, en realidad, el resultado de una herramienta de compilación personalizada. Dado que MyHeader.h es una dependencia de MyInput.x, el sistema de compilación generará primero MyHeader.h antes de ejecutar la herramienta de compilación personalizada en MyInput.x.  
  
    -   En **línea de comandos**, especifique un comando como si estuviera especificándolo en el símbolo del sistema. Especifique un comando válido o archivo por lotes, y cualquier entrada necesaria o archivos de salida. Especifique el **llamar** el comando antes del nombre de un archivo por lotes para garantizar que todos los comandos subsiguientes se ejecutan por lotes.  
  
         Varios archivos de entrada y salidos se pueden especificar simbólicamente con macros MSBuild. [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]especificar la ubicación de archivos o los nombres de los conjuntos de archivos, consulte [comunes Macros para propiedades y comandos de generación](../ide/common-macros-for-build-commands-and-properties.md).  
  
         Dado que el carácter '%' está reservado por MSBuild, si especifica una variable de entorno reemplaza cada  **%**  carácter con escape la **% 25** secuencia de escape hexadecimal. Por ejemplo, reemplace **% WINDIR %** con **25WINDIR % 25**. MSBuild reemplaza cada **% 25** de secuencia con el  **%**  antes de tener acceso a la variable de entorno de caracteres.  
  
    -   En **descripción**, escriba un mensaje descriptivo sobre esta herramienta de compilación personalizada. El mensaje se imprime en la **salida** ventana cuando el sistema de compilación procesa esta herramienta.  
  
    -   En **salidas**, especifique el nombre del archivo de salida. Se trata de una entrada obligatoria; sin un valor para esta propiedad, no se ejecutará la herramienta de compilación personalizada. Si una herramienta de compilación personalizada tiene más de una salida, separe los nombres de archivo con un punto y coma.  
  
         El nombre del archivo de salida debe ser el mismo tal y como se especifica en el **línea de comandos** propiedad. El sistema de compilación de proyectos buscará el archivo y comprobará su fecha. Si el archivo de salida es más reciente que el archivo de entrada, o si no se encuentra el archivo de salida, se ejecuta la herramienta de compilación personalizada. Si todos los de la **dependencias adicionales** archivos sean más antiguos que el archivo de entrada y el archivo de entrada es más antiguo que el archivo especificado en el **salidas** propiedad, no se ejecuta la herramienta de compilación personalizada.  
  
 Si desea que el sistema de compilación para que funcione en un archivo de salida generado por la herramienta de compilación personalizada, debe agregarlo manualmente al proyecto. La herramienta de compilación personalizada actualizará el archivo durante la compilación.  
  
## <a name="example"></a>Ejemplo  
 Se supone que van a incluir en el proyecto un archivo denominado parser.l. Desea que un analizador léxico procese parser.l para generar un archivo .c que tenga el mismo nombre base (parser.c).  
  
 En primer lugar, agregue parser.l y parser.c al proyecto. Si los archivos no existen todavía, solo tiene que agregar una referencia a los archivos. Crear una herramienta de compilación personalizada para parser.l y escriba lo siguiente en el **comandos** propiedad:  
  
```  
lexer %(FullPath) .\%(Filename).c  
```  
  
 Este comando ejecuta el analizador léxico sobre parser.l y produce parser.c en el directorio del proyecto.  
  
 En el **salidas** propiedad, escriba lo siguiente:  
  
```  
.\%(Filename).c  
```  
  
 Cuando se compila el proyecto, el sistema de compilación compara las marcas de tiempo de parser.l y parser.c. Si parser.l es más reciente, o si parser.c no existe, el sistema de compilación ejecuta el valor de la **línea de comandos** propiedad que se va a poner parser.c actualizado. Desde parser.c también se agregó al proyecto, el sistema de compilación, a continuación, lo compila.  
  
## <a name="see-also"></a>Vea también  
 [Común Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)   
 [Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md)