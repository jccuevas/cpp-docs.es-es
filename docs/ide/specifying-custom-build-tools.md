---
title: Especificar las herramientas de compilación personalizadas
ms.date: 06/05/2018
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
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: a4367f3ed914ff948969473b10f4772f1540936d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581810"
---
# <a name="specify-custom-build-tools"></a>Especificar las herramientas de compilación personalizadas

Una *herramienta de compilación personalizada* proporciona al sistema de compilación la información que necesita para compilar archivos de entrada específicos. Una herramienta de compilación personalizada especifica un comando para ejecutar, una lista de archivos de entrada, una lista de archivos de salida generados por el comando y una descripción opcional de la herramienta.

Para obtener información general sobre las herramientas de compilación personalizadas y los pasos de compilación personalizada, vea [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>Para especificar una herramienta de compilación personalizada

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C++](../ide/working-with-project-properties.md).

1. Seleccione **Propiedades de configuración** para habilitar el cuadro **Configuración**. En el cuadro **Configuración**, seleccione la configuración para la que quiera especificar una herramienta de compilación personalizada.

1. En el **Explorador de soluciones**, seleccione el archivo de entrada para la herramienta de compilación personalizada.

   Si no aparece la carpeta **Herramienta de compilación personalizada**, la extensión del archivo seleccionado está asociada con una herramienta predeterminada. Por ejemplo, la herramienta predeterminada para los archivos .c y .cpp es el compilador. Para reemplazar una configuración de herramienta predeterminada, en el nodo **Propiedades de configuración**, en la carpeta **General**, en la propiedad **Tipo de elemento**, seleccione **Herramienta de compilación personalizada**. Haga clic en **Aplicar** y se mostrará el nodo **Herramienta de compilación personalizada**.

1. En el nodo **Herramienta de compilación personalizada**, en la carpeta **General**, especifique las propiedades asociadas a la herramienta de compilación personalizada:

   - En **Dependencias adicionales**, especifique los archivos adicionales además del archivo para el que se esté definiendo la herramienta de compilación personalizada (el archivo asociado con la herramienta de compilación personalizada se considera implícitamente una entrada para la herramienta). Tener archivos de entrada adicionales no es un requisito para una herramienta de compilación personalizada. Si tiene más de una entrada adicional, sepárelas con punto y coma.

      Si la fecha del archivo de **Dependencias adicionales** es posterior a la del archivo de entrada, se ejecuta la herramienta de compilación personalizada. Si todos los archivos de **Dependencias adicionales** son anteriores al archivo de entrada y el archivo de entrada es anterior al archivo de propiedades **Salidas**, la herramienta de compilación personalizada no se ejecuta.

      Por ejemplo, suponga que tiene una herramienta de compilación personalizada que toma MyInput.x como entrada y genera MyInput.cpp, y que este archivo incluye un archivo de encabezado, MyHeader.h. Puede especificar MyHeader.h como una dependencia de entrada para MyInput.x y el sistema de compilación compilará MyInput.cpp cuando esté anticuado con respecto a MyInput.x o MyHeader.h.

      Las dependencias de entrada también pueden garantizar que las herramientas de compilación personalizadas se ejecutan en el orden necesario. En el ejemplo anterior, suponga que MyHeader.h es, en realidad, la salida de una herramienta de compilación personalizada. Como MyHeader.h es una dependencia de MyInput.x, el sistema de compilación compilará primero MyHeader.h antes de ejecutar la herramienta de compilación personalizada en MyInput.x.

   - En **Línea de comandos**, especifique un comando como si estuviera especificándolo en el símbolo del sistema. Especifique un comando o archivo por lotes válido, y los archivos de entrada o salida necesarios. Especifique el comando por lotes **call** antes del nombre de un archivo por lotes para garantizar que se ejecuten todos los comandos siguientes.

      Se pueden especificar varios archivos de entrada y salida simbólicamente mediante macros de MSBuild. Para obtener información sobre cómo especificar la ubicación de los archivos o los nombres de los conjuntos de archivos, vea [Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md).

      Como el carácter "%" está reservado por MSBuild, si se especifica una variable de entorno, reemplace todos los caracteres con escape **%** con la secuencia de escape hexadecimal **%25**. Por ejemplo, reemplace **%WINDIR%** con **%25WINDIR%25**. MSBuild reemplaza todas las secuencias **%25** con el carácter **%** antes de acceder a la variable de entorno.

   - En **Descripción**, escriba un mensaje descriptivo sobre esta herramienta de compilación personalizada. El mensaje se imprime en la ventana **Salida** cuando el sistema de compilación procesa esta herramienta.

   - En **Salidas**, especifique el nombre del archivo de salida. Se trata de una entrada obligatoria; sin un valor para esta propiedad, la herramienta de compilación personalizada no se ejecutará. Si una herramienta de compilación personalizada tiene más de una salida, separe los nombres de archivo con un punto y coma.

      El nombre del archivo de salida debe ser el mismo que se especifique en la propiedad **Línea de comandos**. El sistema de compilación de proyectos buscará el archivo y comprobará su fecha. Si el archivo de salida es más antiguo que el archivo de entrada, o bien si no se encuentra el archivo de salida, se ejecuta la herramienta de compilación personalizada. Si todos los archivos de **Dependencias adicionales** son anteriores al archivo de entrada y el archivo de entrada es anterior al archivo especificado en la propiedad **Salidas**, la herramienta de compilación personalizada no se ejecuta.

Si quiere que el sistema de compilación funcione en un archivo de salida generado por la herramienta de compilación personalizada, debe agregarlo de manera manual al proyecto. La herramienta de compilación personalizada actualizará el archivo durante la compilación.

## <a name="example"></a>Ejemplo

Suponga que quiere incluir un archivo denominado parser.l en el proyecto. Tiene un analizador léxico, **lexer.exe**, en la ruta de acceso del archivo ejecutable. Quiere usarlo para procesar parser.l para generar un archivo .c que tenga el mismo nombre base (parser.c).

En primer lugar, agregue parser.l y parser.c al proyecto. Si todavía no existen los archivos, agregue una referencia a los archivos. Cree una herramienta de compilación personalizada para parser.l y escriba lo siguiente en la propiedad **Comandos**:

> **lexer %(RutaDeAccesoCompleta) .\%(NombreDeArchivo).c**

Este comando ejecuta el analizador léxico en parser.l y genera parser.c en el directorio del proyecto.

En la propiedad **Salidas**, escriba lo siguiente:

> **.\%(NombreDeArchivo).c**

Al compilar el proyecto, el sistema de compilación compara las marcas de tiempo de parser.l y parser.c. Si parser.l es más reciente, o bien si parser.c no existe, el sistema de compilación ejecuta el valor de la propiedad **Línea de comandos** para actualizar parser.c. Como parser.c también se agregó al proyecto, el sistema de compilación lo compila.

## <a name="see-also"></a>Vea también

[Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)<br>
[Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md)
