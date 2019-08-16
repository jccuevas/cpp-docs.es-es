---
title: Introducción a la generación de manifiestos para los programas de C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492528"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Introducción a la generación de manifiestos para los programas de C/C++

Un [manifiesto](/windows/win32/sbscs/manifests) es un documento XML que puede ser un archivo XML externo o un recurso incrustado dentro de una aplicación o un ensamblado. El manifiesto de una [aplicación aislada](/windows/win32/SbsCs/isolated-applications) se utiliza para administrar los nombres y las versiones de los ensamblados en paralelo compartidos en los que se debe enlazar la aplicación en tiempo de ejecución. El manifiesto de un ensamblado en paralelo especifica sus dependencias en nombres, versiones, recursos y otros ensamblados.

Hay dos maneras de crear un manifiesto para una aplicación aislada o un ensamblado en paralelo. En primer lugar, el autor del ensamblado puede crear manualmente un archivo de manifiesto siguiendo las reglas y los requisitos de nomenclatura. Como alternativa, si un programa solo depende de ensamblados visuales C++ como CRT, MFC, ATL u otros, el enlazador puede generar automáticamente un manifiesto.

Los encabezados de las bibliotecas C++ visuales contienen información de ensamblado y, cuando las bibliotecas se incluyen en el código de la aplicación, el enlazador usa esta información de ensamblado para formar un manifiesto para el archivo binario final. El vinculador no incrusta el archivo de manifiesto en el binario y solo puede generar el manifiesto como un archivo externo. Es posible que tenga un manifiesto como archivo externo que no funcione en todos los escenarios. Por ejemplo, se recomienda que los ensamblados privados tengan manifiestos incrustados. En las compilaciones de línea de comandos como las que usan NMAKE para compilar el código, se puede incrustar un manifiesto mediante la herramienta manifiesto; para obtener más información, vea [generación de manifiestos en la línea de comandos](manifest-generation-at-the-command-line.md). Al compilar en Visual Studio, se puede incrustar un manifiesto estableciendo una propiedad para la herramienta manifiesto en el cuadro de diálogo **propiedades del proyecto** . vea [generación de manifiestos en Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>Vea también

[Conceptos de aplicaciones aisladas y ensamblados simultáneos](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
