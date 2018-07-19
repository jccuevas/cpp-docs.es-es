---
title: Descripción de la generación de manifiestos para programas de C/C ++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb6a65c718b88e4072c0ddad19411bb8ea4ddcff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381640"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Introducción a la generación de manifiestos para los programas de C/C++
A [manifiesto](http://msdn.microsoft.com/library/aa375365) es un documento XML que puede ser un archivo XML externo o un recurso incrustado dentro de una aplicación o un ensamblado. El manifiesto de un [aislada aplicación](http://msdn.microsoft.com/library/aa375190) se utiliza para administrar los nombres y las versiones de los ensamblados en paralelo compartidos a los que se debe enlazar la aplicación en tiempo de ejecución. El manifiesto de un ensamblado en paralelo especifica sus dependencias en los nombres, versiones, recursos y otros ensamblados.  
  
 Hay dos maneras de crear un manifiesto para una aplicación aislada o un ensamblado en paralelo. En primer lugar, el autor del ensamblado puede crear manualmente un archivo de manifiesto siguiendo reglas y requisitos de nomenclatura. O bien, si un programa sólo depende de ensamblados de Visual C++ como CRT, MFC, ATL u otros, el vinculador puede generar automáticamente un manifiesto.  
  
 Los encabezados de las bibliotecas de Visual C++ contienen información de ensamblado, y cuando las bibliotecas se incluyen en el código de aplicación, el vinculador usa esta información de ensamblado para formar un manifiesto para el archivo binario final. El vinculador no incrusta el archivo de manifiesto dentro del archivo binario y solo puede generar el manifiesto como un archivo externo. Tener un manifiesto como un archivo externo podría no funcionar en todos los escenarios. Por ejemplo, se recomienda que los ensamblados privados tengan manifiestos incrustados. En las compilaciones de línea de comandos como las que utilizan nmake para compilar el código, se puede incrustar un manifiesto utilizando la herramienta manifiesto; Para obtener más información, consulte [generación de manifiestos en la línea de comandos](../build/manifest-generation-at-the-command-line.md). Al compilar en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], se puede incrustar un manifiesto estableciendo una propiedad para la herramienta de manifiesto en el **propiedades del proyecto** diálogo; vea [generación de manifiestos en Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de aplicaciones aisladas y ensamblados en paralelo](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)