---
title: Eliminación de archivos abiertos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], deleting
ms.assetid: 4fba7fb2-df0a-458e-b760-8858e12b855c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8e66c811571f22c263193ffad676052b34b7f72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087102"
---
# <a name="deleting-open-files"></a>Eliminación de archivos abiertos

**ANSI 4.9.4.1** El efecto de la función remove en un archivo abierto

La función remove elimina un archivo. Si el archivo está abierto, la función produce un error y devuelve -1.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)