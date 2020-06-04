---
title: Generación de manifiestos en Visual Studio
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273370"
---
# <a name="manifest-generation-in-visual-studio"></a>Generación de manifiestos en Visual Studio

En el cuadro de diálogo **Páginas de propiedades** del proyecto se puede controlar la generación de un archivo de manifiesto para un proyecto determinado. En la pestaña **Propiedades de configuración**, haga clic en **Enlazador**, **Archivo de manifiesto** y **Generar manifiesto**. De forma predeterminada, las propiedades del proyecto de los proyectos nuevos están establecidas para generar un archivo de manifiesto. Aun así, es posible deshabilitar la generación del manifiesto para un proyecto mediante la propiedad **Generar manifiesto** del proyecto. Cuando esta propiedad se establece en **Sí**, se genera el manifiesto para el proyecto. En caso contrario, el enlazador omite la información del ensamblado al resolver las dependencias del código de la aplicación y no genera el manifiesto.

El sistema de compilación de Visual Studio permite insertar el manifiesto en el archivo de aplicación binario final o generarlo como un archivo externo. Este comportamiento se controla mediante la opción **Incrustar manifiesto** en el cuadro de diálogo **Propiedades del proyecto**. Para establecer esta propiedad, abra el nodo **Herramienta Manifiesto** y seleccione **Entrada y salida**. Si el manifiesto no está insertado, se genera como un archivo externo y se guarda en el mismo directorio que el archivo binario final. Si el manifiesto está insertado, Visual Studio inserta los manifiestos finales mediante el siguiente proceso:

1. Una vez que el código fuente se ha compilado en los archivos objeto, el enlazador recopila información de ensamblado dependiente. Al vincular el archivo binario final, el enlazador genera un manifiesto intermedio que se usa posteriormente para generar el manifiesto final.

1. Una vez que se han completado el manifiesto intermedio y la vinculación, se ejecutará la herramienta manifiesto para combinar un manifiesto final y guardarlo como un archivo externo.

1. Después, el sistema de compilación del proyecto detecta si el manifiesto generado por la herramienta de manifiesto contiene información diferente a la del manifiesto que ya está insertado en el archivo binario.

1. Si el manifiesto insertado en el archivo binario es diferente del manifiesto generado por la herramienta de manifiesto, o si el archivo binario no contiene un manifiesto insertado, Visual Studio invocará el enlazador una vez más para insertar el archivo de manifiesto externo en el archivo binario como un recurso.

1. Si el manifiesto insertado en el archivo binario es el mismo que el manifiesto generado por la herramienta de manifiesto, la compilación continuará con los siguientes pasos de compilación.

El manifiesto se inserta en el archivo binario final como un recurso de texto y se puede visualizar si el binario final se abre como un archivo en Visual Studio. Para asegurarse de que el manifiesto apunte a las bibliotecas correctas, siga los pasos que se describen en [Descripción de las dependencias de una aplicación de Visual C++](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) o siga las sugerencias indicadas en la sección [Solución de problemas](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Vea también

[Introducción a la generación de manifiestos para los programas de C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
