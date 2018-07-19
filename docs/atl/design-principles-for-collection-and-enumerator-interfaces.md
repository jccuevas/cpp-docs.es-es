---
title: Diseño de Interfaces de enumerador (ATL) y de colección | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab8b42804ca892c80971928b869e09ccdf479d68
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851332"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principios de diseño para la recopilación y las Interfaces de enumerador
Hay diferentes principios de cada tipo de interfaz de diseño:  
  
-   Proporciona una interfaz de colección *aleatorio* el acceso a un *único* elemento de la colección a través de la `Item` método, permite a los clientes descubrir cuántos elementos se encuentran en la colección a través de la `Count` propiedad, y a menudo permite a los clientes agregar y quitar elementos.  
  
-   Proporciona una interfaz de enumerador *serie* el acceso a *varios* elementos de una colección, no permite descubrir cuántos elementos están en la colección (hasta que el enumerador deja de devolver al cliente elementos), y no proporciona ninguna manera de agregar o quitar elementos.  
  
 Cada tipo de interfaz desempeña un rol diferente al proporcionar acceso a los elementos de una colección.  
  
## <a name="see-also"></a>Vea también  
 [Las colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)

