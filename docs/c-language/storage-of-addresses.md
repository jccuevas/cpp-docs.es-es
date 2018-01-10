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
ms.workload: cplusplus
ms.openlocfilehash: bd82f6f5046cf910fbc871be37d4af5856796792
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-addresses"></a>Almacenamiento de direcciones
La cantidad de almacenamiento necesaria para una dirección y el significado de la dirección dependen de la implementación del compilador. No existen garantías de que los punteros a tipos diferentes tengan la misma longitud. Por consiguiente, **sizeof(char \*)** no es necesariamente igual a **sizeof(int \*)**.  
  
 **Específicos de Microsoft**  
  
 Para el compilador de C de Microsoft, **sizeof(char \*)** es igual a **sizeof(int \*)**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de puntero](../c-language/pointer-declarations.md)