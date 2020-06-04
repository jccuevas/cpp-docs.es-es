---
title: Error de las herramientas del vinculador LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: d2b28af52a2ca2263a7bad77c8c69242396ff2b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195258"
---
# <a name="linker-tools-error-lnk1181"></a>Error de las herramientas del vinculador LNK1181

no se puede abrir el archivo de entrada ' nombredearchivo '

El vinculador no encontró `filename` porque no existe o no se encontró la ruta de acceso.

Algunas causas comunes de los errores LNK1181 incluyen:

- se hace referencia a `filename` como una dependencia adicional en la línea del enlazador, pero el archivo no existe.

- Una instrucción **/LIBPATH** que especifica el directorio que contiene `filename` falta.

Para resolver los problemas anteriores, asegúrese de que los archivos a los que se hace referencia en la línea del vinculador están presentes en el sistema.  Asegúrese también de que haya una instrucción **/LIBPATH** para cada directorio que contenga un archivo dependiente del enlazador.

Para obtener más información, consulte [archivos. lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).

Otra causa posible de LNK1181 es que un nombre de archivo largo con espacios incrustados no estuviera entre comillas.  En ese caso, el vinculador solo reconocerá un nombre de archivo hasta el primer espacio y, a continuación, asumirá una extensión de archivo. obj.  La solución a esta situación consiste en incluir el nombre de archivo largo (ruta de acceso más nombre de archivo) entre comillas.

La compilación con la opción [/p (preprocess to a File)](../../build/reference/p-preprocess-to-a-file.md) puede dar como resultado LNK1181, ya que esa opción suprime la creación de archivos. obj.

## <a name="see-also"></a>Consulte también

[/LIBPATH (Directorios de bibliotecas adicionales)](../../build/reference/libpath-additional-libpath.md)
