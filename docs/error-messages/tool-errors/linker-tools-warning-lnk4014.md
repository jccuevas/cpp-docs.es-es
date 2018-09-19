---
title: Las herramientas del vinculador LNK4014 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df0a3b6f30733413a0f27c0b8daa07394bb04b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023116"
---
# <a name="linker-tools-warning-lnk4014"></a>Advertencia de las herramientas del vinculador LNK4014

no se encuentra el objeto miembro "objectname"

No se pudo encontrar LIB `objectname` en la biblioteca.

El **/quitar** y **/extraer** opciones requieren el nombre completo del objeto de miembro que se pueden eliminar o copiar a un archivo. El nombre completo incluye la ruta de acceso del archivo de objeto original. Para ver los nombres completos de objetos miembro de una biblioteca, use DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) o LIB [/lista](../../build/reference/managing-a-library.md).