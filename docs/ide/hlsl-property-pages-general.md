---
title: "Páginas de propiedades HLSL: General | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
dev_langs: C++
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: be548966f6e75afde2c137c8beab38903844667c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hlsl-property-pages-general"></a>Páginas de propiedades HLSL: General
Para configurar las siguientes propiedades del compilador HLSL (fxc.exe), use su **General** página de propiedades. Para obtener información sobre cómo obtener acceso a la **General** página de propiedades en la carpeta HLSL, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Otros directorios de inclusión**  
 Agrega uno o varios directorios a la ruta de acceso de inclusión. Use punto y coma para separar los directorios.  
  
 Esta propiedad se corresponde con el **/I [ruta]** argumento de línea de comandos.  
  
 **Nombre de punto de entrada**  
 Especifica el punto de entrada para el sombreador. De forma predeterminada, el valor es **principal**.  
  
 Esta propiedad se corresponde con el **/E [name]** argumento de línea de comandos.  
  
 **Deshabilitar optimizaciones**  
 **Sí (/ DP)** para deshabilitar las optimizaciones; de lo contrario, **No**. De forma predeterminada, el valor es **Sí (/ DP)** para **depurar** configuraciones y **No** para **versión** configuraciones.  
  
 El **/Od** argumento de línea de comandos para el compilador HLSL se aplica implícitamente la **/Gfp** argumento de línea de comandos, pero la salida no puede ser idéntico al resultado de aplicar pasando ambos el **/Od**  y **/Gfp** argumentos de línea de comandos explícitamente.  
  
 **Habilitar información de depuración**  
 **Sí (/Zi)** para habilitar la información de depuración; en caso contrario, **No**. De forma predeterminada, el valor es **Sí (/Zi)** para **depurar** configuraciones y **No** para **versión** configuraciones.  
  
 **Tipo de sombreado**  
 Especifica el tipo de sombreado. Diferentes tipos de sombreadores implementan diferentes partes de la canalización de gráficos. Ciertos tipos de sombreadores solo están disponibles en los modelos de sombreador más recientes (que se especifican mediante el **modelo de sombreador** propiedad): por ejemplo, sombreadores se introdujeron en el modelo de sombreador 5 de proceso.  
  
 Esta propiedad se corresponde con el **[tipo]** parte de la **/T [tipo] _ [modelo]** argumento de línea de comandos para el compilador HLSL. El **modelos de sombreador** propiedad especifica la **[modelo]** parte del argumento.  
  
 **Modelo de sombreado**  
 Especifica el modelo de sombreador. Modelos de sombreador diferentes tienen capacidades distintas. En general, más recientes de los modelos de sombreador ofrecen capacidades ampliadas pero requieren más moderno hardware gráfico para ejecutar el código del sombreador. Ciertos tipos de sombreadores (que se especifican mediante el **sombreador de tipo** propiedad) solo están disponibles en los modelos de sombreador más recientes, por ejemplo, proceso sombreadores se introdujeron en el modelo de sombreador 5.  
  
 Esta propiedad se corresponde con el **[modelo]** parte de la **/T [tipo] _ [modelo]** argumento de línea de comandos para el compilador HLSL. El **tipo de sombreador** propiedad especifica la **[tipo]** parte del argumento.  
  
 **Definiciones de preprocesador**  
 Agrega una o varias definiciones de símbolo de preprocesador para aplicar al archivo de código fuente HLSL. Use punto y coma para separar las definiciones de símbolos.  
  
 Esta propiedad se corresponde con el **/D [definiciones]** argumento de línea de comandos para el compilador HLSL.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)   
 [Páginas de propiedades HLSL: avanzadas](../ide/hlsl-property-pages-advanced.md)   
 [Páginas de propiedades HLSL: Archivos de salida](../ide/hlsl-property-pages-output-files.md)