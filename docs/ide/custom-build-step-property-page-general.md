---
title: 'Paso de compilación personalizada (Página de propiedades): General'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: dc6765c9519c6cdb4245afa2f07079548a07e1fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621759"
---
# <a name="custom-build-step-property-page-general"></a>Paso de compilación personalizada (Página de propiedades): General

Para cada combinación de configuración y plataforma de destino del proyecto, puede especificar un paso personalizado que se realizará cuando se compile el proyecto.

Para la versión de Linux de esta página, vea [Propiedades de paso de compilación personalizada (C++ para Linux)](../linux/prop-pages/custom-build-step-linux.md).

## <a name="uielement-list"></a>Lista de UIElement

- **Línea de comandos**

   Comando que va a ejecutar el paso de compilación personalizada.

- **Descripción**

   Mensaje que se muestra cuando se ejecuta el paso de compilación personalizada.

- **Salidas**

   Archivo de salida que genera el paso de compilación personalizada. Este valor es necesario para que las compilaciones incrementales funcionen correctamente.

- **Dependencias adicionales**

   Lista delimitada por puntos y coma de los archivos de entrada adicionales que se usarán para el paso de compilación personalizada.

- **Ejecutar después y Ejecutar antes**

   Estas opciones definen cuándo se ejecuta el paso de compilación personalizada en el proceso de compilación, en relación con los destinos enumerados. Los destinos más frecuentes son BuildGenerateSources, BuildCompile y BuildLink, ya que representan los pasos principales del proceso de compilación. Otros destinos frecuentes son Midl, CLCompile y Link.

- **Tratar salida como contenido**

   Esta opción solo es significativa para las aplicaciones de la Plataforma universal de Windows o de Windows Phone, que incluyen todos los archivos de contenido en el paquete .appx.

### <a name="to-specify-a-custom-build-step"></a>Para especificar un paso de compilación personalizada

1. En la barra de menús, seleccione **Proyecto**, **Propiedades**. Para obtener más información, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

1. En el cuadro de diálogo **Páginas de propiedades**, navegue hasta la página **Propiedades de configuración**, **Paso de compilación personalizada**, **General**.

1. Modifique la configuración.

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../ide/property-pages-visual-cpp.md)