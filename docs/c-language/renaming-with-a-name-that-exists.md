---
title: Cambio de nombre por uno que ya existe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: fc2a8f29-f757-4ce0-8d7f-7f8cff7f49ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10b9a9c4e42356a087c8cb6c10a470ba68acd4ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067759"
---
# <a name="renaming-with-a-name-that-exists"></a>Cambio de nombre por uno que ya existe

**ANSI 4.9.4.2** El efecto de que exista un archivo con el nuevo nombre antes de una llamada a la función **rename**

Si intenta cambiar el nombre de un archivo con un nombre que existe, la función **rename** produce un error y devuelve un código de error.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)