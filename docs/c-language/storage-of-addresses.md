---
title: Almacenamiento de direcciones
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 2a0e218d4d34fa1482986ecccd7da8adba38086b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539378"
---
# <a name="storage-of-addresses"></a>Almacenamiento de direcciones

La cantidad de almacenamiento necesaria para una dirección y el significado de la dirección dependen de la implementación del compilador. No existen garantías de que los punteros a tipos diferentes tengan la misma longitud. Por consiguiente, **sizeof(char \*)** no es necesariamente igual a **sizeof(int \*)**.

**Específicos de Microsoft**

Para el compilador de C de Microsoft, **sizeof(char \*)** es igual a **sizeof(int \*)**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Declaraciones de puntero](../c-language/pointer-declarations.md)