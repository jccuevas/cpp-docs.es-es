---
title: Advertencia de las herramientas del vinculador LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: 5de53abc2342e3ed743f6b4abb871e05606dfc37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194283"
---
# <a name="linker-tools-warning-lnk4014"></a>Advertencia de las herramientas del vinculador LNK4014

no se encuentra el objeto miembro "objectname"

LIB no encontró `objectname` en la biblioteca.

Las opciones **/Remove** y **/Extract** requieren el nombre completo del objeto miembro que se va a eliminar o copiar en un archivo. El nombre completo incluye la ruta de acceso del archivo objeto original. Para ver los nombres completos de los objetos miembro de una biblioteca, use DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) o lib [/List](../../build/reference/managing-a-library.md).
