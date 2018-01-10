---
title: "Páginas de propiedades HLSL: Archivos de salida | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs: C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04f6ad8889c9a713b3b64284b329c21d5a2cd49e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hlsl-property-pages-output-files"></a>Páginas de propiedades HLSL: archivos de salida
Para configurar las siguientes propiedades del compilador HLSL (fxc.exe), use su **archivos de salida** propiedad. Para obtener información sobre cómo obtener acceso a la **archivos de salida** página de propiedades en la carpeta HLSL, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Nombre de Variable de encabezado**  
 Especifica el nombre de una matriz que se usa para código de objeto HLSL codificado. La matriz se encuentra en un archivo de encabezado que se genera el compilador de HLSL. El nombre del archivo de encabezado se especifica mediante la **nombre de archivo de encabezado** propiedad.  
  
 Esta propiedad se corresponde con el **/Vn [name]** argumento de línea de comandos.  
  
 **Nombre de archivo de encabezado**  
 Especifica el nombre del archivo de encabezado generado por el compilador HLSL. El encabezado contiene código de objeto HLSL que se codifica en una matriz. El nombre de la matriz especificado por el **nombre de Variable de encabezado** propiedad.  
  
 Esta propiedad se corresponde con el **/Fh [name]** argumento de línea de comandos.  
  
 **Nombre de archivo de objeto**  
 Especifica el nombre del archivo objeto generado por el compilador HLSL. De forma predeterminada, el valor es **$(OutDir) % (Filename) .cso**.  
  
 Esta propiedad se corresponde con el **/fo [name]** argumento de línea de comandos.  
  
 **Resultado del ensamblador**  
 **Lista de sólo ensamblador (/ Fc)** a las instrucciones de lenguaje de ensamblado de salida. **Código de ensamblado y Hex (/ Fx)** para generar las instrucciones de lenguaje de ensamblado y el código de operación correspondiente en formato hexadecimal. De forma predeterminada, ninguna lista es de salida.  
  
 **Archivo de salida del ensamblador**  
 Especifica el nombre del archivo de lista de ensamblado generado por el compilador HLSL.  
  
 Esta propiedad se corresponde con el **/Fc [name]** y **/Fx [name]** argumentos de línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)   
 [Páginas de propiedades HLSL: General](../ide/hlsl-property-pages-general.md)   
 [Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)