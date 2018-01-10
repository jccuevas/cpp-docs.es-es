---
title: "Generación de manifiestos en la línea de comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ba88017e0003c7a552c985516dba9a6254317a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="manifest-generation-at-the-command-line"></a>Generación de manifiestos en la línea de comandos
Al compilar aplicaciones de C o C++ desde la línea de comandos mediante nmake o herramientas similares, se genera el manifiesto, el vinculador ha procesado todos los archivos objeto y se genera el archivo binario final. El vinculador recopila información de ensamblado almacenada en los archivos objeto y combina esta información en un archivo de manifiesto final. De forma predeterminada, el vinculador generará un archivo denominado < nombredebinario >. \<extensión > Manifest para describir el archivo binario final. El vinculador no incrusta un archivo de manifiesto dentro del archivo binario y sólo puede generar un manifiesto como un archivo externo. Hay varias maneras para incrustar un manifiesto dentro del archivo binario final, como el uso de la [herramienta manifiesto (mt.exe)](http://msdn.microsoft.com/library/aa375649) o compilar el manifiesto en un archivo de recursos. Es importante tener en cuenta que determinadas reglas deben seguirse al incrustar un manifiesto dentro del archivo binario final para habilitar características como la vinculación incremental, firma, y editar y continuar. Éstas y otras opciones se describen en [Cómo: incrustar un manifiesto dentro de una aplicación de C/C ++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) al compilar en la línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos](http://msdn.microsoft.com/library/aa375365)   
 [/INCREMENTAL (vincular de forma incremental)](../build/reference/incremental-link-incrementally.md)   
 [Ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Editar y continuar](/visualstudio/debugger/edit-and-continue)   
 [Introducción a la generación de manifiestos para los programas de C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)