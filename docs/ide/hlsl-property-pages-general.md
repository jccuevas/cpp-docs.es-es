---
title: "P&#225;ginas de propiedades HLSL: General | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.FXCompilerTool.ShaderModel"
  - "VC.Project.FXCompilerTool.PreprocessorDefinitions"
  - "VC.Project.FXCompilerTool.ShaderType"
  - "VC.Project.FXCompilerTool.EnableDebuggingInformation"
  - "VC.Project.FXCompilerTool.AdditionalIncludeDirectories"
  - "VC.Project.FXCompilerTool.DisableOptimizations"
  - "VC.Project.FXCompilerTool.EntryPointName"
dev_langs: 
  - "C++"
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
caps.latest.revision: 8
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 8
---
# P&#225;ginas de propiedades HLSL: General
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para configurar las propiedades siguientes del compilador de HLSL \(fxc.exe\), utilice la página de propiedades **General** .  Para obtener información sobre cómo tener acceso a la página de propiedades **General** en la carpeta de HLSL, vea [Cómo: Especificar propiedades de proyecto con páginas de propiedades](../misc/how-to-specify-project-properties-with-property-pages.md).  
  
## Lista de UIElement  
 **Directorios de inclusión adicionales**  
 Agregue uno o más directorios a la ruta de inclusión.  Utilice los signos de punto y coma para separar los directorios.  
  
 Esta propiedad corresponde a **\/I\[path\]** el argumento de línea de comandos.  
  
 **Nombre de Entrypoint**  
 Especifica el punto de entrada para el sombreador.  De forma predeterminada, el valor es **principal**.  
  
 Esta propiedad corresponde a **\/E\[name\]** el argumento de línea de comandos.  
  
 **Optimizaciones de deshabilitar la**  
 **Sí \(\/Od\)** para deshabilitar optimizaciones; si no, **No**.  De forma predeterminada, el valor es **Sí \(\/Od\)** para las configuraciones y **NoDepurar** para las configuraciones **Liberar** .  
  
 El argumento de la línea de comandos **\/Od** al compilador de HLSL aplica implícitamente el argumento de la línea de comandos **\/Gfp** , pero generado no puede ser idéntica a la salida que se genera pasando los argumentos de la línea de comandos de **\/Od** y de **\/Gfp** explícitamente.  
  
 **Habilite la información de depuración**  
 **Sí \(\/Zi\)** para habilitar la información de depuración; si no, **No**.  De forma predeterminada, el valor es **Sí \(\/Zi\)** para las configuraciones y **NoDepurar** para las configuraciones **Liberar** .  
  
 **Tipo de Presentación**  
 Especifica el tipo de presentación.  Tipos diferentes partes de implementan de los sombreadores de diferentes de la canalización de gráficos.  Algunas clases de los sombreadores solo están disponibles en los modelos más recientes de presentación \(que son especificados en la propiedad **Sombreador Model** \) \(por ejemplo, los sombreadores de cálculo se introdujeron en el modelo 5. de presentación.  
  
 Esta propiedad corresponde a **\[type\]** a la parte del argumento de la línea de comandos **\/T \[type\]\_\[model\]** al compilador de HLSL.  La propiedad **Modelos de Presentación** especifica la parte de **\[model\]** de argumento.  
  
 **Sombreador Model**  
 Especifica el modelo de sombreador.  Diferentes modelos de presentación tienen funcionalidad diferentes.  Una ofrecen más reciente de los modelos de presentación expandido normalmente las funciones pero requiere hardware más de gráficos moderno ejecutar el código de presentación.  Algunas clases de los sombreadores \(que son especificados en la propiedad **Tipo de Presentación** \) solo están disponibles en un sombreador más reciente modelo\- para el ejemplo, los sombreadores de cálculo se introdujeron en el modelo 5. de presentación.  
  
 Esta propiedad corresponde a **\[model\]** a la parte del argumento de la línea de comandos **\/T \[type\]\_\[model\]** al compilador de HLSL.  La propiedad **Tipo de Presentación** especifica la parte de **\[type\]** de argumento.  
  
 **Definiciones del preprocesador**  
 Agrega una o más definiciones del símbolo de preprocesador para aplicar al archivo de código fuente de HLSL.  Utilice los signos de punto y coma para separar las definiciones de símbolos.  
  
 Esta propiedad corresponde a **\/D \[definitions\]** el argumento de línea de comandos del compilador de HLSL.  
  
## Vea también  
 [Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)   
 [Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)   
 [Páginas de propiedades HLSL: archivos de salida](../ide/hlsl-property-pages-output-files.md)