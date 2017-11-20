---
title: "Diseñar colección e Interfaces de enumerador (ATL) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40aa94226b93a42b14dfd23a64e12fff00e22729
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principios de diseño para la recopilación y las Interfaces de enumerador
Existen diferentes principios de cada tipo de interfaz de diseño:  
  
-   Proporciona una interfaz de colección *aleatorio* el acceso a un *único* elemento de la colección a través de la **elemento** método, permite a los clientes detectar están cuántos elementos de la colección a través de la **recuento** propiedad, y a menudo permite a los clientes agregar y quitar elementos.  
  
-   Proporciona una interfaz de enumerador *serie* el acceso a *varios* elementos de una colección, no permite detectar están cuántos elementos de la colección (hasta que el enumerador detiene devolver al cliente elementos), y no proporciona ninguna manera de agregar o quitar elementos.  
  
 Cada tipo de interfaz desempeña un rol diferente para proporcionar acceso a los elementos de una colección.  
  
## <a name="see-also"></a>Vea también  
 [Colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)

