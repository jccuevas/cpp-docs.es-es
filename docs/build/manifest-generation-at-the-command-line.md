---
title: Generación de manifiestos en la línea de comandos
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493205"
---
# <a name="manifest-generation-at-the-command-line"></a>Generación de manifiestos en la línea de comandos

Al compilarC++ C/Applications desde la línea de comandos mediante NMAKE u otras herramientas similares, el manifiesto se genera después de que el enlazador haya procesado todos los archivos objeto y creado el archivo binario final. El enlazador recopila información de ensamblado almacenada en los archivos objeto y combina esta información en un archivo de manifiesto final. De forma predeterminada, el vinculador generará un archivo denominado *binary_name*. *Extension*. manifest para describir el archivo binario final. El vinculador no incrusta un archivo de manifiesto en el binario y solo puede generar un manifiesto como un archivo externo. Hay varias maneras de insertar un manifiesto dentro del archivo binario final, como usar la [herramienta manifiesto (MT. exe)](/windows/win32/sbscs/mt-exe) o compilar el manifiesto en un archivo de recursos. Es importante tener en cuenta que deben seguirse reglas específicas al insertar un manifiesto dentro del archivo binario final para habilitar dichas características como vinculación incremental, firma y editar y continuar. Estas y otras opciones se describen en [cómo: Incrustar un manifiesto en una aplicaciónC++ ](how-to-embed-a-manifest-inside-a-c-cpp-application.md) de C/al compilar en la línea de comandos.

## <a name="see-also"></a>Vea también

[Manifiestos](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (Vincular de forma incremental)](reference/incremental-link-incrementally.md)<br/>
[Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Editar y continuar](/visualstudio/debugger/edit-and-continue)<br/>
[Introducción a la generación de manifiestos para los programas de C/C++](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
