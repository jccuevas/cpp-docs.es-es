---
title: Solucionar problemas de personalizaciones de compilación
ms.date: 11/04/2016
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
ms.openlocfilehash: 52f4e37a2321cbd19fc85e7036cb8882e9399ac5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480914"
---
# <a name="troubleshooting-build-customizations"></a>Solucionar problemas de personalizaciones de compilación

Si los pasos de compilación personalizada o los eventos no se comportan de la forma esperada, se pueden hacer varias cosas para intentar comprender la causa del error.

- Asegúrese de que los archivos que generan los pasos de compilación personalizada coinciden con los archivos que se declaran como salidas.

- Si los pasos de compilación personalizada generan archivos que son entradas o dependencias de otros pasos de compilación (personalizada o no), asegúrese de que esos archivos se agregan al proyecto. Y asegúrese de que las herramientas que usan esos archivos se ejecutan después del paso de compilación personalizada.

- Para mostrar lo que realmente hace el paso de compilación personalizada, agregue `@echo on` como el primer comando. Los eventos de compilación y los pasos de compilación se colocan en un archivo .bat temporal y se ejecutan cuando se compila el proyecto. Por tanto, se puede agregar comprobación de errores a los eventos de compilación o comandos de paso de compilación.

- Examine el registro de compilación en el directorio de archivos intermedio para ver lo que realmente se ha ejecutado. La ruta de acceso y el nombre del registro de compilación se representan mediante la expresión de macro de **MSBuild**, **$(IntDir)\\$(Nombre_Proyecto_MSBuild).log**.

- Modifique la configuración del proyecto para obtener más información que la predeterminada en el registro de compilación. En el menú **Herramientas** , haga clic en **Opciones**. En el cuadro de diálogo **Opciones**, haga clic en el nodo **Proyectos y soluciones** y después en el nodo **Compilar y ejecutar**. Luego, en el cuadro **Contenido del archivo de registro de compilación del proyecto de MSBuild**, haga clic en **Detallado**.

- Compruebe los valores de las macros de nombre de archivo o directorio que use. Puede mostrar las macros de forma individual, o bien puede agregar `copy %0 command.bat` al principio del paso de compilación personalizada, lo que copiará los comandos del paso de compilación personalizada a command.bat con todas las macros expandidas.

- Ejecute los pasos de compilación personalizada y los eventos de compilación de forma individual para comprobar su comportamiento.

## <a name="see-also"></a>Vea también

[Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)