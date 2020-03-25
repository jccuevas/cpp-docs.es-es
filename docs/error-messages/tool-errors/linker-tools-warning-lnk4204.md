---
title: Advertencia de las herramientas del vinculador LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 98c53c9b998e9bd544c1cc72bd2b0c3fd2b0a418
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193867"
---
# <a name="linker-tools-warning-lnk4204"></a>Advertencia de las herramientas del vinculador LNK4204

' FILENAME ' no tiene información de depuración para hacer referencia al módulo; vincular objeto como si no hubiera información de depuración

El archivo. pdb tiene una firma errónea. El enlazador seguirá vinculando el objeto sin información de depuración. Puede que desee volver a compilar el archivo objeto mediante la opción [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

LNK4204 puede producirse si algunos de los objetos de la biblioteca hacen referencia a un archivo que ya no existe. Esto puede ocurrir cuando se vuelve a generar la solución, por ejemplo,. un archivo objeto podría eliminarse y no volver a generarse debido a un error de compilación. En este caso, puede compilar con **/Z7**, o **/FD**, para actualizar los objetos y hacer referencia a un único archivo por biblioteca (que no es el nombre de archivo. pdb predeterminado).  Para obtener más información, consulte [/Fd (Nombre del archivo de base de datos del programa)](../../build/reference/fd-program-database-file-name.md).  Asegúrese de que el archivo. pdb se guarda con la biblioteca cada vez que se actualiza en el sistema de control de código fuente.
