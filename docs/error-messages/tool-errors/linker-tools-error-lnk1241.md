---
title: Error de las herramientas del vinculador LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 6e2b955787166c94be4ca35e1c58df5becd243f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183818"
---
# <a name="linker-tools-error-lnk1241"></a>Error de las herramientas del vinculador LNK1241

el archivo de recursos ' archivo de recursos ' ya se especificó

Este error se genera si se ejecuta **CVTRES** manualmente desde la línea de comandos y, a continuación, se pasa el archivo. obj resultante al vinculador además de otros archivos. res.

Para especificar varios archivos. res, páselo al enlazador como archivos. res, no desde los archivos. obj creados por **CVTRES**.
