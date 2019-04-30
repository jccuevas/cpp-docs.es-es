---
title: Advertencia de las herramientas del vinculador LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: f67990ed74f500f1b954edcf1d6437f64f93f0d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298612"
---
# <a name="linker-tools-warning-lnk4014"></a>Advertencia de las herramientas del vinculador LNK4014

no se encuentra el objeto miembro "objectname"

No se pudo encontrar LIB `objectname` en la biblioteca.

El **/quitar** y **/extraer** opciones requieren el nombre completo del objeto de miembro que se pueden eliminar o copiar a un archivo. El nombre completo incluye la ruta de acceso del archivo de objeto original. Para ver los nombres completos de objetos miembro de una biblioteca, use DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) o LIB [/lista](../../build/reference/managing-a-library.md).