---
title: "Página de propiedades de paso de compilación personalizada: General | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
dev_langs:
- C++
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e57d6cf00843cd6604ef269235602ea1b5b5e9b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="custom-build-step-property-page-general"></a>Paso de compilación personalizada (Página de propiedades): General
Para cada combinación de configuración y plataforma de destino del proyecto, puede especificar un paso personalizado que se realizará cuando se compile el proyecto.  

Para la versión de Linux de esta página, vea [propiedades de paso de compilación personalizada (C++ Linux)](../linux/prop-pages/custom-build-step-linux.md).
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Línea de comandos**  
 Comando que va a ejecutar el paso de compilación personalizada.  
  
 **Descripción**  
 Mensaje que se muestra cuando se ejecuta el paso de compilación personalizada.  
  
 **Outputs**  
 Archivo de salida que genera el paso de compilación personalizada. Este valor es necesario para que las compilaciones incrementales funcionen correctamente.  
  
 **Dependencias adicionales**  
 Lista delimitada por puntos y coma de los archivos de entrada adicionales que se usarán para el paso de compilación personalizada.  
  
 **Ejecutar después y ejecutar antes**  
 Estas opciones definen cuándo se ejecuta el paso de compilación personalizada en el proceso de compilación, en relación con los destinos enumerados. Los destinos más frecuentes son BuildGenerateSources, BuildCompile y BuildLink, ya que representan los pasos principales del proceso de compilación. Otros destinos frecuentes son Midl, CLCompile y Link.  
  
 Tratar salida como contenido  
 Esta opción solo es significativa para las aplicaciones de plataforma Universal de Windows o Windows Phone, que incluyen todos los archivos de contenido en el paquete-AppX.  
  
### <a name="to-specify-a-custom-build-step"></a>Para especificar un paso de compilación personalizada  
  
1.  En la barra de menús, seleccione **Proyecto**, **Propiedades**. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
2.  En el **páginas de propiedades** diálogo cuadro, vaya a la **propiedades de configuración**, **paso de compilación personalizada**, **General** página.  
  
3.  Modifique la configuración.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)