---
title: Generación de manifiestos en la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eaaebf02299f8f3907012ec97e467d137cbd246b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315488"
---
# <a name="manifest-generation-at-the-command-line"></a>Generación de manifiestos en la línea de comandos

Al compilar aplicaciones de C o C++ desde la línea de comandos mediante nmake o herramientas similares, el manifiesto se genera después de que el vinculador ha procesado todos los archivos objeto y se compila el archivo binario final. El vinculador recopila información de ensamblado almacenada en los archivos objeto y combina esta información en un archivo de manifiesto final. De forma predeterminada, el enlazador generará un archivo denominado *nombredebinario*. *extensión*manifest para describir el archivo binario final. El vinculador no incrusta un archivo de manifiesto dentro del archivo binario y sólo puede generar un manifiesto como un archivo externo. Hay varias maneras para incrustar un manifiesto en el archivo binario final, como el uso de la [herramienta manifiesto (mt.exe)](https://msdn.microsoft.com/library/aa375649) o compilar el manifiesto en un archivo de recursos. Es importante tener en cuenta que las reglas específicas que se deben seguir al incrustar un manifiesto dentro del archivo binario final para habilitar características como la vinculación incremental, firma y editar y continuar. Estas y otras opciones se tratan en [Cómo: incrustar un manifiesto dentro de unos C/aplicación C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) al compilar en la línea de comandos.

## <a name="see-also"></a>Vea también

[Manifiestos](https://msdn.microsoft.com/library/aa375365)<br/>
[/INCREMENTAL (Vincular de forma incremental)](../build/reference/incremental-link-incrementally.md)<br/>
[Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Editar y continuar](/visualstudio/debugger/edit-and-continue)<br/>
[Introducción a la generación de manifiestos para los programas de C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)<br/>
