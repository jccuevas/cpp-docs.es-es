---
title: Almacenamiento de direcciones
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 47b09ab6cd0b2045206daaee4badad32858ff934
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148743"
---
# <a name="storage-of-addresses"></a>Almacenamiento de direcciones

La cantidad de almacenamiento necesaria para una dirección y el significado de la dirección dependen de la implementación del compilador. No existen garantías de que los punteros a tipos diferentes tengan la misma longitud. Por consiguiente, **sizeof(char \*)** no es necesariamente igual a **sizeof(int \*)**.

**Específicos de Microsoft**

Para el compilador de C de Microsoft, **sizeof(char \*)** es igual a **sizeof(int \*)**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Declaraciones de puntero](../c-language/pointer-declarations.md)
