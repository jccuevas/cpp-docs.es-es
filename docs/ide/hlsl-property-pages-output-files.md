---
title: 'Páginas de propiedades HLSL: archivos de salida | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs:
- C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f04b5f56511975851f4314f2977b84799c2f4e0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410525"
---
# <a name="hlsl-property-pages-output-files"></a>Páginas de propiedades HLSL: archivos de salida

Para configurar las propiedades siguientes del compilador HLSL (fxc.exe), use su propiedad **Archivos de salida**. Para obtener información sobre cómo acceder a la página de propiedades **Archivos de salida** en la carpeta HLSL, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

## <a name="uielement-list"></a>Lista de UIElement

- **Nombre de variable de encabezado**

   Especifica el nombre de una matriz que se usa para el código de objeto de HLSL codificado. La matriz se almacena en un archivo de encabezado generado por el compilador HLSL. El nombre del archivo de encabezado se especifica mediante la propiedad **Nombre de archivo de encabezado**.

Esta propiedad se corresponde con el argumento de la línea de comandos **/Vn[nombre]**.

- **Nombre de archivo de encabezado**

   Especifica el nombre del archivo de encabezado generado por el compilador HLSL. El encabezado contiene código de objeto de HLSL que se codifica en una matriz. El nombre de la matriz se especifica mediante la propiedad **Nombre de variable de encabezado**.

Esta propiedad se corresponde con el argumento de la línea de comandos **/Fh[nombre]**.

- **Nombre de archivo objeto**

   Especifica el nombre del archivo de objeto generado por el compilador HLSL. De forma predeterminada, el valor es **$(DirectorioDeSalida)%(NombreDeArchivo).cso**.

Esta propiedad se corresponde con el argumento de la línea de comandos **/Fo[nombre]**.

- **Resultados de ensamblado**

   **Lista de solo ensamblado (/Fc)** para mostrar solo las instrucciones de lenguaje de ensamblado. **Código de ensamblado y valores hexadecimales (/Fx)** para mostrar las instrucciones de lenguaje de ensamblado y el código de operador correspondiente en formato hexadecimal. De forma predeterminada, no se muestra ninguna lista.

- **Archivo de salida del ensamblador**

   Especifica el nombre del archivo de listas de ensamblado que muestra el compilador HLSL.

   Esta propiedad se corresponde con los argumentos de la línea de comandos **/Fc[nombre]** y **/Fx [nombre]**.

## <a name="see-also"></a>Vea también

[Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)<br>
[Páginas de propiedades HLSL: General](../ide/hlsl-property-pages-general.md)<br>
[Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)