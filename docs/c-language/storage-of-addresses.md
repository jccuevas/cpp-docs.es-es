---
title: Almacenamiento de direcciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe77d3775c489399bb8b9032e645eee17d70b0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076598"
---
# <a name="storage-of-addresses"></a>Almacenamiento de direcciones

La cantidad de almacenamiento necesaria para una dirección y el significado de la dirección dependen de la implementación del compilador. No existen garantías de que los punteros a tipos diferentes tengan la misma longitud. Por consiguiente, **sizeof(char \*)** no es necesariamente igual a **sizeof(int \*)**.

**Específicos de Microsoft**

Para el compilador de C de Microsoft, **sizeof(char \*)** es igual a **sizeof(int \*)**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Declaraciones de puntero](../c-language/pointer-declarations.md)