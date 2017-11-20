---
title: Almacenamiento de direcciones | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d0e996ac191ba3091925a85937e7636a2425215
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="storage-of-addresses"></a>Almacenamiento de direcciones
La cantidad de almacenamiento necesaria para una dirección y el significado de la dirección dependen de la implementación del compilador. No existen garantías de que los punteros a tipos diferentes tengan la misma longitud. Por consiguiente, **sizeof(char \*)** no es necesariamente igual a **sizeof(int \*)**.  
  
 **Específicos de Microsoft**  
  
 Para el compilador de C de Microsoft, **sizeof(char \*)** es igual a **sizeof(int \*)**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de puntero](../c-language/pointer-declarations.md)