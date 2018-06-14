---
title: 'Páginas de propiedades HLSL: General | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
dev_langs:
- C++
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77cc9a44076999633fd17b049cbcfad75f65eb7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340143"
---
# <a name="hlsl-property-pages-general"></a>Páginas de propiedades HLSL: General
Para configurar las propiedades siguientes del compilador HLSL (fxc.exe), use su página de propiedades **General**. Para obtener información sobre cómo acceder a la página de propiedades **General** en la carpeta HLSL, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Directorios de inclusión adicionales**  
 Agrega uno o más directorios a la ruta de acceso de inclusión. Use punto y coma para separar los directorios.  
  
 Esta propiedad se corresponde con el argumento de la línea de comandos **/I[ruta_de_acceso]**.  
  
 **Nombre del punto de entrada**  
 Especifica el punto de entrada para el sombreador. De forma predeterminada, el valor es **main**.  
  
 Esta propiedad se corresponde con el argumento de la línea de comandos **/E[nombre]**.  
  
 **Deshabilitar optimizaciones**  
 **Sí (/Od)** para deshabilitar las optimizaciones; de lo contrario, **No**. De forma predeterminada, el valor es **Sí (/Od)** para las configuraciones **Debug** y **No** para las configuraciones **Release**.  
  
 El argumento de la línea de comandos **/Od** para el compilador HLSL aplica implícitamente el argumento de la línea de comandos **/Gfp**, pero la salida no puede ser idéntico a la que se genera al pasar los dos argumentos de la línea de comandos **/Od** y **/Gfp** de forma explícita.  
  
 **Habilitar la información de depuración**  
 **Sí (/Zi)** para habilitar la información de depuración; en caso contrario, **No**. De forma predeterminada, el valor es **Sí (/Zi)** para las configuraciones **Debug** y **No** para las configuraciones **Release**.  
  
 **Tipo de sombreador**  
 Especifica el tipo de sombreador. Cada tipo de sombreador implementa partes diferentes de la canalización de gráficos. Algunos tipos de sombreadores solo están disponibles en los modelos de sombreador más recientes (que se especifican mediante la propiedad **Modelo de sombreador**); por ejemplo, los sombreadores de cálculo se introdujeron en el modelo de sombreador 5.  
  
 Esta propiedad se corresponde con la parte **[tipo]** del argumento de la línea de comandos **/T [tipo]_[modelo]** para el compilador HLSL. La propiedad **Modelos de sombreador** especifica la parte **[modelo]** del argumento.  
  
 **Modelo de sombreador**  
 Especifica el modelo de sombreador. Cada modelo de sombreador tiene funciones distintas. Por lo general, los modelos de sombreador más recientes ofrecen funciones ampliadas pero requieren hardware gráfico más moderno para ejecutar el código del sombreador. Algunos tipos de sombreadores (que se especifican mediante la propiedad **Modelo de sombreador**) solo están disponibles en los modelos de sombreador más recientes; por ejemplo, los sombreadores de cálculo se introdujeron en el modelo de sombreador 5.  
  
 Esta propiedad se corresponde con la parte **[modelo]** del argumento de la línea de comandos **/T [tipo]_[modelo]** para el compilador HLSL. La propiedad **Tipo de sombreador** especifica la parte **[tipo]** del argumento.  
  
 **Definiciones de preprocesador**  
 Agrega una o varias definiciones de símbolo de preprocesador para aplicar al archivo de código fuente HLSL. Use punto y coma para separar las definiciones de símbolo.  
  
 Esta propiedad se corresponde con el argumento de la línea de comandos **/D [definiciones]** para el compilador HLSL.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)   
 [Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)   
 [Páginas de propiedades HLSL: Archivos de salida](../ide/hlsl-property-pages-output-files.md)