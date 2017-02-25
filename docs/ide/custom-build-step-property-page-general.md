---
title: "Paso de compilaci&#243;n personalizada (P&#225;gina de propiedades): General | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCustomBuildStep.AdditionalInputs"
  - "VC.Project.VCCustomBuildStep.CustomBuildAfterTargets"
  - "VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets"
  - "VC.Project.VCCustomBuildStep.Outputs"
  - "VC.Project.VCCustomBuildStep.Message"
  - "VC.Project.VCCustomBuildStep.Command"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "propiedades del proyecto, paso de compilación personalizada"
  - "paso de compilación personalizado (general)"
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Paso de compilaci&#243;n personalizada (P&#225;gina de propiedades): General
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para cada combinación de configuración y plataforma de destino del proyecto, puede especificar un paso personalizado que se realizará cuando se compile el proyecto.  
  
## Lista de UIElement  
 **Línea de comandos**  
 Comando que va a ejecutar el paso de compilación personalizada.  
  
 **Descripción**  
 Mensaje que se muestra cuando se ejecuta el paso de compilación personalizada.  
  
 **Outputs**  
 Archivo de salida que genera el paso de compilación personalizada.  Este valor es necesario para que las compilaciones incrementales funcionen correctamente.  
  
 **Dependencias adicionales**  
 Lista delimitada por puntos y coma de los archivos de entrada adicionales que se usarán para el paso de compilación personalizada.  
  
 **Ejecutar después y Ejecutar antes**  
 Estas opciones definen cuándo se ejecuta el paso de compilación personalizada en el proceso de compilación, en relación con los destinos enumerados.  Los destinos más frecuentes son BuildGenerateSources, BuildCompile y BuildLink, ya que representan los pasos principales del proceso de compilación.  Otros destinos frecuentes son Midl, CLCompile y Link.  
  
 Tratar salida como contenido  
 Esta opción solo es significativa para las aplicaciones de la Tienda Windows o de Windows Phone, que incluyen todos los archivos de contenido en el paquete .appx.  
  
### Para especificar un paso de compilación personalizada  
  
1.  En la barra de menús, elija **Proyecto**, **Propiedades**.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md).  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, navegue hasta **Propiedades de configuración**, **Paso de compilación personalizada**, **General**.  
  
3.  Modifique la configuración.  
  
## Vea también  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)