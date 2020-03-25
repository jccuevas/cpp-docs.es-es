---
title: Advertencia de las herramientas del vinculador LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: b1f330924b8e47e0649268142106a050c83cb20a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183324"
---
# <a name="linker-tools-warning-lnk4099"></a>Advertencia de las herramientas del vinculador LNK4099

No se encontró el archivo PDB ' nombredearchivo ' con ' Object/Library ' o en ' path '; vincular objeto como si no hubiera información de depuración

El enlazador no pudo encontrar el archivo. pdb. Cópielo en el directorio que contiene `object/library`.

Para buscar el nombre del archivo. pdb asociado al archivo objeto:

1. Extraiga un archivo objeto de la biblioteca con [lib](../../build/reference/lib-reference.md) **/Extract:** `objectname` **. obj** `xyz` **. lib**.

1. Compruebe la ruta de acceso al archivo. pdb con **dumpbin/Section:. Debug $ T/rawdata** `objectname` **. obj**.

También puede compilar con [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), por lo que no es necesario usar el archivo PDB, o bien quitar la opción del vinculador [/Debug](../../build/reference/debug-generate-debug-info.md) si no tiene archivos. pdb para los objetos que está vinculando.
