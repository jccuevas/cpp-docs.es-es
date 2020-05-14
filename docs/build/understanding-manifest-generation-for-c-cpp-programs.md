---
title: Introducción a la generación de manifiestos para los programas de C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492528"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Introducción a la generación de manifiestos para los programas de C/C++

Un [manifiesto](/windows/win32/sbscs/manifests) es un documento XML que puede ser un archivo externo o un recurso insertado en una aplicación o un ensamblado. El manifiesto de una [aplicación aislada](/windows/win32/SbsCs/isolated-applications) se usa para administrar los nombres y las versiones de los ensamblados en paralelo compartidos con los que se debe enlazar la aplicación en tiempo de ejecución. El manifiesto de un ensamblado en paralelo especifica sus dependencias de nombres, versiones, recursos y otros ensamblados.

Hay dos maneras de crear un manifiesto para una aplicación aislada o un ensamblado en paralelo. En primer lugar, el autor del ensamblado puede crear manualmente un archivo de manifiesto según las reglas y los requisitos de nomenclatura. Como alternativa, si un programa solo depende de ensamblados de Visual C++, como CRT, MFC, ATL u otros, el enlazador puede generar automáticamente un manifiesto.

Los encabezados de las bibliotecas de Visual C++ contienen información sobre el ensamblado y, cuando las bibliotecas se incluyen en el código de la aplicación, el enlazador usa dicha información para formar un manifiesto para el archivo binario final. El enlazador no inserta el archivo de manifiesto en el binario y solo puede generar el manifiesto como un archivo externo. Es posible que no en todos los casos se pueda tener un manifiesto como archivo externo. Por ejemplo, se recomienda que los ensamblados privados tengan manifiestos insertados. En las compilaciones de línea de comandos, como las que usan nmake para compilar el código, se puede insertar un manifiesto mediante la herramienta de manifiesto. Para obtener más información, consulte [Generación de manifiestos en la línea de comandos](manifest-generation-at-the-command-line.md). Al compilar en Visual Studio, se puede insertar un manifiesto mediante el establecimiento de una propiedad para la herramienta de manifiesto en el cuadro de diálogo **Propiedades del proyecto**. Consulte [Generación de manifiestos en Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>Vea también

[Conceptos de aplicaciones aisladas y ensamblados simultáneos](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
