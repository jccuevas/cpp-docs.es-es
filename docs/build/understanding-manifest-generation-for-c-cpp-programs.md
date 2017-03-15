---
title: "Introducci&#243;n a la generaci&#243;n de manifiestos para los programas de C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "manifiestos [C++]"
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Introducci&#243;n a la generaci&#243;n de manifiestos para los programas de C/C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un [manifiesto](http://msdn.microsoft.com/library/aa375365) es un documento XML que puede ser un archivo XML externo o un recurso incrustado dentro de una aplicación o un ensamblado.  El archivo de manifiesto de una [aplicación aislada](http://msdn.microsoft.com/library/aa375190) se utiliza para administrar los nombres y las versiones de los ensamblados en paralelo compartidos con los que se debe enlazar la aplicación en tiempo de ejecución.  El manifiesto de un [ensamblado en paralelo](_win32_side_by_side_assemblies) especifica sus dependencias respecto a nombres, versiones, recursos y otros ensamblados.  
  
 Hay dos maneras de crear un manifiesto para una aplicación aislada o un ensamblado en paralelo.  Primero, el creador del ensamblado puede generar manualmente un archivo de manifiesto siguiendo reglas y requisitos de nomenclatura.  Alternativamente, si un programa sólo depende de ensamblados de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] como CRT, MFC, ATL u otros, el vinculador puede generar automáticamente un manifiesto.  
  
 Los encabezados de las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] contienen información de ensamblado, y cuando las bibliotecas se incluyen en el código de la aplicación, esta información de ensamblado la usa el vinculador para formar un manifiesto correspondiente al archivo binario final.  El vinculador no incrusta el archivo de manifiesto dentro del archivo binario y sólo puede generar el manifiesto como un archivo externo.  Tener un manifiesto como archivo externo podría no funcionar en todos los escenarios.  Por ejemplo, se recomienda que los ensamblados privados tengan manifiestos incrustados.  En las compilaciones de línea de comandos como las que utilizan nmake para compilar código, se puede incrustar un manifiesto utilizando la herramienta Manifiesto; para obtener más información, vea [Generación de manifiestos en la línea de comandos](../build/manifest-generation-at-the-command-line.md).  Al compilar en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], se puede incrustar un manifiesto estableciendo una propiedad para la herramienta Manifiesto en el cuadro de diálogo **Propiedades del proyecto**; vea [Generación de manifiestos en Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## Vea también  
 [Conceptos de aplicaciones aisladas y ensamblados simultáneos](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Compilar aplicaciones aisladas y ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)