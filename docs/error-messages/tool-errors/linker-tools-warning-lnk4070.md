---
title: Advertencia de las herramientas del vinculador LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 391a477625b51fd37eacc5d455801ce90d2abbc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194010"
---
# <a name="linker-tools-warning-lnk4070"></a>Advertencia de las herramientas del vinculador LNK4070

/OUT: filename Directiva en. EXP difiere del nombre de archivo de salida ' FILENAME '; omitir Directiva

Los `filename` especificados en la instrucción [Name](../../build/reference/name-c-cpp.md) o [Library](../../build/reference/library.md) cuando se creó el archivo. exp difieren de los `filename` de salida que se suponían de forma predeterminada o se especifican con la opción [/out](../../build/reference/out-output-file-name.md) .

Verá esta advertencia si cambia el nombre de un archivo de salida en el entorno de desarrollo y no se actualizó el archivo. def del proyecto. Actualice manualmente el archivo. def para resolver esta advertencia.

Un programa cliente que utiliza el archivo DLL resultante puede tener problemas.
